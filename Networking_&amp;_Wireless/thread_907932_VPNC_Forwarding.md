---
title: "VPNC Forwarding"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by Bothinator on 2008-09-02
I've been banging my head on this for days, so any help is appreciated!

Scenario:

"Windows laptop" > Ubuntu box > VPNC > DDWRT Router > Internet > VPN Concentrator > Work LAN

I want to be able to communicate with a specific server at work from the laptop through the VPN.  The server IP is 165.105.72.11, and a tracert on the laptop responds only with 192.168.1.99, nothing else.

I've attached some info that hopefully will help:

Windows laptop IP settings:
```
192.168.1.98
255.255.255.0
192.168.1.99
```

Current interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
up vpnc phone
up route del -net 192.168.1.0 netmask 255.255.255.0 dev tun0
up route add -net 165.105.72.0 netmask 255.255.255.0 dev tun0
```
(Note- I had to add 192.168.1.0 because home/work match on that subnet)
(Note- I had to add 165.105.72.0 because it wouldn't pick up that subnet automatically, and that subnet has the server I needed to reach)

ROUTE -n dump after VLNC is connected:
Note: VLNC picks up an address in the 10.3.6.0 range when connected.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
165.105.2.1     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
165.105.66.209  0.0.0.0         255.255.255.255 UH    0      0        0 tun0
165.105.75.15   192.168.1.1     255.255.255.255 UGH   0      0        0 eth1
165.105.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
165.105.72.0    0.0.0.0         255.255.255.0   U     0      0        0 tun0
10.3.6.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
10.3.0.0        0.0.0.0         255.255.0.0     U     0      0        0 tun0
10.4.0.0        0.0.0.0         255.255.0.0     U     0      0        0 tun0
10.5.0.0        0.0.0.0         255.255.0.0     U     0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
```

I've also tried running the following commands:

```
iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE
```
and
```
sysctl -w net.ipv4.ip_forward=1
```

If I terminate VPNC, the laptop can reach the internet.

The laptop is just for troubleshooting - as soon as the connection works, I'll be using a dumb terminal (which only has limited network options...DHCP or Static address, Mask, Gateway, and DNS1/2.)

Last but not least...the TRACEPATH to 165.105.72.11 on the Ubuntu box when VLNC is connected:

```
tracepath 165.105.72.11
 1:  10.3.6.137 (10.3.6.137)                                1.265ms pmtu 1390
 1:  10.3.28.200 (10.3.28.200)                             36.532ms 
 1:  10.3.28.200 (10.3.28.200)                             36.587ms 
 2:  10.3.6.2 (10.3.6.2)                                   37.070ms 
 3:  no reply
 4:  165.105.72.11 (165.105.72.11)                         36.867ms reached
     Resume: pmtu 1390 hops 4 back 126 
```

I'm logging as root, so permissions ain't an issue.

Please let me know if more info or clarification is needed.

Thanks for reading through this outrageously long post!  :)

---

### Post by Bothinator on 2008-09-02
Looking at the TRACEPATH to 165.105.72.11, it goes through several internal addresses before getting to the server...is the reason I can't get to that server because the other machine (Windows laptop) doesn't have an internal address?  I mean, it's a totally different IP class....

Can I pass DHCP requests through the VPN?  So that the connected machine gets an internal address?

If anyone needs more info, just ask! :)

---

### Post by Bothinator on 2008-09-03
/bump

---

### Post by Bothinator on 2008-09-06
Ok, I decided that I wasn't getting through because the 192.x addresses can't get to 10.x addresses.

So, I gave the 2nd (eth0) NIC a 10.0.1.99 (255.255.0.0) address, and the windows laptop an IP of 10.0.1.98 (255.255.0.0).  Both machines can ping each other, but the windows laptop still can't reach the internal LAN through the VPN connection.

Here's what I've got in my interfaces file now:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
up vpnc phone --ifmode tap

auto eth0
iface eth0 inet static
address 10.0.1.99
netmask 255.255.0.0
gateway 0.0.0.0
up iptables -t nat -A POSTROUTING -o tap0 -j MASQUERADE
up sysctl -w net.ipv4.ip_forward=1
up sysctl -w net.ipv4.conf.eth0.send_redirects=1
up sysctl -w net.ipv4.conf.tap0.send_redirects=1
up route add -net 165.105.72.0 netmask 255.255.255.0 dev tap0
```

I don't understand what the Ubuntu machine is doing with the packets...so I did a few pings from the windows laptop while running TCPDUMP...and here's what it said:

```
20:56:48.914609 IP Ubuntu-Router.local.4500 > 165.105.75.15.4500: NONESP-encap: [|isakmp]
20:56:48.914912 IP 165.105.75.15.4500 > Ubuntu-Router.local.4500: isakmp-nat-keep-alive

20:56:49.858631 IP 10.0.1.98 > 165.105.72.11: ICMP echo request, id 512, seq 26880, length 40
20:56:49.862587 arp who-has 165.105.72.11 tell Ubuntu-Router.local
20:56:49.862678 arp reply 165.105.72.11 is-at 80:ff:f0:d9:6f:94 (oui Unknown)

20:56:49.862707 IP 10.0.1.98 > 165.105.72.11: ICMP echo request, id 512, seq 26880, length 40
20:56:49.863099 IP Ubuntu-Router.local.4500 > 165.105.75.15.4500: UDP-encap: ESP(spi=0x71f3e7aa,seq=0xb6), length 92
20:56:50.048606 IP 10.0.1.98.2777 > Ubuntu-Router.local.8905: UDP, length 85
20:56:50.048755 IP Ubuntu-Router.local > 10.0.1.98: ICMP Ubuntu-Router.local udp port 8905 unreachable, length 121
20:56:50.561087 IP 10.0.1.98.2777 > Ubuntu-Router.local.8905: UDP, length 85
20:56:50.561239 IP Ubuntu-Router.local > 10.0.1.98: ICMP Ubuntu-Router.local udp port 8905 unreachable, length 121
20:56:55.223709 IP 10.0.1.98 > 165.105.72.11: ICMP echo request, id 512, seq 27136, length 40
20:56:55.223780 IP 10.0.1.98 > 165.105.72.11: ICMP echo request, id 512, seq 27136, length 40
20:56:55.224415 IP Ubuntu-Router.local.4500 > 165.105.75.15.4500: UDP-encap: ESP(spi=0x71f3e7aa,seq=0xb7), length 92
20:56:56.078248 IP 10.0.1.98.2778 > Ubuntu-Router.local.8905: UDP, length 85
20:56:56.078402 IP Ubuntu-Router.local > 10.0.1.98: ICMP Ubuntu-Router.local udp port 8905 unreachable, length 121
20:56:56.570305 IP 10.0.1.98.2778 > Ubuntu-Router.local.8905: UDP, length 85
20:56:56.570457 IP Ubuntu-Router.local > 10.0.1.98: ICMP Ubuntu-Router.local udp port 8905 unreachable, length 121
20:56:57.914264 IP 165.105.75.15.4500 > Ubuntu-Router.local.4500: isakmp-nat-keep-alive
```

Of course, this doesn't give me much to work with, except that:

1.  The Ubuntu box gets the ping request from the windows laptop
2.  It asks where the server (165.105.72.11) is
3.  It gets a response through the VPN connection
4.  And somehow the packet...just can't get through.

I don't have any firewalls...so I guess my iptables are messed up somehow.  Does anyone have any ideas for me?  Or something to point me in the right direction here?

---

### Post by Bothinator on 2008-09-06
Ok, part of it was iptables.

After I found [[COLOR="Blue"]this[/COLOR]](http://www.revsys.com/writings/quicktips/nat.html), I ran the following:

```
iptables -t nat -A POSTROUTING -o tap0 -j MASQUERADE
iptables -A FORWARD -i tap0 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o tap0 -j ACCEPT
```

And now, the windows laptop can ping inside the VPN connection!  In fact, it could ping all the 10.x.x.x addresses.  But not the 165.105.72.11 server.

So, I re-ran ```
route add -net 165.105.72.0 netmask 255.255.255.0 dev tap0 
``` and now the client can connect!

Now, time to try the dumb terminal....  :)

---

