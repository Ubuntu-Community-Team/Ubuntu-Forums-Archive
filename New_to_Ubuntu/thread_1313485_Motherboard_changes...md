---
title: "Motherboard changes.."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-11-03
Hi all,
My laptop recently started going crazy, and after a warranty repair, I found out they put a new motherboard in. Windows wanted reactivating, and Ubuntu tried to do some disk scanning, which failed continually. I turned it on today, and it didn't try to scan, but after login screen, just had black with a moveable mouse. Anyone know how to rectify?
Also, if anyone knows about this, using windows 7, only some websites work using this current business network. At home, all connections are fine. Does anyone know if there is a quick fix to allow all sites to work? Google always works, and so does ubuntuforums ;P
Thanks for considering,
Robin

P.S. Laptop is presario v3000.

---

### Post by jasonab on 2009-11-04
I swapped the motherboard of my desktop and had the same problem with ubuntu. After the fourth reset, Ubuntu booted fine. So keep trying.

With regard to the websites. Try visiting the sites with an alternative browser. More information (like the error message the browser reports when you unsuccessfully visit the site on your business network) would be helpful.

---

### Post by anewguy on 2009-11-04
It may have lost the video driver, or perhaps the video driver that was installed doesn't work with the replacement motherboard.  Post the output of

lspci

and 

lsusb


Also, double-check under system/administration/hardware drivers and be sure to look to see if there is a restricted driver there and if it is activated.

Dave :)

---

### Post by kansasnoob on 2009-11-04
I would choose Recovery Mode from the grub menu and when it's done running you'll get a list of options. It varies by version, but in Karmic:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

Choose xfix or the equivalent. It will attempt to reconfigure the graphics.

---

