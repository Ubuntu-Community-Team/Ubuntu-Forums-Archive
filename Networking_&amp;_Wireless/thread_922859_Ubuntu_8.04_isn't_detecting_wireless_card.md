---
title: "Ubuntu 8.04 isn't detecting wireless card"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by JackKnifeZero on 2008-09-17
Hello all,

My name is Jack. I'm new to Ubuntu and I'm really enjoying it so far. Everything seems to be fine except that I can't get Ubuntu to recognize my wireless card and I've been searching for solutions for hours. But I haven't been successful yet. I'm running Ubuntu 8.04 on my Dell Inspiron 1525. My wireless card is a Dell Wireless 1505 Draft 802.11n WLAN Mini-Card and the processor is an Intel Pentium Dual-Core. Also, I've noticed that some of you guys have asked for output from the command 'lspci' from the terminal and so I figured I'd give you guys my output just in case that helps. (By the way, my wired connection works and I'm using it right now, but I'd love to get this wireless issue fixed :KS)

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
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)


Any input would be great. Thanks in advance!

JackKnifeZero:)

---

### Post by chocbar31 on 2008-09-17
Try adding the backports.

Copy-and-paste into a terminal:

sudo apt-get install linux-backports-modules-hardy-generic

---

### Post by Ayuthia on 2008-09-17
The wl driver seems to work pretty well with your card.  The other option is to use ndiswrapper.  The b43 driver which comes with the kernel does not support the wireless-n cards yet.

If you want to download the wl driver and install it yourself, here is a guide:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)
You will most likely need to install build-essential:
```
apt-get install build-essential
```Or you can go into Synaptic (the GUI package manager) and install it from there.  You will need to have your install CD or else a working internet connection in Ubuntu.  If you don't have an internet connection and have the CD, you will need to add the CD to the repository list by doing the following:
```
sudo apt-cdrom add
```It will then ask you to load the CD.  Once that is done you can then do the following to install build-essential:
```
sudo apt-get update
sudo apt-get install build-essential
```Or you can run the update in Synaptic and install build-essential from there.

If you want to do the ndiswrapper route, here is a guide that might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
It says Feisty in the title, but it has been updated for Hardy and has been used by a lot of people in the forums with good results.  

Hope that helps.

---

### Post by JackKnifeZero on 2008-09-18
Alright, here is an update on my situation. I tried all the above methods.

Ayuthia, I had great success with the first method you mentioned at [http://ubuntuforums.org/showthread.php?t=896713]("http://ubuntuforums.org/showthread.php?t=896713"). I was able to get my wireless card to work...but I guess I messed something up when I was trying to make the change permanent, because when i rebooted it didn't work anymore. So I tried to go back and make it permanent but now it's not working at all. Is there anyway I can undo everything I did so that I can restart and this time do it correctly?

Thanks...Argh...I was soooo close!:)

---

### Post by JackKnifeZero on 2008-09-18
Nevermind....it's working....woot!!!!

I'm soooo happy! Thanks for all the help!!!

---

