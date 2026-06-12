---
title: "Turning on wireless"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by Nicolas Pham-Dinh on 2008-03-03
I am rather new to Ubuntu. I have installed Gutsy on a Toshiba Tecra S1 laptop and the Intel PRO/Wireless LAN 2100 3B Mini PCI Adapter does not seem to turn on. The wifi card is detected and the correct driver is installed (ipw2100) but when I go to "System - Administration - Network" it shows only "wired" and "modem" connections. No "wireless" even though the wireless switch and light are on. I noticed there is a Fn-F8 special key stroke to turn on wifi as well but this Fn key combinations don't work either as many other Fn key combinations. My feeling is that there is probably two steps to turn on the wireless (the wifi "power on" switch + Fn-F8 ) but I cannot accomplish the second step ( Fn-F8 ). I don't really care about making the Fn-F8 to work as long as I can get a workaround solution to enable wifi. This thread shows a similar problem but with an HP TC1100 tablet pc: 

[http://ubuntuforums.org/showthread.php?t=527751&highlight=ipw2100](http://ubuntuforums.org/showthread.php?t=527751&highlight=ipw2100)

I've searched many hours to find a solution but to no avail. Any help would be greatly appreciated. Thank you in advance.

---

### Post by wieman01 on 2008-03-04
Hello, 

Please open a terminal and post the results of:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces

---

### Post by Nicolas Pham-Dinh on 2008-03-04
sudo iwlist scan:

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sudo lshw -C network:

>   *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=128 maxlatency=34 mingnt=2

  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:a0:d1:d8:83:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.2.15 latency=128 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

sudo cat /etc/network/interfaces:
> 
auto lo
iface lo inet loopback

---

### Post by wieman01 on 2008-03-04
You're right, it's turned off:
> *-network:0 UNCLAIMED
description: Network controller
Do you have Windows on that machine? It might help if you booted Windows and turned it on using "network connections"... Just an idea.

---

### Post by Nicolas Pham-Dinh on 2008-03-04
Alright here's the scoop: I am installing Ubuntu on this laptop for a friend and just found out that its an ex-corporate machine, which probably had their laptops wireless-disabled to protect their data. Grrr. I'm gonna get a PCMCIA A/B wireless adapter which will most likely work. In any event, thank you for your kind help and I apologize for wasting your time.

Regards,
Nicolas

---

### Post by wieman01 on 2008-03-04
No problem. See you next time.

---

### Post by consdel on 2008-05-12
> **wieman01 said:**
> You're right, it's turned off:

Do you have Windows on that machine? It might help if you booted Windows and turned it on using "network connections"... Just an idea.

My girlfriend's Acer Travelmate 660 has this problem (with that chipset): it works only after a reboot of windows, doesn't work with a cold start.
any ideas?

---

### Post by wieman01 on 2008-05-12
> **consdel said:**
> My girlfriend's Acer Travelmate 660 has this problem (with that chipset): it works only after a reboot of windows, doesn't work with a cold start.
any ideas?
Is it perhaps turned off in the Bios?

---

### Post by stpk4 on 2008-05-23
Hi guys
I'm having the EXACT problem as the original poster, i have the exact same outputs from the lshw,iwlist scan and lspci,
Im trying to turn on the ipw2100 mini pci in ubuntu 8.04, but i have no idea
how to solve this?

Thanks,
Jackson

---

