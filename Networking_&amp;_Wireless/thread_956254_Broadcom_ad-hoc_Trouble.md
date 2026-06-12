---
title: "Broadcom ad-hoc Trouble"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by Orbital_Armada on 2008-10-23
Hello, I'm rather new to Ubuntu and Linux as a whole but I'll try to do my best to get most the the important details down.
I have Ubuntu running on a Dell Inspiron 5150 and after some initial trouble with the wireless, I was able to get it working for access-points with the b43legacy driver. Unfortunately, I would really like to be able to use a ad-hoc network with this, and whenever I try to join or create one, the network manager thinks about it for a while, then fails and does nothing. Setting the mode to ad-hoc via terminal and taking the interface up and down doesn't seem to help at all either. Thanks for the help!

**uname**
```
Linux seantop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```



**lspci**: BCM 4306 rev.2
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

---

### Post by Ayuthia on 2008-10-23
It has been a while since I have done this.  Have you tried:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode ad-hoc essid <name of network>
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

---

### Post by Orbital_Armada on 2008-10-23
Thanks for the suggestion, but I more or less already did that with no results. I just tried it again to no avail. Thanks for your interest though.
Also, it seems that the other side of the ad-hoc is simply not receiving any packets at all.

---

