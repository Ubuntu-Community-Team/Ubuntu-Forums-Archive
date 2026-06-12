---
title: "[SOLVED] No wifi connection"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by nnjond on 2008-08-14
Hi,

I've installed Hardy on a brand new laptop. The icon on my panel claims there is no network connection. Will it find one if I move to a wifi hotspot?

Thanks.

---

### Post by cdtech on 2008-08-14
Yes, if it is configured properly. You can check to see if your wireless is working by issuing the command line:
```
iwconfig
```
(This will show your wireless configuration).

---

### Post by nnjond on 2008-08-14
Oh,oh...

iwconfig

lo   No wireless con...

eth0 no wireless extensions.

What should I do?

---

### Post by Kevbert on 2008-08-14
Please post the terminal output of
```
lspci
```
It looks like you may need to install some firmware drivers.

---

### Post by nnjond on 2008-08-14
nnjond@nnjond-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01) 
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04) 
nnjond@nnjond-laptop:~$ iwconfig

---

### Post by Kevbert on 2008-08-14
The dreaded Atheros wireless...  This adapter seems to be a bit hit or miss when it comes to firmware drivers and Linux.  You could try the method [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5585704#post5585704") and use the windows .inf driver.  It assumes that your using 8.04 Hardy Heron.

---

### Post by nnjond on 2008-08-14
Thanks for your help. I seem to have follwed all the steps up to:

You'll need to point the program to where your Windows INF file is (on the right of the box is a folder icon, click on this and browse to the driver.

I dont know where the Windows INF file is?

---

### Post by Kevbert on 2008-08-14
The XP drivers can be found via this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766169").  Click on the link and save the file to your desktop.  No double click on the file and extract it to the desktop (extract here).  Now you can point the program to the Desktop and within the newly extracted folder on your desktop.

---

### Post by nnjond on 2008-08-14
The folder I dld has 2 files in it. I seem to have installed the .inf successfully but idon't know what to do with the .sys. Should I have a connection now?

---

### Post by Kevbert on 2008-08-15
You should now be able to connect to a network.  If you right-click on the 2 monitor icon in the top right-hand corner of your desktop you need to check that both Enable Networking and Enable Wireless are ticked.  If wireless is greyed out you still have problems.
If you left click on the icon you should have a list of nearby wireless networks (if there are any).
If there are still problems you need to go to Applications-Accessories-Terminal and enter the following commands
```
ifconfig
iwconfig
iwlist scanning
```
and post back the outputs.  To copy the output you can use Ctrl+Shift+C and to paste here Ctrl+V.

---

