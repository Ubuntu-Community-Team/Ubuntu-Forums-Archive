---
title: "Cannot enable desktop effects"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Babysitteronacid on 2009-08-27
Hi, can anyone help a newbie? I've got Ubuntu up and running now. Webcam (if a little too red and dark), sound out of the loudspeakers at last, got it louder after opening volume etc.
So....what about all that eye candy I know is there somewhere for the having? After opening "system - appearance - visual effects - extras" I get this message "cannot enable desktop effects". I tried putting in the proprietary ati driver (flgw or some such)....but no joy.
I'm using an HP dv5. The ati g-card is actually fairly monster for a laptop - but I suspect that ati drivers are crap (it seems some other people have probs with ati as well).

colin@colin-laptop:~$ sudo lspci
[sudo] password for colin: 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0a:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
0a:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
colin@colin-laptop:~$ 

Hope this helps the helper
Thanks in advance.

---

### Post by NoaHall on 2009-08-27
System -> Admin -> Hardware drivers
Select and install the right driver.

Note - Ati do indeed suck.

---

### Post by super kim on 2009-08-27
the helpers will want to know what version of ubuntu you are using. this is especially relevant for ati cards.
you should do a google search for your card and ubuntu version, i did, and found pages like this one...
[http://www.paulocabido.com/ubuntu/ati-mobility-radeon-hd-3400-series-jaunty-xorg-and-compiz/](http://www.paulocabido.com/ubuntu/ati-mobility-radeon-hd-3400-series-jaunty-xorg-and-compiz/)

i hope it helps :)

---

### Post by Matthewthegreat on 2009-08-27
After you install the drivers, install compizconfig setting manager :)

---

### Post by Babysitteronacid on 2009-08-30
Version used is 9.04

---

