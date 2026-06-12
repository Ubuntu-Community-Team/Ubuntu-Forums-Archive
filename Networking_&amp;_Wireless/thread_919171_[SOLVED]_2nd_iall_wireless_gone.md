---
title: "[SOLVED] 2nd iall wireless gone"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by intimatewipe on 2008-09-13
Hello,this should be simple but I can't figure it,I have an advent laptop that I installed ubuntu on(wiped xp) but I then found that I would need xp for some work stuff,so I re-installed xp and then Ubuntu,now I can't get wireless to work in ubuntu only(using an intel pro 2200bg card)it worked fine with ubuntu only and wireless works fine in xp,I notice the on/off switch is not working in ubuntu but on the first install the wireless was fine(not sure if the on off button worked then,I did not use it),its the same live cd I used the first time so its all a bit confusing,bit of a noob
so any help gratefully recieved.

---

### Post by intimatewipe on 2008-09-13
bash: shw: command not found
kris@kris-laptop:~$ shw -C 
bash: shw: command not found
kris@kris-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:3f:9d:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:15:00:51:34:42
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:18:f6:ad:85:6b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.1.64 multicast=yes
kris@kris-laptop:~$ 

does this help clarify anything,found command on other post

---

### Post by intimatewipe on 2008-09-13
Fixed,it was disabled,its just that the led on the on/off switch is not working in ubuntu,AAAAAAArgh:mad:

this was a clue;
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
*-network:1 DISABLED

the laptop is an advent but made by medion I think,matbe it'll help someone else,sorry if I've wasted anyones time:(

---

