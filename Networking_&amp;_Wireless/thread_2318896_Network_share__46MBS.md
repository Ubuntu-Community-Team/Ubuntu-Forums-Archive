---
title: "Network share  46MB/S"
date: 2016-03-30
forum: Networking &amp; Wireless
---

### Post by Chrismallia on 2016-03-30
Hi I just installed Ubuntu 15 on a laptop I have that was running windows 10, but I am having a small problem when I had windows 10 and transfer files over the network using windows server 2012 smb shares I got 113MB/S now with Ubuntu I can not get more then 46MB/S. I have a gigabit network switch and network cards cat6 cables  and the laptop has a SSD also does the server so the drives are not the bottleneck. any help or info? thanks regards
btw I was also considering to remove windows server and put ubuntu on my server but what worries me is that I do not get the speeds I got with Windows in file transfers

Here is the info and thanks 

[SIZE=2][FONT=arial]```
untu@ubuntu:~$ sudo  lspci -nnk | grep Ethernet
00:0f.0 Ethernet controller [0200]: NVIDIA Corporation MCP73 Ethernet [10de:07dc] (rev a2)
ubuntu@ubuntu:~$ sudo  lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: NVIDIA Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: enp0s15
       version: a2
       serial: 00:25:11:04:75:f5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.11 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
       resources: irq:28 memory:f9ff7000-f9ff7fff ioport:b880(size=8) memory:f9ffe800-f9ffe8ff memory:f9ffe400-f9ffe40f
```[/FONT][/SIZE]

---

### Post by Chrismallia on 2016-03-31
I installed ubuntu on a different pc with same problem no ideas anyone ?

---

### Post by mikewhatever on 2016-03-31
This is a vary open ended general question, basically, "why something doesn't work as something else".  In case you do want help, add the outputs of
```
  lspci -nnk | grep Ethernet
  lshw -C network
```
to the first post. That would be a good start.

---

### Post by Chrismallia on 2016-05-09
Still looking for help. I tried unraid server with samba shares and with windows I got 113mb/s with ubuntu its back to 45 to 50MB/S

---

### Post by slickymaster on 2016-05-09
*Thread moved to **Networking & Wireless**.*

Did you see [mikewhatever's post]("http://ubuntuforums.org/showthread.php?t=2318896&p=13463787&viewfull=1#post13463787")?

---

### Post by Chrismallia on 2016-05-09
Yes I did I included the results in the first post

---

