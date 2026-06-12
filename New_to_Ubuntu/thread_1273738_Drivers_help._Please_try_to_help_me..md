---
title: "Drivers help. Please try to help me."
date: 2009-09-23
forum: New to Ubuntu
---

### Post by ubuntnoob512 on 2009-09-23
I need help installing drivers for my pc.

I have installed drivers on this thing before but not using linix (ubuntu 9.04).

I am sorry but i don't quite know what to put on here to help you search fore some driver downloads.

If you could find drivers for my computer that would be great.

I know that you will need th find which ones i need so just post a command that i should enter into terminal that would show what drivers i need.


Thanks

my other post:

[http://ubuntuforums.org/showthread.php?t=1272870](http://ubuntuforums.org/showthread.php?t=1272870)

---

### Post by gordintoronto on 2009-09-23
Why do you think you need drivers?  What is not working?

Linux handles drivers very, very differently from Windows.

---

### Post by 73ckn797 on 2009-09-23
The only drivers that I have ever had to install for Ubuntu were for the video card and Ubuntu detected that and I enabled it. The OS will recognize your hardware and it ought to work. Is there something in particular that is not working?

---

### Post by Iowan on 2009-09-23
Network cards (especially laptop wireless) sometimes need different drivers. At the risk of being redundant - what kind of driver are you looking for?

---

### Post by ubuntnoob512 on 2009-09-23
Well, the graphics have been very bad. And I couldn't figure out why because i have a nice graphics card.

I figured it was just how linux was until I tried to see the desktop effects up higher and it wouldent let me because I "dont have a graphics card installed"

---

### Post by ubuntnoob512 on 2009-09-23
I am on wifi right now and if you can read this that means I should have the wifi driver installed.

---

### Post by Yvan300 on 2009-09-23
What graphics card do you have, if it is an ATI card then your driver may be one of many that  has been discontinued by the company thus forcing you to use the free driver. If you really need the driver then there may be one available in intrepid ibex, that was the last release that had propietary drivers for those ati cards.

---

### Post by ubuntnoob512 on 2009-09-23
It is nvidia
how do i find more details about it in linux?

---

### Post by Yvan300 on 2009-09-23
Type in the terminal```
sudo lspci
```

It will give you a good bit of info :)

---

### Post by ubuntnoob512 on 2009-09-23
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
03:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
06:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)

---

### Post by pedro3005 on 2009-09-23
Go to System > Administration > Hardware Drivers and enable the propietary driver.

---

### Post by 3rdalbum on 2009-09-23
> **pedro3005 said:**
> Go to System > Administration > Hardware Drivers and enable the propietary driver.

You might need to go into System > Administration > Synaptic Package Manager and hit the Reload button first, to load the full list of packages, if you didn't have an internet connection available when you installed Ubuntu.

---

### Post by ubuntnoob512 on 2009-09-24
Oh, i did install them. thanks. 

visit my thread:

[http://ubuntuforums.org/showthread.php?t=1274638](http://ubuntuforums.org/showthread.php?t=1274638)

---

