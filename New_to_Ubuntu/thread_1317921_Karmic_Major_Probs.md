---
title: "Karmic Major Probs"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Howie Williams on 2009-11-07
Major major probs with Karmic. Updated from Jaunty then resolution was all to cock. Booted up this a.m. and resoloution and options are now O.K. but now have other problems. Can't go to sytem > Apps > any option without the PC closing down and bringing up the login page. Also try to listen to imbeded music player in web sites and Firefox shuts down.HELP!!!!

---

### Post by Berean on 2009-11-07
Might I suggest that you do a fresh install?  It might be better to start at a clean installation than correct an installation that's corrupted.  Regards.

---

### Post by Howie Williams on 2009-11-07
How does one do that? Will I lose any files music photos etc.

---

### Post by Darce on 2009-11-07
Unless you back it up, you will lose it all ! Best option would have been to back it up BEFORE attempting the upgrade. If you have a live CD, boot from that, navigate to your home directory, and copy any files you want to a usb stick/network drive/another partition, not forgetting browser bookmarks and emails.

Cheers,

Tim

---

### Post by Berean on 2009-11-07
Yes, as previously mentioned, copy your files then download Ubuntu 9.10.  Burn it to a CD (preferably CD-R) and checksum before and check for defects after.  Then put it into the CD drive and press ctrl, alt, and del together and the system will reboot.  Ubuntu should load into RAM and then you can install it where it suggests.  If you're unsure of anything ask away: we'll try to help.

---

### Post by Shazaam on 2009-11-07
Try this in terminal before doing anything...
```
sudo dpkg --configure -a
```
or...
```
sudo apt-get install -f
```
If you get any error messages post them here.

---

