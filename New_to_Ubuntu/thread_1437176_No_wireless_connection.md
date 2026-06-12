---
title: "No wireless connection"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by Augie1944 on 2010-03-23
I am a newbie to Ubuntu and need some help making a wireless connection to my Dell laptop.  The wired connection in Ubuntu works fine, but I do not see any wireless connection in the Network Manager.  If I add my SSID connection and MAC address, I still cannot make a connection.  I have used my wireless Win Vista OS for about 3 yrs. with no problem so the Ethernet controller must be OK.  I have searched these threads for several days and tried some of the suggestions made but have not solved my problem.  When I type sudo lshw -c network,  I see the network is disabled for the Ethernet interface. The logical name is eth0.  I have uninstalled the OS and reinstalled it.  I am 87 yrs. old and have used computers for many yrs. using many Win OSs and am quite interested in using Linux if possible.  But I certainly would like to use my laptop in a wireless connection.  It is in a network with my Win 7 desktop using a Linksys router.  Thanks for any help.

---

### Post by 2hot6ft2 on 2010-03-23
Welcome to the forum. First off we need to know what wifi adapter you have so we'll need some info.
Open a terminal
Applications > Accessories > Terminal
and run
```
lspci
```
That's LSPCI in lower case, and post the results.
```
lsusb
```
That's LSUSB in lower case, and post the results.

Highlight the results with your mouse and right click > copy then right click paste into the reply box.

---

### Post by Augie1944 on 2010-03-23
Thank you for your reply.  I am having trouble navigating the threads but will learn soon.  I did the operations:
cecil@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
cecil@ubuntu:~$ ^C
cecil@ubuntu:~$ 

and
cecil@ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cecil@ubuntu:~$ 

Thanks for offering to help.

---

### Post by cwbar_1 on 2010-03-23
While on the wired connection, navigate to "Hardware Drivers" and activate the Broadcom STA wireless driver.  It will download and install the proper drivers.  Then right click on the network manager icon, make sure enable wireless is ticked.  Left click on the network manager icon and choose your network.

---

### Post by Augie1944 on 2010-03-23
Wonderful.  It all worked just as you said.  Thanks so much for your time.  I should have asked several days ago.  How do I show that the problem is solved?

---

