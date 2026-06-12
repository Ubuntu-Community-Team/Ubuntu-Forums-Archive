---
title: "Broadcom 43225"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by paramax552 on 2013-12-08
I upgraded from 12.04 to 13.04 and my Broadcom 43225 wireless stopped working. The same thing happened when I upgraded from 11.something to 12.04 and I found a post (after hours of searching) that fised it. Now (many months later) I can't find that old post. I've tried about a gazillion things that involve installing linux headers and installing/uninstalling the driver, rebooting, trying the legacy driver, etc. and I can't get it to work. I can't remember exactly all of the things that I've done so far, so I think it's best to start with all of the reports that will show what the system is unhappy about. I don't know what those commands are so I would like if someone will direct me as to how to start.

---

### Post by praseodym on 2013-12-08
Try the native driver:
```

sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
```
Reboot. Error messages are ok in the last 6 lines

---

### Post by paramax552 on 2013-12-08
Holy poopoo, Batman! It worked! I had already installed the linux-firmware-nonfree and nothing was blacklisted, so all I needed to do was purge the bcmwl-kernel-source! Hours and hours later and that's all I needed! Thanks!

---

