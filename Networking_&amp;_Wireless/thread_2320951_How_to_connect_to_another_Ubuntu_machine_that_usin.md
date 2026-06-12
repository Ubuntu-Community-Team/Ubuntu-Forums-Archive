---
title: "How to connect to another Ubuntu machine that using the same router but LAN to WLAN"
date: 2016-04-19
forum: Networking &amp; Wireless
---

### Post by pavlushka on 2016-04-19
I am connected to a router with a wired LAN running Xubuntu and another  machine running Ubuntu is connected to the same router through WLAN. So how can I connect to that machine to access shared folders of that machine? Both machines are using the same ip range.

---

### Post by Bucky Ball on 2016-04-19
*Thread moved to **Networking & Wireless**.*

Welcome. You are really asking two questions here: how to run a remote machine and how to share files/folders between two machines. Perhaps tackle getting a connection up and sharing files first then post remote machine setup questions in a new thread.

First off, can one machine ping the other and the router? 

> ping 192.168.0.***

... where '***' matches the details of the final number of the router or the other machine. Hit enter. Getting a ping time?

I find it makes things easier if you set static IPs on the two machines so they don't change anytime.

---

### Post by pavlushka on 2016-04-19
DHCP is enabled in router, so machine gets random ip within the range and the ping says "Destination Host Unreachable"

---

### Post by Bucky Ball on 2016-04-19
There's your first problem. Is your machine actually showing you are connected to your network in Network Manager? If you can't ping the router you won't be able to share files. Both machines can't ping the router? It is the router you are trying to ping? Let's stick with that for now if so and get one of the machines successfully pinging, or try to.

First up, choose which machine to work on and then open a terminal and:

```
sudo lshw -C network
```

Please post the output here between code tags (see the green link in my signature below for how).

---

### Post by Bashing-om on 2016-04-19
pavlushka; Hello;

@ Bucky Ball; Hey ole buddy;

If it is only to copy files between ... consider:

[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449) <-easiest way to cp files 'tween two 'buntus that share the same router/house (Morbius1)

Pretty simple and straight forward.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2016-04-19
> **Bashing-om said:**
> If it is only to copy files between ... consider:

[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449) <-easiest way to cp files 'tween two 'buntus that share the same router/house (Morbius1)



Might be an option, but for the moment OP can't ping router so no sharing will be happening with any method yet. :)

@pavlushka: You are using the correct router IP when attempting to ping? Sorry if a silly question, but just double-checking. Mine is:

```
ping 192.168.0.1
```

---

### Post by May_Masters on 2016-04-20
First check your own IP-Address. On both machines do a ```
ifconfig -a
```

If both machines are within the same sub-net (check the sunetmask) you should be able to "see" (ping) the other machine

Otherwise your router will have to do some NAT (should be enabled by default)

Here you need to know the IP of your router ! ... ping him, nmap, arp -a ...
Make sure you set the default gateway to this IP

---

### Post by pavlushka on 2016-04-21
My router ip is 192.168.5.**

I tried to ping the other machine while both machines are connected to the internet through the router.

```

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: 00:1f:3a:37:59:b6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=4.4.0-21-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:91300000-9130ffff
  *-network
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: enp2s1
       version: 10
       serial: 00:1b:38:fc:e0:8e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.5.33 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff


```

```


sudo ifconfig -a
enp2s1    Link encap:Ethernet  HWaddr 00:1b:38:fc:e0:8e  
          inet addr:192.168.5.33  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::ce64:95ee:535f:3dde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:255666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:225407922 (225.4 MB)  TX bytes:30798735 (30.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:4320093 (4.3 MB)  TX bytes:4320093 (4.3 MB)

wlp1s0    Link encap:Ethernet  HWaddr 00:1f:3a:37:59:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

And Bashing-om, Hi, yes my primary purpose is sharing files between the machines and looking into that link too, thanks

---

### Post by Bucky Ball on 2016-04-21
> **pavlushka said:**
> I tried to ping the other machine while both machines are connected to the internet through the router.



And? If you don't let us know what's happening we can't give you much help. You tried to ping the other machine by the correct IP and then what?

They're both connected fine to the internet so presume they can both ping the router fine?

---

### Post by pavlushka on 2016-04-21
Yes, the router ip ping result is following,
```

ping 192.168.5.**
PING 192.168.5.** (192.168.5.**) 56(84) bytes of data.
64 bytes from 192.168.5.**: icmp_seq=1 ttl=64 time=0.772 ms
64 bytes from 192.168.5.**: icmp_seq=2 ttl=64 time=0.634 ms
64 bytes from 192.168.5.**: icmp_seq=3 ttl=64 time=0.660 ms
64 bytes from 192.168.5.**: icmp_seq=4 ttl=64 time=0.656 ms
64 bytes from 192.168.5.**: icmp_seq=5 ttl=64 time=0.662 ms
64 bytes from 192.168.5.**: icmp_seq=6 ttl=64 time=0.666 ms
64 bytes from 192.168.5.**: icmp_seq=7 ttl=64 time=0.669 ms
64 bytes from 192.168.5.**: icmp_seq=8 ttl=64 time=0.667 ms
64 bytes from 192.168.5.**: icmp_seq=9 ttl=64 time=0.676 ms
64 bytes from 192.168.5.**: icmp_seq=10 ttl=64 time=0.644 ms
64 bytes from 192.168.5.**: icmp_seq=11 ttl=64 time=0.649 ms
64 bytes from 192.168.5.**: icmp_seq=12 ttl=64 time=0.651 ms
64 bytes from 192.168.5.**: icmp_seq=13 ttl=64 time=0.662 ms
64 bytes from 192.168.5.**: icmp_seq=14 ttl=64 time=0.683 ms
^C
--- 192.168.5.** ping statistics ---
14 packets transmitted, 14 received, 0% packet loss, time 12999ms


```

but to the other machine's ip ping from my one says "Destination host unreachable". Like to add, both machines have gufw enabled with all incoming "deny" and all outgoing "allow", and xubuntu is 64 bit and ubuntu is 32 bit. I disabled both machine's firewall and tried but no success. Both machines can ping the router.

---

### Post by pavlushka on 2016-04-22
"MultiAP Isolation" option was enabled in wifi section of my router, thats the reason behind no ping between lan to wlan, I disabled that option and created one normal user on each machine, added the lines for local ip series like "sshd: 192.168.5." & "vsftpd: 192.168.5." in /etc/hosts.allow file as DHCP is enabled in router otherwise for a static ip, I could add the specific ip in hosts.allow rules. And added "ALL: ALL" in /etc/hosts.deny file to prevent any other connection other than from the desired ones and used "Remmina" through "sftp protocol" to login to the other machine and exchanged files, it worked!

---

### Post by Bucky Ball on 2016-04-22
Thank you for sharing your solution and marking the thread as solved. Well done persisting and digging that up. :)

---

