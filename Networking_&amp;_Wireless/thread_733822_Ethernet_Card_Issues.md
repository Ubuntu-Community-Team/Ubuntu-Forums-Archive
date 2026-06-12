---
title: "Ethernet Card Issues"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by KnightAR on 2008-03-24
I'm currently running Ubuntu 7.10 Desktop version with 2 Ethernet cards (1 onboard, 1 PCI). The system is setup as a Internet gateway for my local network. The issue I am having is that for the past few months I've had to replace my 2nd Ethernet card (PCI) 3 times due to it just stops working in Ubuntu. My latest one, was a gigabyte linksys card that cost be a pretty penny yet it did the same exact thing. Basically this what happens:

A few hours before the Ethernet stops working, I ether notice a very huge slow down in Internet speeds and/or I get huge ping loss when it comes to network access. Then I loose access to my Linux system all together (Due to the 2nd Ethernet card being my local Ethernet adapter). Whenever I restart the system I keep an eye on the Ethernet lights, They stay on until it passes the BIOS, and it gets though the boot loader and then all lights go off and they blink maybe every 30-45 seconds.

At this point all I can do is two thing, Shutdown the computer and change the card to another PCI slot (and hope to god it works, it only has worked 1 out of 3 times) or replace the adapter altogether. Replacing the adapter every few months is costly and I choose not to if I can help it. I'm wondering if anyone else has seen this type of issue, or know of a way I can look into why this happens. I've never really messed around with the networking side of Linux beyond iptables, so I don't know what to do. However I know that the ip address is being assigned by checking 'ifconfig -a' and that it has the hardware address just like any other system.

And just in case someone mentions that it could be a bad adapter, Let me remind you this is the 3rd PCI card, and the old cards that has worked before works fine on other (windows based) systems. So the Ethernet card itself has nothing to do with it, It just seems like Ubuntu starts rejecting the card after time and I need to know a quick way to fix it without replacing the adapter. Also, All 3 network cards were different brands (3com, Netgear, Linksys) with entirely different chip sets so there's currently no common issue between adapters.

I hope someone can help, cause this is a serious issue, and if I can fix it a quick and easy way I would. I'm even thinking about buying a motherboard with two Ethernet adapters, but that still costs money.

Thanks for any help you can give me!

---

### Post by KnightAR on 2008-03-27
This issue has gotten even weirder. I re-installed Ubuntu 7.10 and it worked fine for almost 2 days. Now, It's done it again and this time the Live CD won't even allow the PCI Card to function. Someone, Please help!

>   *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 10
       serial: 00:1b:2f:28:73:f9
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.1 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=1GB/s


> ubuntu@ubuntu:/$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable
From 192.168.1.1 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.2 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3999ms

---

### Post by nzquiet1 on 2008-03-27
hmmm, in reading your post, I seem to have pretty much the same issue as you, where in Ubuntu seems to stop allowing access to the network card, yet it is there, listed in all the setups and ifconfigs, but just does not work.

---

### Post by nzquiet1 on 2008-03-29
Hi there, suggestion for you, check your router or switch.  Ie I had a very simular problem to yours, and have just taken my switch out of the network structure and put a different router in there and suddenly the internal network is up and running as if nothing was wrong.

Hope it works for you.

---

