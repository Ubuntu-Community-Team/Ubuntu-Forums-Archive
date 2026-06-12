---
title: "Ubuntu network wireless firmware missing"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by Chimaster345 on 2011-07-10
Hey guys I just downloaded ubuntu alongside windows xp my internet works fine on windows but on ubuntu when I click on the connection button it says firmware missing.
Thanks for help in advance.

---

### Post by jimrz on 2011-07-10
> **Chimaster345 said:**
> Hey guys I just downloaded ubuntu alongside windows xp my internet works fine on windows but on ubuntu when I click on the connection button it says firmware missing.
Thanks for help in advance.
we need a bit more info ... what is the network card you are trying to use? need the make & model... in order to even attempt to help

---

### Post by Chimaster345 on 2011-07-10
> **jimrz said:**
> we need a bit more info ... what is the network card you are trying to use? need the make & model... in order to even attempt to help
 My network card is Realtek RTL8139/810x Family Fast Ethernet NIC.

---

### Post by wep940 on 2011-07-10
Also, when you say "along side" do you mean a WUBI install or did you make it dual-boot?  It makes a difference as sometimes things can be a little difficult in WUBI, and it's really only meant for testing anyway.  Any real use should be in dual-boot or even stand alone.

---

### Post by grahammechanical on 2011-07-10
Do you see an icon on the top panel that looks like a small circuit board? Actually, it looks like an adapter card that plugs into a PCI slot. When the wireless driver is not installed as part of the installation the usual procedure is to make a connection to the router/modem by cable and then click on that icon which will load the Additional Drivers utility where you a can activate any drivers that are available. Then restart and click on the network icon again. You can also find this utility under System Settings.

If you cannot make a wired Internet connection for some reason then it becomes a little more complicated.

Here is a link

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

It will help you see what you can do and what information is useful to the forum when giving advice.

By the way, We are assuming that you are using 11.04 under the Unity user interface. Anything different will affect the directions that are given.

Regards.

---

### Post by Chimaster345 on 2011-07-10
> **wep940 said:**
> Also, when you say "along side" do you mean a WUBI install or did you make it dual-boot? It makes a difference as sometimes things can be a little difficult in WUBI, and it's really only meant for testing anyway. Any real use should be in dual-boot or even stand alone.
 I used wubi.

---

### Post by Chimaster345 on 2011-07-10
> **grahammechanical said:**
> Do you see an icon on the top panel that looks like a small circuit board? Actually, it looks like an adapter card that plugs into a PCI slot. When the wireless driver is not installed as part of the installation the usual procedure is to make a connection to the router/modem by cable and then click on that icon which will load the Additional Drivers utility where you a can activate any drivers that are available. Then restart and click on the network icon again. You can also find this utility under System Settings.
 
If you cannot make a wired Internet connection for some reason then it becomes a little more complicated.
 
Here is a link
 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
 
It will help you see what you can do and what information is useful to the forum when giving advice.
 
By the way, We are assuming that you are using 11.04 under the Unity user interface. Anything different will affect the directions that are given.
 
Regards.
 I am going to follow the directions in the link once i find an ethernet cord. Thanks.

---

### Post by Chimaster345 on 2011-07-10
> **Chimaster345 said:**
> I am going to follow the directions in the link once i find an ethernet cord. Thanks.
 And sadly I dont have an ethernet cord. any other ways? Maybe get the firmware onto a flashdrive then install it while in ubuntu? if thats possible.

---

### Post by wildmanne39 on 2011-07-10
> **Chimaster345 said:**
> And sadly I dont have an ethernet cord. any other ways? Maybe get the firmware onto a flashdrive then install it while in ubuntu? if thats possible.
Hi, that might be possible but how are you going to get it on a flash drive with no internet connection? You can use a friends computer to download the required driver, or if you have windows you can download it to the desktop of windows then boot ubuntu and click on your windows drive go to desktop and copy it to ubuntu.

---

### Post by wep940 on 2011-07-11
> **Chimaster345 said:**
> My network card is Realtek RTL8139/810x Family Fast Ethernet NIC.That is the hard-wire ethernet adapter, not your wireless. I suspect your wireless is probably going to be a Broadcom chipset since you get the firmware missing message.
 
In order for us to determine the chipset, and therefore the driver for you, please do the following:
 
- open a terminal window (applications/accessories/terminal)
- type: lspci <press enter>
- type: lsusb <press enter>
 
Post those outputs back here. Even better, look in your Windows install and go to the device manager and look up your wireless there - it should tell you what it is. Post that back here as well.
 
Also, what make and model is the PC?

---

### Post by Chimaster345 on 2011-07-11
> **wep940 said:**
> That is the hard-wire ethernet adapter, not your wireless. I suspect your wireless is probably going to be a Broadcom chipset since you get the firmware missing message.
 
In order for us to determine the chipset, and therefore the driver for you, please do the following:
 
- open a terminal window (applications/accessories/terminal)
- type: lspci <press enter>
- type: lsusb <press enter>
 
Post those outputs back here. Even better, look in your Windows install and go to the device manager and look up your wireless there - it should tell you what it is. Post that back here as well.
 
Also, what make and model is the PC?
 Broadcom 802.11b/g WLAN is my Wireless card.
My computer is a Presario C300.
I could not get the terminal info because it was too long to write down.

---

### Post by wildmanne39 on 2011-07-11
Hi, run the commands then copy them to a flash drive and use the computer with internet to post them here, because we need the exact card to help you because there are many different broadcom cards.

---

### Post by Chimaster345 on 2011-07-11
> **wildmanne39 said:**
> Hi, run the commands then copy them to a flash drive and use the computer with internet to post them here, because we need the exact card to help you because there are many different broadcom cards.
 
[SIZE=3][FONT=Times New Roman]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]joey@ubuntu:~$ lsusb[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 003 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 001 Device 002: ID 090c:1000 Feiya Technology Corp. Flash Drive[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/SIZE]

---

### Post by gandaran on 2011-07-11
```
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```
follow this thread
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by wildmanne39 on 2011-07-11
Hi, that is the same guide I was going to give you.

---

### Post by wep940 on 2011-07-11
+1 on the "all" firmware package mentioned in the link.  However, for the firmware cutter, etc., that is actually on the installation CD in the /pool/main/b folder - you don't need to download it and copy it, etc..  When booted to Ubuntu, put the installation CD in your drive - if a message comes up about a source CD just cancel the message.  Use "Places" to explore the CD - go to the /pool/main/b folder and you'll find what you need for everything but the firmware itself.  I've used the firmware file mention in the link and it saved my behind.
 
Good luck!

---

