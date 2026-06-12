---
title: "Kernel Panic-not syncing: Out of memory and no killable processes"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by suomalainen on 2010-05-14
Ubunteros,

Has anyone seen the error message:

Kernel Panic-not syncing: Out of memory and no killable processes?????????

I'm getting this message when using the Live CD of 10.04LTS to install Ubuntu on an internal hard drive of a friends PC.

I don't know what to do next and would appreciate any insight and help.

Thank You!!!!

---

### Post by -humanaut- on 2010-05-14
When are you getting the Error at boot? During Install?

---

### Post by suomalainen on 2010-05-14
> When are you getting the Error at boot? During Install?

> I'm getting this message when using the Live CD of 10.04LTS to install Ubuntu on an internal hard drive of a friends PC.


Does this help?????

---

### Post by -humanaut- on 2010-05-14
No, What I'm asking is does the LiveCD even boot? or Is Ubiquity failing during the installation.

---

### Post by suomalainen on 2010-05-14
I see some sort of a splash screen and then seconds later the error message. The Live CD will boot in other laptops and PC's perfectly. This is the first time I've seen this error message using this CD for this particular install.

DOes this help? Thanks for Your support!!!

---

### Post by -humanaut- on 2010-05-14
Yes, It could be the installation media. Also try booting with the kernel parameter NOMODESET and NOAPCI that will essentially boot it into safe mode. Could you give me the specs of the PC?

---

### Post by suomalainen on 2010-05-14
How do you boot EXACTLY in NOMODESET or NOAPCI???? I've never done that before.

base memory: 640K
Extended Memory: 64512K
Other Memory 384k
Total Memory: 65536K

CPU type: Pentium-MMX
CPU speed 233 MHz
Base memory: 640k
Cache Memory 512k

this was all I could find as bios is quite old...

Thanks again for your support!!!

---

### Post by -humanaut- on 2010-05-14
To be honest with you Ubuntu isn't going to run on that system. I'd recommend something MUCH MUCH MUCH lighter such as DeLi Linux,DSL,Slitaz,Puppy you could theoretically get Lubuntu to install off an Alternate Text based installation but I'd imagine even that would be too heavy DeLi Linux or Absolute Linux would be your best bet for a system like that.  Or if your comfortable building a Debian system you could install a bare-bones command line system then add X,IceWM (or maybe Fluxbox).

[http://www.delilinux.org/](http://www.delilinux.org/)
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)
[http://www.absolutelinux.org/](http://www.absolutelinux.org/)
[http://www.puppylinux.org/](http://www.puppylinux.org/)

Those should all run on that system.

---

### Post by suomalainen on 2010-05-14
What improvements would need to be made to get it to work? Increase memory? Or what?

---

### Post by -humanaut- on 2010-05-14
The absolute only feasible way I could see ubuntu running on that system is to download the minimal .iso and carefully hand picking packages such as iceWM Xorg Gnome,KDE,Xfce, and LXDE are all going to struggle on that system. I wouldn't recommend anything less then a Pentium III 1GHZ minimum 512MB of Ram for a full blown Gnome Ubuntu Installation.

---

### Post by ~VaSiK~ on 2010-09-09
Dear -humanaut-,

I have the same problem during installation Ubuntu Server 9.10. 
This error appear during hardware detection (as i understand, first is network card).

Hardware is next:
CPU - P3 400MHz
RAM - 64M

I know that main problem can be in low memory. 
But can i some how install ubuntu server on this PC? 
Maybe beter to use oldest release of Ubuntu? Can it help me?

Thank in advance!

---

