---
title: "Wireless Networking Belkin router Fujitsu-Siemens Laptop"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by nor02744 on 2007-12-13
I have struggled a while and can not connect wireless to the network. In the terminal window a have submitted the following commands:
sudo ifconfig eth1 down

sudo dhclient -r eth1

There is already a pid file /var/run/dhclient.pid with pid 5815

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth1/00:0c:f1:3d:08:bc

Sending on   LPF/eth1/00:0c:f1:3d:08:bc

Sending on   Socket/fallback

sudo ifconfig eth1 up

sudo iwconfig eth1 essid <"Name">

sudo iwconfig eth1 key <HEX_KEY>
sudo iwconfig eth1 mode Managed

sudo dhclient eth1


And I got the following response:

There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0c:f1:3d:08:bc
Sending on   LPF/eth1/00:0c:f1:3d:08:bc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

My question: Is this releated to the router?? I have tried all settings in the router, both WEP  and no WEP, updated firmware but nothing seems to solve the problem. I use i Fujitsu-Siemens LapTop E4010 with the PRO/Wireless LAN 2100 3B Mini PCI Adapter.
The router is a Belkin Wireless G Router. Before I changed from Windows XP to ubuntu it was ok. 
Does anyone have an idea of what the creates the problem?:confused:

---

### Post by nor02744 on 2007-12-14
I just tested another Fujitsu Siemens Laptop running Windows XP over a VPN connection, and that computer connect wireless without any problems. As I am a novice on Linux I really need some ideas to get up and running wireless.

---

### Post by ugm6hr on 2007-12-14
I am no networking expert in Linux, but it sounds like you have an Intel2100 wifi card, and want to connect to a wifi router.

You should not need to use any Terminal commands (in theory).

Before continuing - confirm the following outputs:
```
lspci
lshw -C network
```

These will tell you what hardware chipset the wifi uses, and also which driver Ubuntu has loaded.

If you post the output from those commands, someone will hopefully be a ble to point you in the right direction.

This page suggests ndiswrapper might work (if the default Linux drivers don't): [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

Previous experience (in Puppy Linux) suggests that sometimes the ipw2200 and ipw2100 drivers are confused with each other - so "blacklisting" ipw2200 might resolve the issue (if that is the problem).

---

### Post by nor02744 on 2007-12-17
The command replied with:
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 20)
01:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 20)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0d.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

I am still confused.:confused:

---

### Post by ugm6hr on 2007-12-17
> 01:0d.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

This just confirms your hardware - Intel 2100 3B (as you had said).

What about?
```
lshw -C network
```

This will confirm which driver is currently being used.

---

### Post by nor02744 on 2007-12-17
It looks like the driver is:
 driver=ipw2100 driverversion=git-1.2.2

But I am still confused:confused:

---

### Post by ugm6hr on 2007-12-17
Sorry you are confused.

It looks like the wifi card has been correctly installed with the appropriate driver.  This should just work without any interference.

Do you have a Network Manager icon in the top right corner?  Are you on Gutsy / Ubuntu7.10?

If so, just left-click on the NM icon (often looks like 2 computer screens or 4 small grey bars and see what happens.  Or right-click.

It should give you options to connect wirelessly.

---

### Post by nor02744 on 2007-12-18
Yes I do use Ubuntu 7.10
Yes I have a network manager (the two screens)
And I have configured the wireless network with DHCP and WEP code.

The nm-applet seems to be of ver. 0.6.5. I expect this to be the right version even if it is copyright to RedHat and novell
:confused:

---

### Post by ugm6hr on 2007-12-18
What do you see when you click on the NM-Applet icon?

It should look like the screenshot - but there should be a list of wifi networks below where it says "Wireless Networks" - unfortunately I don't have any in range at the moment.

When you click on your network, it should give you the option to enter the WEP code.

The only other thing is - do you "hide" your SSID?  If so - don't bother (there are plenty of reports about how pointless that is anyway).

---

### Post by nor02744 on 2007-12-18
I have enabled essid, I mean I can see it and a lot of others in the area.

---

### Post by precisedjs on 2007-12-18
I would just completely stay away from belkin, go with a linksys

---

### Post by ugm6hr on 2007-12-18
> **nor02744 said:**
> I have enabled essid, I mean I can see it and a lot of others in the area.

And what happens if you click on your network in the drop-down list?

---

### Post by nor02744 on 2007-12-19
The router sends OFFER to the IP address assigned to the wireless card, but it never sends  ACK to the card. I think it is because the wireless card do not reply to the router's OFFER.. Compared with the wired connection, the router always replies the OFFER with an ACK to that particular IP address.

When I send the commands to the router from the terminal:
sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "xxx"
sudo iwconfig eth1 key yyyy
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

I receives the response:
.....
[B]No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/B]
.......
:confused:

---

