---
title: "SSH/Ad-Hoc problems"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by skadoo on 2007-08-29
Hi.

I'm having problems establishing a SSH connection between my Ubuntu machine and a Mac on an ad-hoc wireless network. The ad-hoc connection comes up fine, but whenever I try to establish a ssh connection (from either machine) I get a "No route to host" message.

The relevant lines from /etc/network/interfaces:

> auto ra0
iface ra0 inet static
        address 192.168.1.91
        netmask 255.255.255.0
        gateway 192.168.1.1
        broadcast 192.168.1.255
        wireless-mode ad-hoc
        wireless-essid skadoo
        wireless-key ##########
        wireless-channel 6
        wireless-rate 11M


The airport card has IP address 192.168.1.89 netmask 255.255.255.0

iwconfig:

> lo        no wireless extensions.

eth2      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"skadoo"  
          Mode:Ad-Hoc  Frequency=2.437 GHz  Cell: F2:3D:D3:10:76:4F   
          Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key: xxxxxxxxxx  Security mode:open
          Link Quality=53/100  Signal level=-86 dBm  Noise level:-220 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I'm stumped. I'd appreciate any help with this...

---

### Post by spd106 on 2007-08-29
Your on the same LAN, so it shouldn't be a routing issue, though you can always check the routing table to make sure it has an entry for the 192.168.1.0 network.

Can you ping the other hosts by IP address?

Have you checked to make sure that all hosts on the ad hoc network have the same cell address?

---

### Post by KCPokes on 2007-08-29
I assume that you can access the internet via the wireless connection in Ubuntu?  As was stated, it is a the same subnet, thus it shoudn't be a routing issue.  Normally the "no route to host" error relates to a connection issue, especially if it is within your local network.

---

### Post by skadoo on 2007-08-29
Thanks for the replies.

> I assume that you can access the internet via the wireless connection in Ubuntu? 

Yes, no problem.

> Your on the same LAN, so it shouldn't be a routing issue, though you can always check the routing table to make sure it has an entry for the 192.168.1.0 network.


I think this looks ok:

```

# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 ra0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 ra0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth2
```

> Can you ping the other hosts by IP address?

No, it seems not:

```
# ping 192.168.1.90
PING 192.168.1.90 (192.168.1.90) 56(84) bytes of data.
From 192.168.1.42 icmp_seq=2 Destination Host Unreachable
From 192.168.1.42 icmp_seq=3 Destination Host Unreachable
From 192.168.1.42 icmp_seq=4 Destination Host Unreachable
```

> Have you checked to make sure that all hosts on the ad hoc network have the same cell address?

Sorry, but I'm not sure what that means. Could you let me know how I check the cell address? (What is the cell address, exactly...?)

Thanks again for your help.

---

### Post by skadoo on 2007-08-29
> # ping 192.168.1.90
PING 192.168.1.90 (192.168.1.90) 56(84) bytes of data.
From 192.168.1.42 icmp_seq=2 Destination Host Unreachable
From 192.168.1.42 icmp_seq=3 Destination Host Unreachable
From 192.168.1.42 icmp_seq=4 Destination Host Unreachable

Ugh, so now I see that's trying to contact the wireless address from a wired port... But I've also tested this with the wired port commented out in /etc/network/interfaces, and I still can't ping the other machine.

---

### Post by spd106 on 2007-08-29
It's probably not a good idea to have both interfaces on the same 192.168.1.0/24 network (unless you are going to bridge them). Try shifting the ad hoc network to another subnet e.g. 192.168.2.0/24. 

When I said cell address before I was meaning the IBSSD cell address used in the ad hoc network. You can see it in the iwconfig output. I don't have a MAC, so I have no idea how you would check it from there.

Incidentally you can specify the interface when you ping like so
```
ping -I ra0 192.168.1.90
```

Which driver are you using and which chipset does the wifi card have? Have you used ad hoc before successfully?

---

### Post by skadoo on 2007-08-29
> It's probably not a good idea to have both interfaces on the same 192.168.1.0/24 network (unless you are going to bridge them). Try shifting the ad hoc network to another subnet e.g. 192.168.2.0/24. 

Ok, I did that. I changed the entry in /etc/network interfaces to:

```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet static
        address 192.168.1.42
        netmask 255.255.255.0
        gateway 192.168.1.1
        broadcast 192.168.1.255
 
auto ra0
iface ra0 inet static
        address 192.168.2.1
        netmask 255.255.255.0
        gateway 192.168.2.1
        broadcast 192.168.2.255
        wireless-mode ad-hoc
        wireless-essid skadoo
        wireless-key xxxxxxxxxx
        wireless-channel 6
        wireless-rate 11M
```

and I changed the IP address on the airport card to 192.168.2.0.

But when I ping the Mac from the Ubuntu machine:

```
#ping -I 192.168.2.1 192.168.2.0
PING 192.168.2.0 (192.168.2.0) from 192.168.2.1 : 56(84) bytes of data.
ping: sendmsg: Permission denied
ping: sendmsg: Permission denied
ping: sendmsg: Permission denied
ping: sendmsg: Permission denied
```

Which seems pretty weird.

And when I ping the Ubuntu machine from the mac, it says "Host is down." Although all other indications are that both machines are connected to the same ad-hoc network.

> When I said cell address before I was meaning the IBSSD cell address used in the ad hoc network. You can see it in the iwconfig output. I don't have a MAC, so I have no idea how you would check it from there.

Ah, ok. This is the output from iwconfig on the Ubuntu machine:

```
#iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"skadoo"  
          Mode:Ad-Hoc  Frequency=2.437 GHz  Cell: 92:E4:A0:D2:78:63   
          Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:xxxxxxxxxx  Security mode:open
          Link Quality=54/100  Signal level=-81 dBm  Noise level:-220 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I'm not sure how to find the cell address on the Mac, and a google search didn't show up anything useful. The "Airport ID" is: 00:1b:63:14:2c:c1. But I have no idea if that is the same thing as the cell address, or just coincidentally a hex string of the same length...


> Which driver are you using and which chipset does the wifi card have? Have you used ad hoc before successfully?

It's the ralink chipset, rt2500 driver. I have used ad hoc successfuly before, but with different hardware -- a Netgear PCMCIA wireless card and atheros driver. That had some quirks too, but I was able to get it working...

---

