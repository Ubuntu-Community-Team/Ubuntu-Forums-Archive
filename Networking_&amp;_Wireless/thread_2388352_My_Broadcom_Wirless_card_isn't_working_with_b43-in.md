---
title: "My Broadcom Wirless card isn't working with b43-installer"
date: 2018-04-01
forum: Networking &amp; Wireless
---

### Post by cowboyenvy2 on 2018-04-01
PC 1: 

So my system is installed from a USB stick using lubuntu 17.10.01 alternative ISO and is the QT-Desktop (non-minimal)
This device shows no network interface for the broadcom wireless card at all

Computer Name        : Inspiron-1501
Kernel        : Linux 4.13.0-37-generic (x86_64)
Version        : #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018
C Library        : GNU C Library / (Ubuntu GLIBC 2.26-0ubuntu2.1) 2.26
Distribution        : Ubuntu 17.10

```

~$ lspci -vnn | grep 14e4
05:00.0 Network controller [0280]: Broadcom Limited BCM4311 802.11a/b/g [14e4:4312] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Limited BCM4401-B0 100Base-TX [14e4:170c] (rev 02)


~$ sudo apt search b43

b43-fwcutter/artful,now 1:019-3 i386 [installed,automatic]
  utility for extracting Broadcom 43xx firmware

firmware-b43-installer/artful,artful,now 1:019-3 all [installed]
  firmware installer for the b43 driver

~$ sudo apt search bcmwl
bcmwl-kernel-source/artful 6.30.223.271+bdcom-0ubuntu3 amd64
  Broadcom 802.11 Linux STA wireless driver source


```
PC 2

So my system is installed from a USB stick using lubuntu 17.10.01 alternative ISO and is the QT-Desktop (minimal) using wicd-curses
This computer shows a wlan network interface with a mac address of [00:1b:fc]("https://aruljohn.com/mac/001BFC9E5550") which is 'asustek' and no networks available with when scanning wifi

Computer Name        : Latitude-D531
Kernel        : Linux 4.13.0-37-generic (i686)
Version        : #42-Ubuntu SMP Wed Mar 7 14:12:29 UTC 2018
C Library        : GNU C Library / (Ubuntu GLIBC 2.26-0ubuntu2.1) 2.26
Distribution        : Ubuntu 17.10


```

~$ lspci -vnn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Limited NetXtreme BCM5755M Gigabit Ethernet PCI Express  [14e4:1673] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Limited BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

~$ sudo apt search b43

b43-fwcutter/artful,now 1:019-3 i386 [installed,automatic]
  utility for extracting Broadcom 43xx firmware

firmware-b43-installer/artful,artful,now 1:019-3 all [installed]
  firmware installer for the b43 driver

~$ sudo apt search bcmwl
bcmwl-kernel-source/artful 6.30.223.271+bdcom-0ubuntu3 amd64
  Broadcom 802.11 Linux STA wireless driver source


```

PC 3

So my system is installed from a USB stick using lubuntu  17.10.01 ISO and is the standard graphical install
This computers broadcom card functions properly.

Computer Name        : Inspiron-e1705
Kernel        : Linux 4.13.0-37-generic (i686)
Version        : #24-Ubuntu SMP Mon Dec 18 17:29:35 UTC 2017
C Library        : GNU C Library / (Ubuntu GLIBC 2.26-0ubuntu2.1) 2.26
Distribution        : Ubuntu 17.10


```

~$ lspci -vnn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Limited BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
05:00.0 Network controller [0280]: Broadcom Limited BCM4311 802.11b/g [14e4:4311] (rev 01)

~$ sudo apt search b43

b43-fwcutter/artful,now 1:019-3 amd64 [installed,automatic]
  utility for extracting Broadcom 43xx firmware

firmware-b43-installer/artful,artful,now 1:019-3 all [installed]
  firmware installer for the b43 driver

~$ sudo apt search bcmwl
bcmwl-kernel-source/artful 6.30.223.271+bdcom-0ubuntu3 amd64
  Broadcom 802.11 Linux STA wireless driver source


```

I'm tempted to chalk the issue up to either the alternative ISO or issues with Broadcom and QT, I had previously installed 17.01 on the latitude-d531 and had wireless working on both the amd64 and i386 variants. 

Any suggestions to avoid reinstalling the operating system again on these non-working PCs would be appreciated.

---

### Post by wildmanne39 on 2018-04-01
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

---

### Post by cowboyenvy2 on 2018-04-01
as a by the by, both computers work with linksys USB adapters.

---

### Post by praseodym on 2018-04-01
Try this one:

```
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot

---

### Post by cowboyenvy2 on 2018-04-01
Thank you, that fixed my issue on the Inspiron-1501
replacing wicd-curses with networkmanager-gnome worked for my latitidue-d531 so all devices are presently working, thanks

---

### Post by uxama on 2018-04-17
This thread helped me solve this (senior noob), though it's using the installer, afaik.
[https://forums.linuxmint.com/viewtopic.php?f=53&t=232330](https://forums.linuxmint.com/viewtopic.php?f=53&t=232330)

---

