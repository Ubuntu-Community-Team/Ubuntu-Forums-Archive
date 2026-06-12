---
title: "Dual boot Ubuntu Mandriva"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by anchorschmidt on 2009-04-11
I am running Ubuntu Intrepid and want to dual boot ubuntu and Mandriva. However, when I insert the Ubuntu live disk and boot up my sytem and enter gparted, I am unable to resize the partition.

---

### Post by Kosimo on 2009-04-11
> **anchorschmidt said:**
> I am running Ubuntu Intrepid and want to dual boot ubuntu and Mandriva. However, when I insert the Ubuntu live disk and boot up my sytem and enter gparted, I am unable to resize the partition.


What is the system saying when you try to resize your partition?

---

### Post by anchorschmidt on 2009-04-11
Nothing, the option is greyed out. I can't even select it.

---

### Post by sayems on 2009-04-11
which partition are you trying to resize?

---

### Post by RetchingRabbit on 2009-04-11
Note that any partition must be unmounted when performing partitioning operations. This may require the use of a live cd.

---

### Post by Twitch6000 on 2009-04-11
download the gparted live cd to do that kind of partitioning.

Link here - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by anchorschmidt on 2009-04-11
Trying that: Thanks

---

### Post by anchorschmidt on 2009-04-11
I don't know what happened. I downloaded the .iso file, burned it as an image to a disk using braesero, and restarted the computer with the disk inside the drive but it still didn't work. Ubuntu just boots up.

---

### Post by anchorschmidt on 2009-04-11
The partition that I'm trying to resize is an ext3 partition

---

### Post by zvacet on 2009-04-12
And in BIOS you choose to boot from CD?

---

### Post by anchorschmidt on 2009-04-12
No :), how do you do that?

---

### Post by anchorschmidt on 2009-04-12
Bump, Anyone?

---

### Post by sschnee on 2009-04-12
Usually during the boot up process you will see something like "press F2 for setup" or "press F10 for Options" or something like that.  Hit the button it tells you to.  This will allow you to change your BIOS settings.

I don't exactly what your settings will look like, but most are self explanatory.  Look for the part of the BIOS settings where it asks you where to look for booting.

Set it to look at your CD drive before your hard drive.  This will make your computer boot from a live CD rather than your OS on your HD.

---

### Post by anchorschmidt on 2009-04-15
Hey, I tried that and I had to enable the menu first but it worked :). THanks a lot!!!!

---

