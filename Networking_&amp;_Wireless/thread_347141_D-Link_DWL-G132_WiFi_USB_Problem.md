---
title: "D-Link DWL-G132 WiFi USB Problem"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by deat on 2007-01-26
I have searched the forum for any help regarding the D-Link DWL-G132, and all I found that was any help was:
[http://ubuntuforums.org/showthread.php?p=1993115](http://ubuntuforums.org/showthread.php?p=1993115)

Though it still didn't quite assist me in solving my problem.

My question is what should I do to install this on Ubuntu 6.10? I'm quite inexperienced with Ubuntu, so I'd ask that if you do help me, that you'd provide step-by-step instructions.

Regards,
Zach

---

### Post by deat on 2007-01-27
Anyone?

---

### Post by tturrisi on 2007-01-28
The dwl-g132 usb has an Atheros chipset which uses thye madwifi driver in linux, and is well supported.  Unfortunately, madwifi does NOT work with usb, it only works with pci or pcmcia Ahheros devices.  Thus to use your adapter in linux you will need to use the Windows drivers for the device along with ndis-wrapper.  Search the forums for howtos re ndiswrapper.

---

### Post by trenog on 2007-01-31
I am also interested in this solution as it would save me money and time/aggrevation when it comes to my installation of Dapper that will likely happen in the next few days.

---

### Post by OldGaf on 2007-01-31
Hey,

I just got a few to work a few weeks ago. Follow the steps from my dell post and substitute the latest dlink drivers for the dell ones.... works fine for me.

[http://www.ubuntuforums.org/showthread.php?t=342558](http://www.ubuntuforums.org/showthread.php?t=342558)

I am on my pocket pc now so it is not so easy for me to help. If you need more details I will check in again in a day or so.

---

### Post by OldGaf on 2007-02-01
Here is my DWL-G132 link. I have two working in Kubuntu Edgy now.

[http://cooldragonscomputing.com/smf/index.php?topic=32.msg47#msg47](http://cooldragonscomputing.com/smf/index.php?topic=32.msg47#msg47)

-OG-

---

