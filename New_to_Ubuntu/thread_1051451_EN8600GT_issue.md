---
title: "EN8600GT issue"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by fleton on 2009-01-26
Hello, first time posting on forums but I have used it before with great success but right now I am unable to find a solution to a issue of mine. I just got two new ASUS EN8600GT Silents (SLIing them) and took out my old card which was a nvidia 8600GT and upon booting my system it seems go good until it got to the login screen and it loaded into a CLI login screen. Believing it was a driver error (just to make things hopefully simple) I just decided to reinstall ubuntu 8.10 because I had everything backed up and was just going to start off fresh and the live CD worked great so I installed ubuntu and and it booted fine, then I downloaded all updates and the newest drivers for my video card. restarted computer and am now having the same issue. Here is the current screen I'm looking at (I have no issues logging in but whats the point of two nice video cards without a GUI?)

```
Boot from (hd0, 0) ext3    83199329-115a-4fc9-bb4b-4928b04ed3de
starting up ...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t (/dev/disk/by_uuid/b836def2-ba6d-45c1-5df608fd4c7e) = d ev(8,5)
kinit: trying to resume from /dev.disk/by-uuid/b8e6def2-ba6d-45c1ba6d-45c1-5df608fd4c7e
knitit: No resume image, doing normal boot...

Ubuntu 8.10 Fleton-Desktop tty1

Fleton-Desktop login:
```

Any help would be great :D

Currently i'm going to try a older driver for it and see if it works, ill post my results later

Edit: older driver still creates the same error and so does using a KDE environment, please any help would be great.

Edit2: By removing one of the video cards it booted up fine, so now the issue is getting SLI to work, any ideas?

Edit3: Solved using the guide by dagrump :D

---

