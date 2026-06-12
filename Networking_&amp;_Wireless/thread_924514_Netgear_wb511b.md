---
title: "Netgear wb511b"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by lightfoot9 on 2008-09-19
I followed the instructions in WifiDocsDriverNdiswrapper and used the Netgear wn511b.inf/sys files 
from a Windows installation.


Before selecting the network to be connected with, ifconfig gives:

wlan0:	link encap:Ethernet  HWaddr 00:14:6c:f3:e5:2a
	UP BROADCAST MULTICAST MTU:1500 Metric:1
	RX packets :0 errors:0 dropped:0 overuns:0 frame:0
	TX packets:0 errors:0 dropped:0 overuns:0 carrier:0
	collisions:0 txquelen:1000
	RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
	interrupt:10 Memory:2c000000-2c004000

After selection, the network symbol rotates (Attempting to join the wireless network 'mynetwork'....). 
After a short time, it stops rotating and everything locks up - Terminal won't come up, & can't shut down 
without turning the power off.


______________

Running lspci the Netgear wn511b card was identified as using Broadcom BCM43XG chip set.
I used the ubuntu "How to: Broadcom Wireless cards" in the ubuntuforums to load the Broadcom
files. These load bcm43xx-fwcutter. The problem is that the blacklist prevents this from loading and
that it was "replaced by b43 and ssb".

What do I use and how do I load it?

---

### Post by bingobingo on 2009-02-02
I do not think you need ndiwrapper there is a driver that I have not tried, yet, but about to buy the card, $11 @ ecast....

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by rderoko on 2009-02-27
Yes, I got the WN511B working with the new Broadcom STA Wireless driver.

I noticed that, after it was activated in the Hardware drivers list, my /etc/modprobe.d/blacklist file showed that the bcm43xx, b43, b43-legacy and the ssb drivers were all blacklisted.

lspci output:
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
02:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)


[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by rderoko on 2009-02-27
Sorry, I forgot to include the fact that I am using Intrepid.

---

