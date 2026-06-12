---
title: "How to enable PAE"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by beew on 2011-08-18
Hi,

I have a 32 bit installation of Natty in an external drive which I use as a portable. Recently I get my hands on a new 64 bit computer which I can boot it from but it is only accessing 3 G of ram (the computer has 16G) I thought PAE is activated automatically but apparently it is not. How do I activate it or do I need to install the pae headers for the kernel? (do I ned the pae kernel image too?)

Thanks.


P.S. Since I only have sporadic access to this machine it wouldn't worth the troubles for me to install a full blown 64 bit system in my external drive in case anyone is wondering. :)

---

### Post by Enigmapond on 2011-08-18
Yes you need the PAE kernel. This will maybe help..
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by NightwishFan on 2011-08-18
You might need this package? Not sure. [http://packages.ubuntu.com/natty-updates/linux-image-generic-pae](http://packages.ubuntu.com/natty-updates/linux-image-generic-pae)

---

### Post by seawolf167 on 2011-08-18
> **beew said:**
> P.S. Since I only have sporadic access to this machine it wouldn't worth the troubles for me to install a full blown 64 bit system in my external drive in case anyone is wondering.

Although if you have a separate / (root) partition doing a full x86_64 install would be a breeze (depending on the currently installed software). Just sayin' :P

---

### Post by beew on 2011-08-18
> **seawolf167 said:**
> Although if you have a separate / (root) partition doing a full x86_64 install would be a breeze (depending on the currently installed software). Just sayin' :P

I do have a separate / partition but I don't want to lose my 32 bit system since all computers I can boot it from are 32 bits. If I have regular access to a 64 bit machine it would justify having a separate install of a 64 bit system but if I only can access once every couple of weeks it wouldn't worth the troubles, I just want to do some testings.

---

### Post by trozamon on 2011-08-18
If you want to get really fancy, you could dual boot 64-bit and 32-bit on the external hard drive, with three partitions: one for x64, one for x32, and one for data. Native 64-bit operating systems perform better than PAE by a slight amount.

---

