---
title: "Duplicate sources.list entry"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by TheTeamFromMars on 2011-02-05
Anyone know how I can stop this error from appearing every time I do an update? 

"W: Duplicate sources.list entry [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Packages 
(/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_main_binary-amd64_Packages"

I checked in /var/lib/apt/lists/ but there don't seem to be any duplicates...

This is what I found in there...

-rw-r--r-- 1 root root      828 2011-01-09 13:56 ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_main_binary-amd64_Packages
-rw-r--r-- 1 root root    13951 2011-01-09 13:56 ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_Release
-rw-r--r-- 1 root root      316 2011-01-09 13:56 ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_Release.gpg

****

I'd really appreciate if someone knows how to fix this - thanks!

---

### Post by DiSTORT3D on 2011-02-05
it says sources.list

located at /etc/apt/sources.list

---

### Post by TheTeamFromMars on 2011-02-05
Thanks but I looked in /etc/apt/sources.list and couldn't see any duplicates there either.

---

### Post by cwsnyder on 2011-02-05
Try removing your tulatrix source PPA entry from the Sources List GUI, log out and log back in, then re-enabling the PPA.

---

### Post by TheTeamFromMars on 2011-02-09
Thanks cwsnyder! 
I was able to remove the duplicate entry using Ubuntu Tweak's package cleaner. Looks like that has sorted the problem. Thanks for your help.

---

