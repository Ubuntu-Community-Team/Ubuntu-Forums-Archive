---
title: "Intel 4965 AGN does not show anywhere"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by esbendamm on 2007-09-18
Hi,

I have this WIFI nic "Intel 4965 AGN" and I can't seem to find it anywhere in Ubuntu. When I click on my "Network" settings I can only see Wired connnection (the one I am using now) and Modem connection. Any suggestions to that, other than having to convert to Gutsy kernel (as I read in another post could be a solution to WIFI issues)

Thanks

---

### Post by noob12 on 2007-09-18
That card isn't directly supported in Feisty.  The Gutsy suggestion is because there is a driver (still at development stage) that is included in Gutsy, and I've seen some users report success with it.  The solution for Feisty is either to build iwlwifi drivers yourself or to install ndiswrapper + the windows driver. 

Here are pointers to threads for these but they aren't ones I've tried myself (as I don't have that card).


For iwlwifi-based approach:
[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

For ndiswrapper-based approach:
[http://ubuntuforums.org/showthread.php?t=471794](http://ubuntuforums.org/showthread.php?t=471794)

---

