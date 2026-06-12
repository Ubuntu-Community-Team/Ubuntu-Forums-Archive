---
title: "Wireless card not found"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by b0rt on 2007-07-06
I have an Xterasys xn-2411b, i used  it first in edgy and using  wireless assistant  it worked perfectly, only plug and play. But now i made a clean install of Feisty, and it doesnt had the wireless assistant, so i install it from adept manager, but when i open the wireless assistant it says this :

" No usable wireless devices found"

And i had alredy plug the card in, so, what can i do? any helpt will be apreciated.

---

### Post by taylorsnow on 2007-07-06
I have had alot of luck using **NDISwrapper,** which is a tool that will take a windows driver for your card and wrap is so that is usable for linux. Here is the link....

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

If you are new to Linux and or the Terminal this might not be the easiest way for you.... but i havent found a driver yet that you cant make work with this....

---

### Post by b0rt on 2007-07-07
OK, i tried ndiswrapper and everything was going ok, but, when i put ```
bort@Garoth:~$ ndiswrapper -l
wlanpci : driver installed

```
it doesnt say anything about device present, so... what happend wrong? 
any help will be apreciated

---

### Post by kevdog on 2007-07-07
Please post the following and I think I may be able to help you:

lspci -nn
lshw -C network

Thanks

---

### Post by b0rt on 2007-07-07
thx man, this is what i get:
```
bort@Garoth:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge [8086:1a30] (rev 11)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge [8086:1a31] (rev 11)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go] [10de:0175] (rev a3)
02:07.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
02:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:0b.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 32)
02:0b.1 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 32)
02:0d.0 System peripheral [0880]: Toshiba America Info Systems SD TypA Controller [1179:0805] (rev 03)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)
bort@Garoth:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 10
       serial: 00:08:0d:cd:42:51
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.12 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:ce00-ceff iomemory:fcefff00-fcefffff irq:11
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
       resources: iomemory:50000000-500001ff irq:11

```
any idea? if you need more info just let me know

---

