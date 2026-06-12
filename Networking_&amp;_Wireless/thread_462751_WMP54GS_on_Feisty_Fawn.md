---
title: "WMP54GS on Feisty Fawn"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by dksaun on 2007-06-03
I just recently set up my Vista computer to dual boot with Ubuntu Feisty Fawn, and I'm having trouble getting my wireless adapter to work. I'm running a Linksys Wireless-G PCI Adapter with Speedbooster  (Model#: WMP54GS). I tried following the instructions given here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), but to no avail. I got all the way down to "2.5.2.2. Checking to make sure the driver was installed correctly" where it directs me to run "ndiswrapper -l" in Terminal. Terminal reports that the driver is present, but does not report that the hardware is. This is confirmed by checking in "ipconfig" and "iwconfig" where my adapter doesn't even show up. Also, my PCI ID shows up as "14e4:4318", though that doesn't match up with my actual device on the ndiswrapper wireless card list (here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/")

Basically, I'd like to know what I'm doing wrong and how I can fix it. Sorry, by the way, for rambling a bit: I'm very new to this and didn't know how much, and which, information would be needed to solve my problem.

Thanks in advance,
Dan.

---

