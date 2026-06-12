---
title: "Wireless problem with Intel Pro/wireless 2100"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by ujodarko on 2008-08-08
Hi :)

I have installed Ubuntu on Acer 371TCi and it has Intel Pro/wireless 2100 card. It seems to be mounted correctly because lshw -C Network shows:

root@administrator-laptop:~# lshw -C Network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:1e:63:a8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:07:d0:e6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=172.18.150.10 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
...

When I want to check 'Wireless connection' after left clicking on monitors in the 'Notification area', **'Enable Wireless' line is grey!** [COLOR="DarkRed"]**I can't put check sign cause it is not active?!?**[/COLOR]

System/Administration/Network settings: wireless connection is listed and it is in the roaming mode.

What should I do?

Thank you :)

---

### Post by ujodarko on 2008-08-09
Please help :(

---

### Post by ujodarko on 2008-08-09
Well, friend showed me on his laptop the same situation. His wifi card is functioning perfectly until he switch it off by pressing a wireless key on the keyboard!!!

And after that, he can not activate "Enable Wireless" in NM left click opened menu...

**Please can you help me with my Wireless keyboard button that does not work under [COLOR="Sienna"]Ubuntu[/COLOR] and works perfectly with WinXP?**

---

### Post by master night on 2008-08-09
i have the same problem too 
on my lap top 
please help

---

### Post by ujodarko on 2008-08-09
> **master night said:**
> i have the same problem too 
on my lap top 
please help

What lap top do you have?

p.s. on my comp wifi LED is turned on, but the button is dead #-o and card is not turned on!

---

### Post by ujodarko on 2008-08-09
[http://ubuntuforums.org/showthread.php?t=844426&page=4](http://ubuntuforums.org/showthread.php?t=844426&page=4)

there is solution!!!

I've pressed Fn+F2, after that Fn+F3, and wireless was ON!

:guitar:

---

### Post by ujodarko on 2008-08-12
In fact, Fn+F2 or F3 doesn't help!!! It seems to be the solution but that time I've pressed lots of keys ;) included the one for system suspend. Efect is similar as I was choosing: Suspend (from turn off menu).
[B]
Has anybody idea why WiFi card starts only when waking up from 'suspend' mode,right after having Ubuntu running?! 

Thnx[/B]

---

### Post by ujodarko on 2008-08-13
No ideas?:rolleyes:

---

