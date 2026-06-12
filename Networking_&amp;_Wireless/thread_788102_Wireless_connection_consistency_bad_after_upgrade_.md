---
title: "Wireless connection consistency bad after upgrade to Hardy Heron."
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by nors on 2008-05-09
Hi fellow ubuntu users.

It seems that i as many others are experiencing problems with the wireless connection after upgrading to Ubuntu 8.04... It worked perfectly in Gusty :\

I browsed through all the other threads in here, but didn't stumble over similar issues.

I can connect more or less fine to my network which is encrypted by WPA on a Netgear router.

The problem is that when fx downloading heavy files my connection gets knocked out or entirely disconnected randomly now and then... I have no clue of what is going on so i seek your help... 


**lspci -nn**
```

root@christoffer-laptop:/home/christoffer# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)

```

**lshw -C network**
```

root@christoffer-laptop:/home/christoffer# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:84:6e:6c
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:60:6d:e6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.3 latency=64 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b

```

---

### Post by Joe of loath on 2008-05-09
this may sound a little silly, but what frequency is your processor? my 2.4ghz athlon knocked out my wireless cards, and when i opened the case i found the card EXACTLEY 2 wavelengths away from the cpu, and it was interfering with the connection. i moved the card along a slot, and it works fine.

---

### Post by nors on 2008-05-10
This is a laptop so i doubt this has any relevancy ?
IBM T42

---

### Post by nors on 2008-05-17
No one got a solution for this?

---

