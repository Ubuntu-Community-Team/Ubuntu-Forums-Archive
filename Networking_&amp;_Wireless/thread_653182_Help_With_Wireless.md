---
title: "Help With Wireless"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by TheDude07 on 2007-12-29
I have just installed Fiesty Fawn in a dual boot with Vista on an 8 month old Dell laptop.  Have not been able to get wireless networks to show up during roaming mode or connect during manual configuration.  

System:

Dell Inspiron E1505 (32 bit):

Intel Chipset
Broadcom 440x.10/100 Int Controller
Broadcom 802.11g Network Adapter

The wireless card works fine in windows but seems like it is turned off in Ubuntu.  I have read that there isn't very good support for the broadcom wireless adapters in linux.  

I've tried a few things to no avail including:

Using ndiswrapper to install the windows b44win.inf file
Downloading and installing new linux device drivers from the broadcom website...In which I recieved an        error upon loading the driver.

Also here is the results from lspci:

richard@richard-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller

03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)


I am thinking that maybe windows is turning off the card when shutting down...The only question is how to turn it back on when booting up Ubuntu or for that matter finding away to keep windows from turning it off.  I do have a short cut key to turn the wireless on and off which works in windows but doesn't seem to work in Ubuntu.

Does Anybody have any ideas???

---

### Post by cdtech on 2007-12-30
Same card here. Best tutorial for this model > [[COLOR="DarkRed"].:: Here ::.[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")

---

