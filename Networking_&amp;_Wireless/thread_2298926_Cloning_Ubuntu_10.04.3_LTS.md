---
title: "Cloning Ubuntu 10.04.3 LTS"
date: 2015-10-14
forum: Networking &amp; Wireless
---

### Post by Craig_Patno on 2015-10-14
Edit: sorry I missed typed and I don't know how to edit the title, the version I am working with is 14.04.3 LTS, not 10.04.3. 

I am trying to clone Ubuntu 14.04.3 LTS on to new hardware and I am having trouble with the network. I have done this many times in the past on older versions and one of the first things I did after cloning the machine onto new hardware was to delete the file 70-persistent-net.rules. I have read that file no longer exists in the new version of Ubuntu but what I cannot find is how to delete the reference to the old MAC address (if that is even my problem). Googling "clone Ubuntu" will show many results that instruct you to delete or edit that file but I cannot find anything on how to handle this on the new version. Right now in /etc/udev/rules.d there is nothing there except a README file. Can someone advise me on how to clone Ubuntu to new hardware and not have the old MAC address references be an issue (again if that is even the problem here).

For reference all of my interfaces show up when I do an ifconfig. I have 4 network cards that are bonded. I have no network connectivity though. This is exactly what would happen in the older versions of Ubuntu and once I deleted that file network service would be restored. 

Thanks,
Craig

---

### Post by TheFu on 2015-10-14
Welcome to the forums.

[http://ubuntuforums.org/showthread.php?t=2276236](http://ubuntuforums.org/showthread.php?t=2276236) and
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) and
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Sorry cannot help more. It has been 3+ yrs since I migrated any 2010 systems.  Last spring, I did upgrade one from 10.04 to 12.04 to 14.04, which was a nightmare and took weeks of testing, reading mainly due to the software package it ran, not something Ubuntu related. Plus putting off the upgrade didn't really save me time overall.

---

