---
title: "Wifi dropping"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by snippyv on 2010-05-10
Hello.

I'm a total noob to Linux....so please bear with me.

I'm running UNR Lucid........and every thing works except problems with the wifi. It connects but keeps dropping....making web surfing an impossibility.

My netbook is a Advent 4211.....which is a clone of a MSI Wind u100.

Everything was fine with Microsoft XP......the OS the netbook came with.

Bit rate will start at 54mbs.....but then gradually drop to 2mbs.

Why does it do this??? can it be fixed? Or am destined to go back to XP!!!!!!!

Any help greatly appreciated.


 :~$

---

### Post by Sealbhach on 2010-05-10
Just as a suggestion, install wicd, which is an alternative to Network Manager, and see if the same thing happens.

.

---

### Post by Nxion on 2010-05-10
> **snippyv said:**
> Hello.

I'm a total noob to Linux....so please bear with me.

I'm running UNR Lucid........and every thing works except problems with the wifi. It connects but keeps dropping....making web surfing an impossibility.

My netbook is a Advent 4211.....which is a clone of a MSI Wind u100.

Everything was fine with Microsoft XP......the OS the netbook came with.

Bit rate will start at 54mbs.....but then gradually drop to 2mbs.

Why does it do this??? can it be fixed? Or am destined to go back to XP!!!!!!!

Any help greatly appreciated.


 :~$

Lets see what wireless card you have in your machine. If you open up a terminal type the following and repost the output.

```
sudo lshw -C network
```

Thanks!

---

### Post by snippyv on 2010-05-10
Thanks for the quick reply.

-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:49:3a:11
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:c000(size=256) memory:ffd10000-ffd10fff(prefetchable) memory:ffd00000-ffd0ffff(prefetchable) memory:dfd00000-dfd0ffff(prefetchable)
  *-network
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:1d:92:c9:9f:5a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 ip=192.168.1.2 latency=0 multicast=yes wireless=802.11b/g  link
       resources: irq:17 ioport:b000(size=256) memory:dfc00000-dfc03fff
snippy@snippy-laptop:~$

---

### Post by Nxion on 2010-05-10
Thanks for that. Have you tried to update the machine via the built in network card? Maybe it just need a driver update?

---

### Post by snippyv on 2010-05-10
Thanks for the reply.

Errr..........so I need a new driver???

Sorry for my ignorance but I am new to Linux.

Cheers

---

### Post by snippyv on 2010-05-10
Where would I find the driver.........and load it???

---

### Post by Nxion on 2010-05-10
No worries :) I would say if you can plug the laptop into a wired network if you have one and try to run the Update Manager to get all the latest updates.

---

### Post by snippyv on 2010-05-11
Hello.

I have managed to update the system via the wifi.....but it still drops.

Sometimes the wifi will be ok for an hour or so........and sometimes it will drop after 2 minutes.

Is this something to do with the wifi card?

Can anyone please help...it will be a crying shame to go back to windows XP!!!!!:(

---

### Post by Nxion on 2010-05-11
From what I can see is that this might not just be you. It seems that there might be an issue with wifi and Realtek (RTL8187SE) drivers in 10.04. To be honest. I would submit a bug report on launchpad. Or if you want to, try to load 9.10 and see what happens. It seems to be an issue with the latest kernel.

---

### Post by bredman on 2010-05-11
Some wireless drivers have problems with some security settings. Usually WEP is not well supported and can degrade after time. I speak from bitter experience of trying to use WEP on Broadcom wireless hardware.

You don't say what type of security you are using. It may be worthwhile changing your security settings to see if this makes any difference. In an extreme case you might want to go naked for a while, depending on how friendly your neighbourhood is.

---

### Post by Sealbhach on 2010-05-12
Try installing wicd network manager. That way you can test if it's a problem with the regular network manager.

.

---

### Post by snippyv on 2010-05-12
Ok...thanks I'll try installing wcid and get back to you.

In the mean time....if its a problem with the wireless card......can anyone suggest a replacement that would work under Ubuntu??? I'm in the UK.

I'm desperate to get this to work....going back to XP will be a heart breaker! 

Thanks again for all the suggestions.

---

