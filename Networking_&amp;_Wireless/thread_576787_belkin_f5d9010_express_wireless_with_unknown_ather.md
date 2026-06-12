---
title: "belkin f5d9010 express wireless with unknown atheros chopset in x64"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by anfractuosities on 2007-10-15
***********not 9010 but 8071
***********not 9010 but 8071

lspci -nn

```
~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M56P [Radeon Mobility X1600] [1002:71c5]
02:00.0 Network controller [0280]: Atheros Communications, Inc. Unknown device [168c:0024] (rev 01)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
05:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832]
05:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:01.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)
05:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
```


lshw  -C network
```
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:11:d6:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.160.130 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ff8ff000-ff8fffff irq:17
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:ff7f0000-ff7fffff irq:10
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@05:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:85:77:35
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:d800-d8ff iomemory:ff9ffc00-ff9ffcff irq:18
```


I could not find my wireless device here

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

or here

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

[


I am trying to get this card to replace my working, but malfunctioning itel pro wireless mini pci card.  Can I have them both installed at once?  I will be sending my minipci card to get a replacement and wanted to use thise expresscard in the meantime.

***********not 9010 but 8071
***********not 9010 but 8071
***********not 9010 but 8071

---

### Post by anfractuosities on 2007-10-15
anyone???

---

### Post by jingo811 on 2007-10-16
I don't seem to be able to find Belkin 9010 nor 8071on both the databases :-k
Kevdog is usually good at these things I can poke him for you.  But maybe someone else know how to help you out more properly also.

---

### Post by rustybronco on 2007-10-16
[http://www.belkin.com/support/download/downloaddetails.asp?lang=1&download=1743](http://www.belkin.com/support/download/downloaddetails.asp?lang=1&download=1743)

[https://answers.launchpad.net/ubuntu/+question/4972](https://answers.launchpad.net/ubuntu/+question/4972)
"I'm pretty sure that the card has an Airgo Chipset."

[http://www.yesmicro.com/26442BTD-discount-BELKIN+COMPONENTS-F5D9010-Card+Bus-G-MIMO-WLS.aspx](http://www.yesmicro.com/26442BTD-discount-BELKIN+COMPONENTS-F5D9010-Card+Bus-G-MIMO-WLS.aspx)

[http://www.news.com/Belkin-looks-to-speed-Wi-Fi-products-with-Airgo-tech/2100-7351_3-5300569.html](http://www.news.com/Belkin-looks-to-speed-Wi-Fi-products-with-Airgo-tech/2100-7351_3-5300569.html)

[http://sourceforge.net/projects/agnx80211driver](http://sourceforge.net/projects/agnx80211driver)

---

### Post by anfractuosities on 2007-10-16
> **rustybronco said:**
> [http://www.belkin.com/support/download/downloaddetails.asp?lang=1&download=1743](http://www.belkin.com/support/download/downloaddetails.asp?lang=1&download=1743)

[https://answers.launchpad.net/ubuntu/+question/4972](https://answers.launchpad.net/ubuntu/+question/4972)
"I'm pretty sure that the card has an Airgo Chipset."

[http://www.yesmicro.com/26442BTD-discount-BELKIN+COMPONENTS-F5D9010-Card+Bus-G-MIMO-WLS.aspx](http://www.yesmicro.com/26442BTD-discount-BELKIN+COMPONENTS-F5D9010-Card+Bus-G-MIMO-WLS.aspx)

[http://www.news.com/Belkin-looks-to-speed-Wi-Fi-products-with-Airgo-tech/2100-7351_3-5300569.html](http://www.news.com/Belkin-looks-to-speed-Wi-Fi-products-with-Airgo-tech/2100-7351_3-5300569.html)

[http://sourceforge.net/projects/agnx80211driver](http://sourceforge.net/projects/agnx80211driver)



Its not the 9010 its the 8071...i was mistaken

---

### Post by jingo811 on 2007-10-16
> with unknown atheros chopset in x64
Hehe you said chopset :) 
And I'm still having trouble finding your correct device in both the databases.  If the Ndiswrapper list doesn't mention your device at all then that means you're the Neill Armstrong for your wireless device.  Your're the one that has to take the first steps before anybody else.

---

### Post by anfractuosities on 2007-10-16
crap...

---

### Post by jingo811 on 2007-10-17
crap indeed :)

---

### Post by kevdog on 2007-10-18
If you have the 64 bit windows xp driver I think that it would most likely work with ndiswrapper.  64 bit networking card -- yes indeed it would be interesting, however I would definitely give ndiswrapper a shot -- thats the only way I know how to do it.

---

### Post by jingo811 on 2007-10-18
Yeah so do you have a Wireless setup CD for you Belkin F9D8071 that have any of the below folders ?
[LIST]
[*]/Win XP/drivers
[*]/Win 2000/drivers
[*]/Win Vista/drivers
[/LIST]

containing 2 files with these file types 
*.inf
*.sys

---

### Post by teaker1s on 2008-02-18
chip set is atheros AR5418 and can be made to work on debian with madwifi 
experimental driver for ar5008 which debian etch works perfectly with
[here]("http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008")

monitor mode works- I don't get any lights on it but airsnort works:guitar:

---

