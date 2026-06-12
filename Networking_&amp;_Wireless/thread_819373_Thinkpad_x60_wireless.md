---
title: "Thinkpad x60 wireless"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by mmmendes on 2008-06-05
Hi,

I am a completely new ubuntu 8.04 user so I don't know much about this OS. My problem is that my wireless card it is not working under ubuntu (led turned off) but its working perfectly on windows XP (led on). What I should do in order to fix it? If possible give me help on a step-by-step bias as like I sad I'm a brand new user.

---

### Post by Ayuthia on 2008-06-05
> **mmmendes said:**
> Hi,

I am a completely new ubuntu 8.04 user so I don't know much about this OS. My problem is that my wireless card it is not working under ubuntu (led turned off) but its working perfectly on windows XP (led on). What I should do in order to fix it? If possible give me help on a step-by-step bias as like I sad I'm a brand new user.
Can you open up Terminal and type the following:
```
lspci -nn
```and post the results?  If you do not have an internet connection, please look for Network Controller or Ethernet Controller and post that information.  That will help determine what wireless card you have.

---

### Post by mmmendes on 2008-06-06
Thanks for your help. I'm just waiting for the next step. Following the results:

mauricio@mauricio-laptop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02) 
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02) 
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02) 
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02) 
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02) 
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a] mauricio@mauricio-laptop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02) 
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02) 
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02) 
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02) 
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02) 
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a] 
03:00.0 Network controller [0280]: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter [168c:0024] (rev 01) 
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b4) 
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 09) 
15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 18) 
mauricio@mauricio-laptop:~$ 
03:00.0 Network controller [0280]: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter [168c:0024] (rev 01) 
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b4) 
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 09) 
15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 18) 
mauricio@mauricio-laptop:~$

---

### Post by Ayuthia on 2008-06-10
It looks like you need to use the madwifi drivers.  You might check out this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi").   You should try out section 3.1 first and if it does not work, try section 4. 

Hope that helps.

---

### Post by mmmendes on 2008-06-10
Let me see if I understand

Section 3.1

I should go to the terminal ant type:

sudo apt-get install linux-restricted-modules madwifi-tools 

Is it?

[ ]s

---

### Post by Ayuthia on 2008-06-10
> **mmmendes said:**
> Let me see if I understand

Section 3.1

I should go to the terminal ant type:

sudo apt-get install linux-restricted-modules madwifi-tools 

Is it?

[ ]s

Yes. :)

---

### Post by Kaneda on 2008-06-23
> **Ayuthia said:**
> It looks like you need to use the madwifi drivers.  You might check out this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi").   You should try out section 3.1 first and if it does not work, try section 4. 

Hope that helps.

Hi Ayuthia, I was having a similar problem, and using section 4 of that guide worked for me.  Thanks a lot!

---

### Post by dy_wen on 2008-07-10
Hey,

A friend of mine also has a problem with her Thinkpad X60
She has a different kind of wireless card - I think (in this thread it is an atheros and here it is an Intel one - if I can decode this info correctly, that is).
What is very weird is that her wireless worked perfectly under Gutsy and has stopped working under Hardy.
It is not the card itself because it works in another operating system (one whose name I will not mention here ;-))

lspci -nn (type wireless card)

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 
943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 
945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] 
(rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 
945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller 
[8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High 
Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI 
Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI 
Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI 
Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI 
Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) 
USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) 
USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) 
USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) 
USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) 
USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge 
[8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC 
Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE 
Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 
Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus 
Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit 
Ethernet Controller [8086:109a]
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 
3945ABG Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b4)
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 
Controller [1180:0552] (rev 09)
15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 
SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 18)

thanks for having a look

---

