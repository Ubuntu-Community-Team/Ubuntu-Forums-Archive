---
title: "problem connecting to network"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by Dark Link on 2007-06-12
hi, 

ive got my computer booting into vista and ubuntu  everything works fine on vista but on ubuntu most of the time i can't connect to my network. My network adapter is made is a netgear WG111v2 but on vista it uses a realtek RTL8187 Wireless 802.11g 54mbps USB 2.0 Network adapter, driver. 

please help.

---

### Post by ugm6hr on 2007-06-12
I don't have that USB wifi device, but this might be useful (from [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/) )

Card: NetGear, Inc. WG111 WiFi (v2)
Chipset: RTL8187
usbid: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
encryption: using WEP- 128bit
Driver: 04/04/2006,5.1221.0412.2006 (copied from netrtuw.inf); Realtek drivers v1221. (these are no longer on the realtek website google them); filename: rtlsetup-8187(1221)(0412).zip WIN98 folder; url: [http://www.majorgeeks.com](http://www.majorgeeks.com) (this is where I got it)
Other: The XP drivers did not work in this package, but the WIN98 ones did. In my experience, any driver for this adapter will load fine in ndiswrapper, but so far this is the only one that I got to find my AP. Other drivers even detected other AP’s, but not mine (which was closer than the detected ones). I also could not set the ESSID with other drivers. This one has neither of those problems.

If you type *lsusb* in Terminal - it should confirm the RTL8187 chipset (look for Network Controller).

And this suggests that ndiswrapper should manage to get it to work with the Win98 drivers.  Whether it will or not, I don't know.

---

### Post by Dark Link on 2007-06-17
I can't install ndiswrapper because:

1. The folder that it needs hast got the .config file in it
2. To install it I need to be connected to the internet and I get my internet through my wireless network.

Also it my wireless adapter worked before but it just stopped working for some reason

---

### Post by panurge77 on 2007-06-27
I still dont get it why ndiswrapper is not included in default install. There are tons of people with this problem every install...

---

### Post by ugm6hr on 2007-06-28
> **Dark Link said:**
> I can't install ndiswrapper because:

1. The folder that it needs hast got the .config file in it
2. To install it I need to be connected to the internet and I get my internet through my wireless network.

1.  Don't understand this point
2. You can install it if you download from within Windows - either from Ubuntu packages website or direct from ndiswrapper website and then compile - and then install on Ubuntu.

If you want it from repos - follow this:
[http://ubuntuforums.org/showthread.php?t=476735&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=476735&highlight=ndiswrapper)

As for why it had been working before - as I said, this may or may not work.

---

