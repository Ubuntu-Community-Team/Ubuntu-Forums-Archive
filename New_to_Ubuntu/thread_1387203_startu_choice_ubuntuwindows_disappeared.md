---
title: "startu choice ubuntu/windows disappeared"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by mlotfi on 2010-01-21
Hi,

I have Ubuntu and windows XP installed in my PC, a problem happened in Windows XP, so I have to reinstall windows XP, now when I turn on my PC it goes directly to Windows XP, how to have that first page that give you the choices of starting ubuntu or windows ?

thanks

---

### Post by stevanbt on 2010-01-21
Hi,
The problem is that when you re-installed windows it has overwritten the Master Boot Record (MBR).  Windows doesn't check for any other operating systems when it installs.  You will have to re-install GRUB to get your previous boot menu to appear.

You can re-install GRUB via the Live CD without affecting either your windows or ubuntu installs.

Thanks, Steve.

---

### Post by mlotfi on 2010-01-21
what is GRUB ?
how to install it from the CD ?

thanks lot

---

### Post by Merk42 on 2010-01-21
Which version of Ubuntu were you running?
There was a major change to GRUB as of 9.10

---

### Post by mlotfi on 2010-04-12
How to install GRUB from ubuntu 9.10 ?

thanks

---

### Post by IndyGunFreak on 2010-04-12
This was written for Ubuntu 7.04, but it should work for 9.10 as well...

[http://thelinuxsociety.org.uk/content/reinstall-grub-using-live-cd](http://thelinuxsociety.org.uk/content/reinstall-grub-using-live-cd)

---

### Post by e4uforums on 2010-04-12
[http://ubuntuforums.org/showthread.php?t=1327197](http://ubuntuforums.org/showthread.php?t=1327197)

There are a few links in this thread that will get you going.

---

### Post by mlotfi on 2010-04-12
I did the grub instatllation, now when rebooting ubuntu start and no windows 7.

---

### Post by IndyGunFreak on 2010-04-12
Are you getting a grub menu at all?  Watch your screen during boot up, do you see "Hit esc for grub menu" or something like that, and a countdown?

IGF

---

### Post by Merk42 on 2010-04-12
When in Ubuntu try opening up a terminal (Applications > Accessories > Terminal) and run the following command
```
 sudo update-grub
```

---

