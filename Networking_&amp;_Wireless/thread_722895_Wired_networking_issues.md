---
title: "Wired networking issues"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by ssalman on 2008-03-12
I've been trying to fix my wired network for more than a week with no success. I have a laptop connected to a broadband cable modem directly without using a router. when I use my XP laptop, it works without ANY setup (no password or account info) but with my ubuntu laptop, I have no success. Below is what I tried so far,

I've also used "$ sudo pppoeconf" but it could not find anything.

Could someone please give me a hint, I'm running out of ideas on how to get this to work, thanks in advance...



```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:A4:8E:36:E4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1678146 (1.6 MB)  TX bytes:155681 (152.0 KB)

eth0:avah Link encap:Ethernet  HWaddr 00:10:A4:8E:36:E4  
          inet addr:169.254.8.79  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:339460 (331.5 KB)  TX bytes:339460 (331.5 KB)

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 09
       serial: 00:10:a4:8e:36:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.

```

---

### Post by Phoenixzeus on 2008-03-13
Can you ping your Modem?
What ISP are you with?
Does your Internet Service Provider use a proxy?

---

### Post by ssalman on 2008-03-13
Thanks Phoenixzeus.
 
Here is the problem, I'm currently in a temprory company housing, so the modem and the ISP are not mine. I do not know what is the IP of the modem, and I don't know the ISP. but when I use my XP laptop, it connects directly with no login or setup, so I'm not sure what kind of setup is being used to accomplish this... any ideas? Thanks.

---

### Post by Iowan on 2008-03-13
How are you set up - DHCP, static, or local zeroconf? Check under manual configuration (Two-monitors icon at upper right) or System>Administration>Network.

---

### Post by ssalman on 2008-03-14
Originally, it was setup for Roaming. but I've also tried DHCP, ZeroConf, and Static copying the info from my XP laptop. nothing work.
 
I think the issue is that I don't know what type of connection I have with the modem (PPPOE, Ethernet, other) but XP is able to recognize it immediately.
 
What's more, there is a piece of paper with the modem, that reads something like "if you're visiting from outside the US, you laptop may not work with this connection, so contact your IS reps."

---

### Post by rustybronco on 2008-03-14
> **ssalman said:**
>  but when I use my XP laptop, it connects directly with no login or setup, so I'm not sure what kind of setup is being used to accomplish this... any ideas? Thanks.here in the states, cable modems are tied to the mac address of the machine that the cable modem is first connected  to. maybe they tie it to a mac address? a long shot but something worth considering.
[http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html](http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html)

in xp start>run>cmd> ipconfig /all and copy the mac address.

---

### Post by Iowan on 2008-03-14
I wondered about the MAC address, as well - but MAC address *_should _*be the same whether machine is running XP or Ubuntu.

---

### Post by rustybronco on 2008-03-14
> **Iowan said:**
> I wondered about the MAC address, as well - but MAC address *_should _*be the same whether machine is running XP or Ubuntu.I read it as two different laptops, one linux one windows.
> when I use my XP laptop, it works without ANY setup (no password or account info) but with my ubuntu laptop,
maybe they will clarify it.

---

### Post by ssalman on 2008-03-14
you're right, they are two laptops.

I didn't think of the MAC address. I'll try it and then report back. Thanks.

---

### Post by ssalman on 2008-03-19
Thanks rustybronco, this solved the issue. the modem was actually tied to the MAC address of the 1st laptop I used, which was the XP laptop, as soon as I rebooted the modem, it worked!
 
Thanks for the help.

---

### Post by rustybronco on 2008-03-19
Thought so...

and you're welcome.

---

