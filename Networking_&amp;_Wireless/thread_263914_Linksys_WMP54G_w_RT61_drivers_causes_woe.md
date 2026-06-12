---
title: "Linksys WMP54G w/ RT61 drivers causes woe"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by JebusWankel on 2006-09-23
This card was originally not recognized in my computer. It worked from the live cd so I reinstalled and it would work once I activated it. Then I rebooted and the computer hung at configuring network interfaces. I did a ctrl+c and it skipped that. Then I could log in but it wouldn't even start x. I reinstalled and have avoided the card. Tonight I decided to take a crack at it again. I followed this: [https://help.ubuntu.com/community/Rt61WirelessCardsHowTo?highlight=%28RT61%29](https://help.ubuntu.com/community/Rt61WirelessCardsHowTo?highlight=%28RT61%29)
	
I got to the part where I have to read the readme and configure the file rt61sta.dat. I couldn't find anything to change because currently my home network is unsecured. I then continued to follow the guide.
Then here's what conspired:
> eric@eric-desktop:~$ depmod
FATAL: Could not open /lib/modules/2.6.15-27-386/modules.dep.temp for writing: Permission denied
eric@eric-desktop:~$ sudo depmod
Password:
eric@eric-desktop:~$ modprobe rt61
eric@eric-desktop:~$ dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
eric@eric-desktop:~$

	Previously I tried to activate the card and the computer beeped to death. It completely froze emitted a constant beep (I had been playing music). I tried again and it seemed ok. Now it just plain doesn't work. It doesn't connect but it doesn't cause other problems. If you can help me with either compiling this driver or if you can tell we how to undo what I've done and fix the original problem that would be awesome too. Thanx.

---

### Post by wieman01 on 2006-09-23
Could it be as simple as that?
> [COLOR="Red"]sudo[/COLOR] modprobe rt61
[COLOR="Red"]sudo[/COLOR] dhclient

---

### Post by JebusWankel on 2006-09-23
I'm afraid not. No change. Thanx for the quick reply though.

---

### Post by blx_286 on 2006-09-23
> **JebusWankel said:**
> This card was originally not recognized in my computer. It worked from the live cd so I reinstalled and it would work once I activated it. Then I rebooted and the computer hung at configuring network interfaces. I did a ctrl+c and it skipped that. Then I could log in but it wouldn't even start x. I reinstalled and have avoided the card. Tonight I decided to take a crack at it again. I followed this: [https://help.ubuntu.com/community/Rt61WirelessCardsHowTo?highlight=%28RT61%29](https://help.ubuntu.com/community/Rt61WirelessCardsHowTo?highlight=%28RT61%29)
	
I got to the part where I have to read the readme and configure the file rt61sta.dat. I couldn't find anything to change because currently my home network is unsecured. I then continued to follow the guide.
Then here's what conspired:

	Previously I tried to activate the card and the computer beeped to death. It completely froze emitted a constant beep (I had been playing music). I tried again and it seemed ok. Now it just plain doesn't work. It doesn't connect but it doesn't cause other problems. If you can help me with either compiling this driver or if you can tell we how to undo what I've done and fix the original problem that would be awesome too. Thanx.

Looks like a few of us are having probs with this one [http://ubuntuforums.org/showthread.php?t=263844](http://ubuntuforums.org/showthread.php?t=263844)

I found this by googling, but haven't got too far into it yet [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

There was this too [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

---

### Post by JebusWankel on 2006-09-25
Problem solved. Thanks so much to lupine_nickt for the repository and thread. You Rock! [http://ubuntuforums.org/showthread.php?t=240669](http://ubuntuforums.org/showthread.php?t=240669)

---

### Post by DapperMe17 on 2006-11-24
I too, have this Linksys WMP54g V4 pci card. RT61

Like you, it isn't even recognized as hardware via lspci. It's not recognized using LiveCD, or fresh installing Dapper 6.06. No lights, no nothing:( 

Will any driver out there help this card to be recognized as hardware?

---

