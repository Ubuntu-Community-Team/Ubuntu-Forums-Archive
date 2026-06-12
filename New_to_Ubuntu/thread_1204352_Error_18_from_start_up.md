---
title: "Error 18 from start up"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by berentorin on 2009-07-04
I have a laptop and have been running ubuntu 8.4 with duel boot winXP no problem.
Until I decided to up grade to 9.04. I used (sudo update –manager  -d)  and sat back to enjoy the thoughts of my upgrade . When the time came to accept the upgrade I noticed the upgrade is for 9.10 well I was like a kid in a toy shop.:p

Two hours later the time came to boot the laptop  --- then that’s when the error came up - ERROR 18.
Now I am grumpy. I can’t use win xp for work on Monday. 
I have now loaded 9.04 but still getting the ERROR 18 and it just hangs.:mad:
I have had a look at what’s on offer in the way of a fix, but they all seem to be written in a way that’s above my head. I am able to use terminal but I don’t know what a kernel is so my knowledge has limits.
Is there any one that can tell me in plane terms what I can do to fix this?.

---

### Post by presence1960 on 2009-07-04
here is what error 18 means from the GRUB manual : 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

Usually the fix is to create a separate /boot partition within the specified area on your disk. But what I am not so sure about is you did an upgrade and your partition should not have moved. it was working prior. But if you want to install jaunty again, you can use the same partition you did for / (root) but make a separate /boot partition. Make sure you set the mountpoint as /boot when you install and the Jaunty partition as /.

---

### Post by presence1960 on 2009-07-04
> **berentorin said:**
> I have a laptop and have been running ubuntu 8.4 with duel boot winXP no problem.
Until I decided to up grade to 9.04. I used (sudo update –manager  -d)  and sat back to enjoy the thoughts of my upgrade . When the time came to accept the upgrade I noticed the upgrade is for 9.10 well I was like a kid in a toy shop.:p

Two hours later the time came to boot the laptop  --- then that’s when the error came up - ERROR 18.
Now I am grumpy. I can’t use win xp for work on Monday. 
I have now loaded 9.04 but still getting the ERROR 18 and it just hangs.:mad:
I have had a look at what’s on offer in the way of a fix, but they all seem to be written in a way that’s above my head. I am able to use terminal but I don’t know what a kernel is so my knowledge has limits.
Is there any one that can tell me in plane terms what I can do to fix this?.

P.S. Something went wrong with the upgrade process because it should have upgraded in this order 8.04 > 8.10 > 9.04.

---

### Post by LewRockwell on 2009-07-04
it is highly recommended to acquire the newer release on a LiveCD and CONFIRM that it will indeed operate properly BEFORE any changes are made to your CURRENT-PROPERLY-FUNCTIONING operating system(s)

and, of course, it goes without saying...

do your darn back-ups FIRST

.

---

### Post by Tutigan on 2009-07-04
Personally, I'd suggest downloading the latest ISO, and removing your old Ubuntu and re-installing Ubuntu.
You may (or may not) be able to boot into Windows from GRUB straightaway. If not, let us know, and we'll be sure to help!

---

### Post by berentorin on 2009-07-08
I thank you all for the help and have now tacken the win xp off my lap top and switched over to ubuntu. now I have to find an accounts package. I have been looking at GNUCASH but its not as easy as it looks to use. That is the last stone to turn for me to go fully linux.

again thank you):P

---

### Post by presence1960 on 2009-07-08
> **berentorin said:**
> I thank you all for the help and have now tacken the win xp off my lap top and switched over to ubuntu. now I have to find an accounts package. I have been looking at GNUCASH but its not as easy as it looks to use. That is the last stone to turn for me to go fully linux.

again thank you):P

try kmymoney2. it is a KDE package but you can install it on Gnome. pretty similar to MS Money except it costs nothing.

---

