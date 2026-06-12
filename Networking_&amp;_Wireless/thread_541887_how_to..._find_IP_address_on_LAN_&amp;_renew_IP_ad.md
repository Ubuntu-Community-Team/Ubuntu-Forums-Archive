---
title: "how to... find IP address on LAN &amp; renew IP address lease"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by Ndyanabo on 2007-09-03
Hi,

Some quick networking questions.

1. how do I release and renew an IP address lease? I'm looking for the equivalent commands to the windows "ipconfig /release", "ipconfig /renew?"


2. I'm looking for a command which will show the IP addresses of all the devices, including the router itself, on my LAN.

I recently connected to my apartment's wireless network through a linksys wireless router that I flashed with open source firmware. I think it's using bridge mode or client bridge mode or something like that to connect to the wireless network. I was successful, but when I connected to the network, new IP addresses were assigned to both computers and the router. It was easy to find the IP of the main computer, but the second computer is headless, and of course I can't tunnel over to it since I don't have the ip any more. I could plug in the monitor and keyboard, but that's a pain (and since the IPs are dynamic, I don't want to have to do that every time the address changes. Also, the router's IP changed too, so I need to find the address so that I can get to the administration page. 


here's what I've tried:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:B0:D0:DE:49:8A  
          inet addr:128.36.38.46  Bcast:128.36.38.255  Mask:255.255.255.0
          inet6 addr: 2002:8024:161a:9:2b0:d0ff:fede:498a/64 Scope:Global
          inet6 addr: fe80::2b0:d0ff:fede:498a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8392726 errors:0 dropped:0 overruns:139 frame:0
          TX packets:284502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2016468173 (1.8 GiB)  TX bytes:38915017 (37.1 MiB)
          Interrupt:17 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2165868 (2.0 MiB)  TX bytes:2165868 (2.0 MiB)


```

```
$ arp -na
? (128.36.38.174) at 00:19:E3:02:2E:F1 [ether] on eth0
? (128.36.38.94) at 00:13:02:99:5B:0F [ether] on eth0
? (128.36.38.1) at 00:0C:CF:6B:D3:FC [ether] on eth0
? (128.36.38.157) at 00:0D:93:ED:95:48 [ether] on eth0
? (128.36.38.30) at 00:14:A5:8B:50:65 [ether] on eth0
? (128.36.38.32) at 00:11:24:98:A8:74 [ether] on eth0
? (128.36.38.44) at 00:19:E3:04:9D:87 [ether] on eth0

```
none of those MACs are my devices. Not sure what the IPs refer to. Some devices on the network.

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0

```

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.36.38.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         128.36.38.1     0.0.0.0         UG    0      0        0 eth0

```
I tried that gateway address in firefox, but didn't get to the router's page.


thanks.

---

### Post by usererror on 2007-09-03
I am also sort of in your boat...

what is the bash command to tell me what my current IP/Subnet Mask/Gateway address is just like in windows **ipconfig**?

I just did a **route -n** and in the last line it DOES show my Router/Gateway address but is there a command that will show me all 3 just like ipconfig does?

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth1

```

---

### Post by wieman01 on 2007-09-04
Renew IP lease:
> sudo ifdown [COLOR="Red"]eth0[/COLOR]
> sudo ifup [COLOR="Red"]eth0[/COLOR]
Router IP address (as highlighted above):
> route
That is all I can say here.

---

### Post by nickmcg on 2007-09-04
> **wieman01 said:**
> Renew IP lease:


Router IP address (as highlighted above):

That is all I can say here.

surely ```
sudo dhclient
```will release & renew ip lease, and ```
sudo ifconfig
``` will display the local ip configuration

As for displaying IP addresses for all machines on the lan, the dhcp server is the machine to ask for that - on  a netgear router, you can display a list of attached devices.

Nick

---

### Post by wieman01 on 2007-09-04
"ifup" and "ifdown" invoke the DHCP client progam. So the effect is the same. :-) But you are right, "dhclient" makes it a bit more distinct.

---

### Post by usererror on 2007-09-04
But there is no "one" command to display IP, Gateway, etc as in Windows' with 'ipconfig' ?

---

### Post by Ndyanabo on 2007-09-04
okay, I'm sure yous guys are right about the IP renew. But I still can't find my router's IP.

```
$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:B0:D0:DE:49:8A  
          inet addr:128.36.38.46  Bcast:128.36.38.255  Mask:255.255.255.0
          inet6 addr: 2002:8024:27fa:9:2b0:d0ff:fede:498a/64 Scope:Global
          inet6 addr: fe80::2b0:d0ff:fede:498a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11265982 errors:0 dropped:0 overruns:139 frame:0
          TX packets:346581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2947887507 (2.7 GiB)  TX bytes:46326871 (44.1 MiB)
          Interrupt:17 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2707637 (2.5 MiB)  TX bytes:2707637 (2.5 MiB)

```

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.36.38.0     *               255.255.255.0   U     0      0        0 eth0
default         college.net.yal 0.0.0.0         UG    0      0        0 eth0
```

???? 

there's nothing there that I can use to log into my router admin page.

---

### Post by wieman01 on 2007-09-04
That IS the router:
> college.net.yal
Ping it and you should get a response from it which reveals the IP address:
> ping college.net.yal
Although I am not sure if "college.net.yal" is the full name... it might be cut off. It could be "128.36.38.1".

---

### Post by usererror on 2007-09-04
> **wieman01 said:**
> That IS the router:

Ping it and you should get a response from it which reveals the IP address:

Although I am not sure if "college.net.yal" is the full name... it might be cut off. It could be "128.36.38.1".

I agree with Wieman01, try pinging the 128.36.38.1 address.  I am assuming from your output above this isn't your typical Home network router you are connecting to either. ;)

Good luck!

---

### Post by Ndyanabo on 2007-09-04
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.36.38.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         128.36.38.1     0.0.0.0         UG    0      0        0 eth0

```

this would suggest that "college.net.yal" *is* appended, and that the address is 128.36.38.1, right?

```
ping 128.36.38.1
PING 128.36.38.1 (128.36.38.1) 56(84) bytes of data.
64 bytes from 128.36.38.1: icmp_seq=1 ttl=255 time=1.20 ms
64 bytes from 128.36.38.1: icmp_seq=3 ttl=255 time=10.7 ms
64 bytes from 128.36.38.1: icmp_seq=5 ttl=255 time=30.5 ms
64 bytes from 128.36.38.1: icmp_seq=6 ttl=255 time=26.7 ms

--- 128.36.38.1 ping statistics ---
6 packets transmitted, 4 received, 33% packet loss, time 5016ms
rtt min/avg/max/mdev = 1.209/17.317/30.599/11.920 ms

```

this shows that there is a device at 128.36.38.1.

but then, I also did:

```
ping college.net.yale.edu
PING college.net.yale.edu (128.36.95.1) 56(84) bytes of data.
64 bytes from college.net.yale.edu (128.36.95.1): icmp_seq=1 ttl=255 time=2.49 ms
64 bytes from college.net.yale.edu (128.36.95.1): icmp_seq=2 ttl=255 time=1.86 ms
64 bytes from college.net.yale.edu (128.36.95.1): icmp_seq=3 ttl=255 time=17.4 ms

--- college.net.yale.edu ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 1.861/7.263/17.437/7.198 ms

```

so there's another device at 128.36.95.1.


So,  is 128.36.38.1 necessarily my router? My router is configured for client bridge mode or something so might this be the device that it's connecting to? 

the bottom line for me is that putting 128.36.38.1, or for that matter 128.36.95.1, into firefox returns "Unable to connect".

so, I'm at a loss.

---

### Post by usererror on 2007-09-04
If there is bridging involved, the other side of the bridge, could be the gateway so set your gateway address to **128.36.95.1** and see if that works.

Where I work we have a wireless bridge, each side has it's own IP address but they are not the gateway addresses...it is a transparent bridge, though...

I guess I should have asked in the first place...why is bridging involved???  are you unable to just plug into a network port and get a DHCP address?  I assume you are using static IPs here...

post back!

---

### Post by nickmcg on 2007-09-04
It might be worth using traceroute to an external site to find where the routers/bridges are on the lan (I'm not sure whether this should be a question or a statement)

Nick

---

### Post by Ndyanabo on 2007-09-04
thanks for your interest. 

why did I have to use bridge mode? I'm not using the router for a wireless lan. When I had a normal ISP, I plugged it into the modem, and got an address through DHCP, as you say. Now, however, I use it to connect to my apartment/school's wireless internet network. There's no wired ethernet in the apartment to connect to. So, I asked the IT guys what to do, and they told me client mode. Client mode didn't work, so I brought the router to them they configured it for client bridge mode. I brought the router home and it connects to the wireless network, but in doing so, new IPs were assigned. Hence, I can't "find" the router.

Long story short, the school has a huge complex network, so I imagine that's why I'm in client bridge mode. 

The IPs are dynamic, as specified by the schools network. I had to register the MAC addresses of the computers and also the router with the school, and I believe that the IPs are set by the school's hardware. 

There are two computers on the network, one main, and one headless. (annoyingly,  I don't even know the IP address of the headless computer -- I assume I'll find it once I get to the router's admin page). 

I assume that "gateway address" refers to the router's admin address? I tried **128.36.95.1 ** in a browser and got nothing. If I'm wrong, how do I set the gateway address?

I'm really in over my head here, actually. I have no idea what traceroute is, for example.

---

### Post by usererror on 2007-09-05
I think i see what you're doing now.  Your dorm room does not have any wired network ports only a wireless network...so you are using a Wireless Router in 'client mode' that connects to the wireless network and then you can wire into the ports with your other computers?

---

### Post by Ndyanabo on 2007-09-05
yup, that's right (except I live in an apartment, not a dorm). I've got two computers plugged into that router. Plus a third (windows) laptop that connects to the network independently of the router.

---

### Post by anv on 2007-10-14
>  sudo ifdown eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 4132
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:92:34:bb:4f
Sending on   LPF/eth0/00:1a:92:34:bb:4f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Operation not permitted

> ~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:92:34:bb:4f
Sending on   LPF/eth0/00:1a:92:34:bb:4f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.9
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.9
bound to 192.168.0.130 -- renewal in 1648 seconds.



why this hapens? I mean why It doesn't allow me to have new ip, it says it is bound?

---

### Post by usererror on 2007-10-14
anv, i'm not sure what you are asking?

in your first quote you shut down the interface.

in your second quote you restarted the interface and you were assigned an IP address by the dhcp server i.e. it bound your mac-address of your pc to an IP address.

---

### Post by anv on 2007-10-15
So I meant that why it is bound to this ip:  192.168.0.130 should it release and change? even I use those commands it stays everytime in this ip, and I don't have static ip from my service provider.

---

### Post by tturrisi on 2007-10-15
ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'
will show your lan ip address

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
will show your wan ip address

grep -v "|" /proc/net/wireless | awk -F: '{print $1}'
will show the wifi adapter name

route | grep default
will show the gateway ip address

save as net-renew.sh and make executable
(will kill the current net & restart it newly)
```

#/bin/bash
ifconfig ethX down
ifconfig ethX up
/etc/init.d/networking restart
```

---

### Post by usererror on 2007-10-15
> **anv said:**
> So I meant that why it is bound to this ip:  192.168.0.130 should it release and change? even I use those commands it stays everytime in this ip, and I don't have static ip from my service provider.

No, it may not always change.  Yes it is a DHCP address, but you may get that IP over and over again.  Their lease times may be days or weeks long before it expires and has to give you a new IP address.  But even when your dhcp lease expires you *might* end up with the same IP again.

---

