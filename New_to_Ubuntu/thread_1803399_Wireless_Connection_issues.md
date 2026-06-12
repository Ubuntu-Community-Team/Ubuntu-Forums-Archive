---
title: "Wireless Connection issues"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by PayJ567 on 2011-07-13
Hello,

I'm completely new to linux stuff.

I'm having wireless connection issues my Asus Eee PC won't stay connected to my wireless connection port and also won't allow me to browse the internet.

 To run a command as administrator (user "root"), use "sudo <command>".
  See "man sudo_root" for details.
   
  joe@joe-1018P:~$ lspci
  00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
  00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
  00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
  00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
  00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
  00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
  00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
  00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
  00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
  00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
  00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
  00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
  00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
  00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
  00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
  01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
  02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
  joe@joe-1018P:~$ ^C
  joe@joe-1018P:~$

---

### Post by gandaran on 2011-07-13
```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```
do you have the right broadcom drivers installed?
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

