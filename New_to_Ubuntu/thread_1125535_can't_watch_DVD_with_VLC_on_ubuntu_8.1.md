---
title: "can't watch DVD with VLC on ubuntu 8.1"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by ralph2 on 2009-04-14
VLC doesn't work on ubuntu 8.1, downloaded codec pack but no chance..
I want to watch DVD's, doesn't work on movie player too.

heeeelp me please:guitar:

---

### Post by SunnyRabbiera on 2009-04-14
are you sure you installed libdvdcss?
Most commercial DVD's wont work without it.

---

### Post by steve101101 on 2009-04-14
do you have libdvdcss2 package

---

### Post by steve101101 on 2009-04-14
man you just beat me 2 the punch.

---

### Post by djbushido on 2009-04-14
The dvdcss2 package doesn't actually install libdvdcss. Try looking for and running this script: "sudo /usr/share/doc/libdvdread3/install-css.sh" - This is part of libdvdread3. Post back if this works.

---

### Post by LowSky on 2009-04-14
here you go open a terminal and copy and past each line at a time, then reboot, dvd should play, note use 386 or AMD 64 depending on your install

**i386: **
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

```
**amd64: **
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

---

### Post by Redbomber on 2009-04-18
Just a note to say, I had same prob, and this fixed my issue.  Thanks guys.

---

### Post by techdude3177 on 2009-05-01
> **djbushido said:**
> The dvdcss2 package doesn't actually install libdvdcss. Try looking for and running this script: "sudo /usr/share/doc/libdvdread3/install-css.sh" - This is part of libdvdread3. Post back if this works.

This worked out great for me... was able to play the DVD in VLC not in totem though but whatever didnt use it much anyways!:popcorn:

---

