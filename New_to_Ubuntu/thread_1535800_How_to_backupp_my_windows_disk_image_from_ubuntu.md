---
title: "How to backupp my windows disk image from ubuntu"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by sofiaisabel on 2010-07-21
Ok so here goes a difficult question... I installed ubuntu using wubi, (And now i hate myself for it) Basically wubi installs ubuntu using windows. What I want to do is make a partition for ubuntu only, And I think I know how to do this, but the thing is that I would like to make a image backup of my entire disk (including my windos installation) just in case i screw up my entire hard drive. 

So, anyone knows how to make a image backuo of a disk that has windows and wubi-ubuntu in it?

---

### Post by scorchgeek on 2010-07-21
Doesn't wubi just install ubuntu inside the windows partition? (I'm not sure on this, I've never used wubi.) If that's true, all you need to do is image the windows partition using any available software for that purpose.

---

### Post by sofiaisabel on 2010-07-21
Yes that's what wubi does... Ok big problem... I cant make a backup from windows because the softwar for it must be paid for... So i wnat to do it from ubuntu, but if i do it the regular way i think i would just backup the ubuntu part of the disk wouldn't I?

BTW thanks for answering

---

### Post by Frogs Hair on 2010-07-21
When I had Wubi , I used Back in Time to make an image of my home folder . It is possible to enter the host folder from a Wubi installation , but I never tried to make a back up image of the host folder . It may be possible .

---

### Post by edwardLS on 2010-07-21
I have successfully use CloneZilla to do exactly what I think you are trying to do.  You can do the whole disk or a partition.

---

### Post by Mark Phelps on 2010-07-22
> **sofiaisabel said:**
> Yes that's what wubi does... Ok big problem... I cant make a backup from windows because the softwar for it must be paid for...

Not necessarily ...

Macrium Reflect is most probably the best MS Windows partition/drive backup software out there (I use it!) and it's available for free.  Just Google their site, download the free version, install it and use it.  You can even use it to create a Linux-based boot CD.

---

### Post by anewguy on 2010-07-22
> **Mark Phelps said:**
> Not necessarily ...

Macrium Reflect is most probably the best MS Windows partition/drive backup software out there (I use it!) and it's available for free.  Just Google their site, download the free version, install it and use it.  You can even use it to create a Linux-based boot CD.

+1  I've been using Macrium Reflect for years, and so have my friends.  Works like a champ!

---

### Post by pricetech on 2010-07-22
Actually the windows AIK (Automated Installation Kit) is a free download from MS and can be used to image windows.

---

