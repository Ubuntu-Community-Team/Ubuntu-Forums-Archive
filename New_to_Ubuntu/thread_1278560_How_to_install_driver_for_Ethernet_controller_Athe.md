---
title: "How to install driver for Ethernet controller: Atheros Communications Inc. AR242x 802"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by sumosu on 2009-09-29
Hi everyone!
I am a very new ubuntu user (version 8.10). I installed it on my Acer Aspire One laptop. Everything works OK except of wifi ;-( .

I have tried a lot of things. Nothing worked. After writing lspci in terminal I have this:

 	 	 abd@abd-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)



I have to say that I am NOT able to connect with internet via LAN cable! This is why I was not able to cope with this problem because many 'formulas' depends on this.



I will appreciate any help.

---

### Post by yeats on 2009-09-29
I'll mention that this works out of the box in Jaunty (9.04)...

---

### Post by LewRockwell on 2009-09-29
> **chrissharp123 said:**
> I'll mention that this works out of the box in Jaunty (9.04)...

yes

back-ups

secure your data

use 9.04 LiveCD to perform a fresh install
(after using the LiveCD test-drive function of course)

.

---

### Post by lkraemer on 2009-09-30
If you want to keep Ubuntu 8.10, and use the madwifi drivers PM me,
or you can search the forum for a HOWTO:

lkraemer

---

