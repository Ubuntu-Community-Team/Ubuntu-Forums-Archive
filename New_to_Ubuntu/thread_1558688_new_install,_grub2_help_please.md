---
title: "new install, grub2 help please"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by mr-woof on 2010-08-22
lo all,

dead quick and easy one for you all, I've been installing my new system into a new case and onto new disks today, XP is on an 80gb drive (sda) and ubuntu 10.04 is on another 80gb drive (sdb). I've installed the bootloader onto Sdb, thinking that's the right thing to do.

Anyway it just boots straight into XP, I'm now aware that menu.lst has been replaced by grub.cfg, but I'm not sure what to edit now so I can get the dual boot on the go.

I've been at this now for about 8 hours, I'm full of hayfever :( Help! :)

I just want to get grub setup and the updates done and that's me for the day lol

---

### Post by skatinjj on 2010-08-22
> **mr-woof said:**
> lo all,

dead quick and easy one for you all, I've been installing my new system into a new case and onto new disks today, XP is on an 80gb drive (sda) and ubuntu 10.04 is on another 80gb drive (sdb). I've installed the bootloader onto Sdb, thinking that's the right thing to do.

Anyway it just boots straight into XP, I'm now aware that menu.lst has been replaced by grub.cfg, but I'm not sure what to edit now so I can get the dual boot on the go.

I've been at this now for about 8 hours, I'm full of hayfever :( Help! :)

I just want to get grub setup and the updates done and that's me for the day lol

I'd start by changing my hard drive boot priority in BIOS so the drive with Ubuntu boots first and go from there.

If you get to the grub screen, it may have the option to boot into Windows then you would be good to go.

---

### Post by Elfy on 2010-08-22
I'd just have installed grub to sda and not bothered changing it. But if you can change boot order to sdb it should be ok. 

If xp is not there you could try sudo update-grub

---

### Post by mr-woof on 2010-08-22
thanks chaps, I've changed the sata cables round so sdb is on sata1 and it's worked, i can boot into xp as well :)

I really should of thought of that but this hayfever is killing me, it feels like someone is squeezing my head :)

---

### Post by amjjawad on 2010-10-02
I've done the same thing (Ubuntu's Boot loader is installed on sdb) and I had no problem as long as sdb is the first HDD in BIOS. I even installed Ubuntu 10.04 on an external HDD (which means it's USB) and it works smoothly :)

Don't forget to mark this thread as solved if your problem is fixed now ;)

---

