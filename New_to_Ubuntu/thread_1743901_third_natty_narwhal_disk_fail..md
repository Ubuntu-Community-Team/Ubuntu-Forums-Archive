---
title: "third natty narwhal disk fail."
date: 2011-04-29
forum: New to Ubuntu
---

### Post by gammaxana on 2011-04-29
hey guys natty narwhal wont install and ive gone through 3 disks for 11.04 

assistance is apretiated 


gamma

---

### Post by aaron76 on 2011-04-29
Well, I had the same trouble trying to update, but my cd worked fine. I downloaded it from isohunt. Did you try burning it on a lower speed?

---

### Post by ankspo71 on 2011-04-29
Hi,
In addition to what the above poster said...
Does the live cd start?  Does the installer get stuck or crash?

Have you checked the md5sum of the ISO image? You can check the md5sum by opening your terminal and doing:
```
md5sum /path/to/ubuntu-11.04-desktop-i386.iso
```

It will take about 30 seconds for the command to generate the number. When you see the number, compare it to the md5sum number found on one of the Ubuntu mirror download locations.
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/11.04/MD5SUMS](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/11.04/MD5SUMS)

If it doesn't match the number then you have a bad ISO and will need to download it again.

Also, I think Ubuntu 11.04 still has the "Check this cd for defects" option in the boot menu of the live cd. Try booting into the live cd, but instead choose that option to see if the image was burned successfully to the cd.

Hope this helps.

*Edited* because [http://cdimage.ubuntu.com/releases/11.04/release/MD5SUMS](http://cdimage.ubuntu.com/releases/11.04/release/MD5SUMS) didn't show all of the usual md5sums.

---

### Post by gammaxana on 2011-04-30
well now it boots into demo now. but it wouldent see my hdd. but now i configured it good. and now it  takesforever forthe live cd to load..  and wifi is not working ether. cant do any treminal stuff because my linux  hdd got erased  so im trying to put narwhal on it.

---

### Post by cap10Ibraim on 2011-04-30
did you burn the iso at low speed ?
plus I used to have problem with cds , I recommend using a usb instead

---

### Post by user333 on 2011-04-30
You might need to re-download. Sometimes the ISO get corrupted. Or, you can wait until they sell CDs and order one.

---

### Post by gammaxana on 2011-04-30
checked and no disk errors but installing there was on but it rebooted. also my trouble is with an AE1000 wifi driver..

---

### Post by gammaxana on 2011-05-01
now the disk has errors. im thinking i should try the usb way. what do you think?

---

