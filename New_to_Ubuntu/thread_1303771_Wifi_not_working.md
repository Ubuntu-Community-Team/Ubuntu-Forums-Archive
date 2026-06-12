---
title: "Wifi not working"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by McDarling on 2009-10-28
So I just installed 9.04 on an old HP Pavilion ze4400 that previously had XP on it. Now it can only connect to the internet through a wired connection. When it had XP, the wireless was fine, so I don't think it's a hardware issue. Also, the wifi indicator light is on. The issue is that no wireless networks can be found. What can I do?

---

### Post by jualin on 2009-10-28
You should start by going to the terminal and typing > lspci and post the results on the forums so we can identify your wireless card.

---

### Post by bribera on 2009-10-28
It would also be helpful to know the specifics of the network to which you're attempting to connect.

Is it encrypted? More importantly, is the SSID hidden?

---

### Post by McDarling on 2009-10-28
Sorry about that. Thanks for the quick replies.
Here's my output from lspci

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

I'm trying to connect to a unencrypted network that is not hidden, but it does have a password. I can't find any networks though.

---

### Post by anewguy on 2009-10-28
You need a driver installed for your wireless (the BCM4306) to work.  There is a restricted driver that is supposed to work, but I've never had a need to use it.  Check under system/administration/hardware drivers (I *think* that's it - I'm on KDE right now or I'd know for sure) to see if there is a driver listed there you can enable.

We can also install the Windows drivers if you have them (the .inf and .sys files are needed).  If you have a CD for the adapter or can download the driver we can do that easily as well.

Some say one way is better than the other, but the truth is they are both about equal in terms of supporting your wireless.  If a restricted driver is all that is needed, it can be faster to install that way, but even installing the Windows drivers is easy and quick.

Let us know what you'd like to try.

Dave :)

---

### Post by anewguy on 2009-10-28
Found this, it should make it easy for you:

[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/]("http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/")

Dave :)

---

### Post by McDarling on 2009-10-28
Fantastic! It's working perfectly. The driver was right there System/Admin/Hardware Drivers. Thank you everyone!

---

### Post by anewguy on 2009-10-28
Your welcome!

Dave :)

---

