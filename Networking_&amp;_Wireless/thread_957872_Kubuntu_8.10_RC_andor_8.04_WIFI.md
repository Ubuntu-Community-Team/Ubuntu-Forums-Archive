---
title: "Kubuntu 8.10 RC and/or 8.04 WIFI"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by whos2know on 2008-10-24
Hi,

I have recently downloaded Kubuntu 8.10 RC and also 8.04.   I am unable to get the WIFI to work on both of them.  I know how to do it on Ubuntu (but it's been awhile) but on Kubuntu I have no clue.  I have a Linksys Wireless G PCI Model No. WMP54GS.  I do not have any internet access besides WIFI although I can download whatever that is needed from the Ubuntu side.  If possible can someone explain how I would go about doing this and what files I would need to download to make this painless as possible.  Thank you very much!

-Bobby

---

### Post by Ayuthia on 2008-10-24
> **whos2know said:**
> Hi,

I have recently downloaded Kubuntu 8.10 RC and also 8.04.   I am unable to get the WIFI to work on both of them.  I know how to do it on Ubuntu (but it's been awhile) but on Kubuntu I have no clue.  I have a Linksys Wireless G PCI Model No. WMP54GS.  I do not have any internet access besides WIFI although I can download whatever that is needed from the Ubuntu side.  If possible can someone explain how I would go about doing this and what files I would need to download to make this painless as possible.  Thank you very much!

-Bobby

Can you post the results of:
```
lspci -nn
```Linksys uses a variety of chipsets for the same model.  This will help us identify which one you have.

---

### Post by whos2know on 2008-10-24
Thank you for your reply... here is the info from that command...

cbobby@bobby-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a1] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1)
00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1)
00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1)
00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1)
00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1)
00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1)
00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1)
00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1)
00:02.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03bc] (rev a1)
00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:0e.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:0e.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a3)
00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:0f.1 Audio device [0403]: nVidia Corporation MCP55 High Definition Audio [10de:0371] (rev a2)
00:11.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a3)
00:12.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a3)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600 GT [10de:0402] (rev a1)
02:07.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
02:09.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
bobby@bobby-desktop:~$


Thank you again!!

-Bobby

---

### Post by Ayuthia on 2008-10-24
Here is a set of instructions for 8.10.  This is a revised version of this [thread]("http://ubuntuforums.org/showthread.php?t=779754")(changed because the firmware is different in Intrepid):

[B]Option 2
For those without a working internet connection[/B]

**If you have a Intrepid install CD, **
Insert your CD and do the following:
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install b43-fwcutter
```
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**
Now skip down to the Downloading Firmware section.

**If you don't have a Intrepid install CD**
You will have to find a place with a working internet connection.  Go to this link:
[http://packages.ubuntu.com/intrepid/utils/b43-fwcutter](http://packages.ubuntu.com/intrepid/utils/b43-fwcutter)
Download the version that you need--amd64 for 64-bit and i386 for 32-bit.  Copy the file to your home directory and do the following:
64-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-4ubuntu1_amd64.deb
```
It is possible that the _011-4ubuntu1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

32-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-4ubuntu1_i386.deb
```
It is possible that the _011-4ubuntu1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

**Downloading Firmware**
Both 32-bit and 64-bit:
You will still need to find someplace with a working internet connection and download the following files:
```
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```
Copy those files to your home directory.  In the Terminal/Konsole/xterm window do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```

For those of you who are configuring your /etc/network/interfaces, you might need to do:
```
sudo /etc/init.d/networking restart
```That will restarting your network and will read through the /etc/networking/interfaces to connect.

Hope that helps.  I have not seen any results about how the 4318 cards are doing in Intrepid but I know that the card did not do too well in Hardy.

---

### Post by azakarea on 2008-10-25
hi 
this is my second day only using the UBUNTU 8.04 and ia m facing a big problem when i finish the installation every thing working ok but the graphic Card ( Nvidia ) and i knew how to install the driver for it but the problem happeens afyer letting the updates take place on the system the wirless card and the full networking not functional so i have to re format and install but no automatic update any more . so it seems that the Installtion cd have the driver so i will post the result of the command you gac=ve before so i can use it later :
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72M [GeForce Go 7400] [10de:01d8] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
05:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

thanks 
Best regards you all linux team

---

### Post by whos2know on 2008-10-25
Thank you very very much!! It works great!! You where very helpful!!

have a wonderful day!

-Bobby

---

### Post by monjope on 2008-11-12
Thank you very very much!! :razz:

---

### Post by susanw on 2009-04-15
Ayuthia, 

Thank you very much for your post on how to get broadcom working. I've been searching for a way to install the driver for ages when not being on the internet on that computer and your solution was quick, to the point and well written, cheers,

susan

---

### Post by amelie1214 on 2009-09-30
> **Ayuthia said:**
> Here is a set of instructions for 8.10.  This is a revised version of this [thread]("http://ubuntuforums.org/showthread.php?t=779754")(changed because the firmware is different in Intrepid):

[B]Option 2
For those without a working internet connection[/B]

**If you have a Intrepid install CD, **
Insert your CD and do the following:
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install b43-fwcutter
```**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**
Now skip down to the Downloading Firmware section.

**If you don't have a Intrepid install CD**
You will have to find a place with a working internet connection.  Go to this link:
[http://packages.ubuntu.com/intrepid/utils/b43-fwcutter](http://packages.ubuntu.com/intrepid/utils/b43-fwcutter)
Download the version that you need--amd64 for 64-bit and i386 for 32-bit.  Copy the file to your home directory and do the following:
64-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-4ubuntu1_amd64.deb
```It is possible that the _011-4ubuntu1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

32-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-4ubuntu1_i386.deb
```It is possible that the _011-4ubuntu1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

**Downloading Firmware**
Both 32-bit and 64-bit:
You will still need to find someplace with a working internet connection and download the following files:
```
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```Copy those files to your home directory.  In the Terminal/Konsole/xterm window do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```For those of you who are configuring your /etc/network/interfaces, you might need to do:
```
sudo /etc/init.d/networking restart
```That will restarting your network and will read through the /etc/networking/interfaces to connect.

Hope that helps.  I have not seen any results about how the 4318 cards are doing in Intrepid but I know that the card did not do too well in Hardy.



Hi!!
 I have Kubuntu installed in an acer aspire 5520, with a signalup wireless card, and I can't get the wireless to work. I have followed the suggestions above but it just doesn't work, on one side when trying to do

sudo ifconfig wlan0 up

it says that 
wlan0: ERROR while getting interface flags: No such device
and when I try to look for wireless networks it says that is unable to find wireless interfaces. Any suggestions?I don't know much about Linux and I really would like it to work!
 Thanks very much!!!

---

### Post by Ayuthia on 2009-09-30
> **amelie1214 said:**
> Hi!!
 I have Kubuntu installed in an acer aspire 5520, with a signalup wireless card, and I can't get the wireless to work. I have followed the suggestions above but it just doesn't work, on one side when trying to do

sudo ifconfig wlan0 up

it says that 
wlan0: ERROR while getting interface flags: No such device
and when I try to look for wireless networks it says that is unable to find wireless interfaces. Any suggestions?I don't know much about Linux and I really would like it to work!
 Thanks very much!!!

Can you go into the Konsole and post the results of:
```
lspci -nn
lshw -C network
```It will help us see which wireless card you have along with what wireless driver your system is trying to use.

---

### Post by Crandom on 2009-11-08
@Ayuthia: Thank you SO SO much. I have been living with ndiswrapper for years trying to  find a solution!

---

