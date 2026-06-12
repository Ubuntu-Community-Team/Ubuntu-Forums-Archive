---
title: "Ubuntu Maverick hd partitions and installation"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by siretfel on 2010-12-27
Hi all,
I gave a try Ubuntu 10.10 and I'm very impressed.
I would like your suggestions on this:
I have an internal HD on my toshiba sattelite of 120GB
60 is for Vista  (allready installed)
60 is just for data.
I want to split the second disk for data to 2 hds 30 and 30 and put ubuntu in one of two and keep one just for data.
Could you please suggest me how to split the hd where i'll put ubuntu?
i.e. how to split it? I need a swap, an ext4 etc.
How much space to allocate for each?
I have 3GB of Memory.
Any suggestions are welcome.
Oh, something else: 
What about boot? Should i keep vista's boot manager?
Thanks

---

### Post by mikewhatever on 2010-12-27
Gparted is the program to manage partitions. It's on the live cd/usb, and it can resize, create and delete partition.

_The Sizes_
swap - no more then 3GB, less if not planning to suspend to disk.
root - the rest (~17GB).

I'd recommend installing Ubuntu's boot loader and let it manage both Ubuntu and Vista. That's also the default behavior.

---

### Post by amjjawad on 2010-12-27
As mikewhatever suggested, you could go for it but sooner or later, you'll like Ubuntu and perhaps you'll need more space. Anyway, that data partition can be used later as Ubutnu can access NTFS Partitions by default.

There's a Dual-Booting Guide in my signature, please refer to it to avoid some mistakes that others have done just because they did not follow the right procedure. It will show you clearly how to install the Boot Loader (GRUB2) that mikewhatever was referring to.

---

### Post by siretfel on 2010-12-27
Let me just say to both of you thank you very much!
Both replies were great. 
I will do as you suggested and I will follow the excelent guides!
Again thanks a lot for your quick replies.
Happy new year to both of you!

---

### Post by amjjawad on 2010-12-27
> **siretfel said:**
> Let me just say to both of you thank you very much!
Both replies were great. 
I will do as you suggested and I will follow the excelent guides!
Again thanks a lot for your quick replies.
Happy new year to both of you!

Happy new year and you're most welcome :)

---

### Post by siretfel on 2010-12-29
Hi again!
Guys, i'm officially running ubuntu 10.10.
I followed your instructions, and ubuntu runs so smooth so elegant so FREAKING FAST that i'm afraid to touch my laptop hahahahahaha!!!!
:popcorn::guitar:):P

I'm am so thankful to you and so satisfied by ubuntu!

I just wanted to tell you that everything is great as you both said and that from now on ubuntu is my primary and probably the only operating system in my life.

Thanks again!

---

### Post by amjjawad on 2010-12-29
> **siretfel said:**
> Hi again!
Guys, i'm officially running ubuntu 10.10.
I followed your instructions, and ubuntu runs so smooth so elegant so FREAKING FAST that i'm afraid to touch my laptop hahahahahaha!!!!
:popcorn::guitar:):P

I'm am so thankful to you and so satisfied by ubuntu!

I just wanted to tell you that everything is great as you both said and that from now on ubuntu is my primary and probably the only operating system in my life.

Thanks again!

You welcome anytime and I'm so glad you managed to get it up and running :)

ALL the best and Long Live Ubuntu ;)

---

