---
title: "Can't connect wirelessly"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by robrpb on 2008-11-01
I am new to Linux and Ubuntu. I just installed ver. 8-10 and everything seemed to install with no problems. I am now trying to connect wirelessly to the internet and I am not able to. I have a Dell Inspiron 8200 with XP Home ed. I have a Linksys WPC54G V.3 wireless card and a Linksys WRT54G V.3 router with WPA Personal security on channel 11.

I went to Linksys' website and could not find any Linux drivers. I was thinking this is at least one of my problems because I could not see any available wireless networks. Any help in getting my laptop to work wirelessly is greatly appreciated. Thanks.

---

### Post by Ayuthia on 2008-11-01
> **robrpb said:**
> I am new to Linux and Ubuntu. I just installed ver. 8-10 and everything seemed to install with no problems. I am now trying to connect wirelessly to the internet and I am not able to. I have a Dell Inspiron 8200 with XP Home ed. I have a Linksys WPC54G V.3 wireless card and a Linksys WRT54G V.3 router with WPA Personal security on channel 11.

I went to Linksys' website and could not find any Linux drivers. I was thinking this is at least one of my problems because I could not see any available wireless networks. Any help in getting my laptop to work wirelessly is greatly appreciated. Thanks.

Can you post the results of lspci -nn?  I can't remember which chipset this card is using.  Two of the versions use a Broadcom chipset and the other one is using something else.  Thanks!

---

### Post by robrpb on 2008-11-01
Here are the results. Thanks.

rob@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 Go] [10de:0112] (rev b2)
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4451 IEEE-1394 Controller [104c:8027]
07:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
rob@ubuntu:~$

---

### Post by Ayuthia on 2008-11-01
It looks like you will need to use ndiswrapper.  Here is a link that should help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by robrpb on 2008-11-02
I went to the above link and followed the directions. Everything seemed to install with no problems. The problem now is that the driver is not activated. I go to System>Administration>Hardware Drivers. It then displays "Broadcom B43 wireless Driver" and when I click to activate a new window pops up saying"Downloading and installing driver..." Nothing happens with the progress bar staying at 0%. I am able to connect to the internet with a wired connection and I am connected to the internet when I do the above. After about 5-10 minutes it appears it times out and the pop-up box disappears. I have tried this 3-4 times with the sames results. I restart the computer after each attempt because when I click activate after the pop-up box disappears, nothing happens. Your help is again appreciated. Thanks. Rob

---

### Post by Ayuthia on 2008-11-02
> **robrpb said:**
> I went to the above link and followed the directions. Everything seemed to install with no problems. The problem now is that the driver is not activated. I go to System>Administration>Hardware Drivers. It then displays "Broadcom B43 wireless Driver" and when I click to activate a new window pops up saying"Downloading and installing driver..." Nothing happens with the progress bar staying at 0%. I am able to connect to the internet with a wired connection and I am connected to the internet when I do the above. After about 5-10 minutes it appears it times out and the pop-up box disappears. I have tried this 3-4 times with the sames results. I restart the computer after each attempt because when I click activate after the pop-up box disappears, nothing happens. Your help is again appreciated. Thanks. Rob

If you have a wired connection you can try the following:
```
/usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```
It is the same thing as using the Hardware Drivers.

I will say that I am not 100% confident that it is going to work for you.  So far, I have not seen any 4318 rev 02 cards working with the b43 driver.  Only the 4318 rev 03.  Regardless, I hope that it works for you!

EDIT: I take back what I said.  There are some out there that do work!

---

### Post by robrpb on 2008-11-02
I tried "/usr/share/b43-fwcutter/install_bcm43xx_firmware.sh" and it came back "No such file or directory" I checked to make sure I was connected to the internet and I was. I also restarted the computer and got the same message.

---

### Post by Ayuthia on 2008-11-02
> **robrpb said:**
> I tried "/usr/share/b43-fwcutter/install_bcm43xx_firmware.sh" and it came back "No such file or directory" I checked to make sure I was connected to the internet and I was. I also restarted the computer and got the same message.

It sounds like b43-fwcutter did not get installed.  You can try installin b43-fwcutter from Synaptic or you can do the following from the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

---

### Post by robrpb on 2008-11-02
When I typed the second of the two commands I was asked to insert the disc labeled "Ubuntu 8.10 _Intrepid Ibex_ -Release i386 (20081029.5)" I inserted the disc I used to install Ubuntu and when I hit enter I keep getting the same message to insert the disc into the cdrom and hit enter. I am stuck at this point. Thanks.

---

