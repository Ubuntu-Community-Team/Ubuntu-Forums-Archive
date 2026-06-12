---
title: "Where's me Linksys WAG354G wireless gone??"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by SilverSatori on 2007-01-20
Hey peepz,

N00b to Ubuntu here, got my wired net connection running a ok (hence being on here! :guitar: ) ... however, I cannot get my wireless to work.

I've spent a few hours looking around the forum and the docs but cannot find anything that has helped .... not that I have understood most of it!!

I can understand as much as enabling the wireless in >>system>>administration>>networking, but I don't know what it means by Network Essid .... I know what ssid is for my router (WAG354G) so is Essid the same?... and I also don't know what it means when asking for network password ... I don't use one ... being in the middle of nowhere and having no neighbours!!

Any hoo, here are the results from my terminal queries...

LSPCI:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:01.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)

LSUSB:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

IWCONFIG:

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

.....

Any help will be most appreciated .... I feel like I am back in the stone ages using wires again!!:lolflag:

Cheerz

SilverSatori

---

### Post by maggotbrain on 2007-01-21
Hello,

You are correct, your ESSID needs to match on both the wireless router and your wireless NIC on your computer 
Judging from your post, I would assume that you have access to your wireless router, yes?

If so, make a note of its config (ESSID, channel, frequency,etc). For a single user/home network, I generally find it more convenient  to configure your router to match the wireless NIC defaults settings, if possible.
For example, your NIC is trying to connect on channel 1.Make sure your router is set up for channel 1 as well.

Hope this help you.

---

### Post by SilverSatori on 2007-01-21
Actually, thinking about it, no, I cannot even get access to my routher via wireless.  Sorry I should have mentioned that initially.

I can get the wireless diod to light up on the laptop, but I cannot get onto the router set up page via wireless.

Suppose I should get round this bit first, a!?:rolleyes: :-\"

---

### Post by maggotbrain on 2007-01-21
Sorry for not being clear. I was actually just suggesting you access the router from a wired link so as to get all of the configuration details set up to match your wireless NIC, and hopefully tweaking it until the card connected.

such as:
step 1- config router via wired conn.
step 2- turn down wired connection/turn up wirelless
step 3- ????
step4 - profit/connect

---

### Post by SilverSatori on 2007-01-21
Right...

I've gone into my router set up whilst wired, and it now has an ssid name of test, then broadcasting on channel 1 .... I don't have any security set up yet (wep or wpa etc) as I want to get it working first ..... now the router channel matches the iwconfig channel, however, the essid name is still blank when I run iwconfig.... 

So what am I not doing correctly?? ... all the essid says in iwconfig says is " " .... eh??

As a side note, when I go into system network wireless, enable it and put in the essid name of test ... I am still leaving the password field blank as I do not use a password .... I presume this would be the wep or wpa code if and when I set that bit up??

Sorry for being a right n00b :confused: :( 

Silver Satori

---

