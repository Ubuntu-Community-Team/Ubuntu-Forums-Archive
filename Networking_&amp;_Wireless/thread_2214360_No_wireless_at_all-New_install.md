---
title: "No wireless at all-New install"
date: 2014-03-31
forum: Networking &amp; Wireless
---

### Post by rich15 on 2014-03-31
Rather than go through 4000 posts, I just installed Ubuntu on a older notebook, a HPdv5000, about 7 years old. The Ubuntu install is good but I can't get the wireless to even show up in the network box, even though built in wireless works with the Win XP I left installed. Anything I'm missing here? Has anyone had the same issue? Is there a solution to this problem and if so what steps do I need to do to get wireless to work? Any help will be appreciated as I really like Ubuntu. Thanks.

---

### Post by Hadaka on 2014-03-31
hi open a terminal ctrl/alt/t and while connected
to the internet with a cable please do..
```
sudo apt-get update
sudo apt-get upgrqade
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```

---

