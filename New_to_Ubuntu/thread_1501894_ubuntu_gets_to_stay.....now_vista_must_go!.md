---
title: "ubuntu gets to stay.....now vista must go!"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by CaptMorgane on 2010-06-04
Alright, I'm in. Now I want to rid windoze from my laptop so that I can free up about 15 gigs.

How do I go about it? What do I need to do to wipe the partition with windoze in it?

I've already backed up all other files.

---

### Post by sandyd on 2010-06-04
> **CaptMorgane said:**
> Alright, I'm in. Now I want to rid windoze from my laptop so that I can free up about 15 gigs.

How do I go about it? What do I need to do to wipe the partition with windoze in it?

I've already backed up all other files.
```

sudo apt-get install gparted
gksudo gparted
```

delete the windows partition. and don't do it if you installed ubuntu using wubi, rather than a dual boot.

---

### Post by Mark Phelps on 2010-06-05
> **carlee said:**
>  ... and don't do it if you installed ubuntu using wubi, rather than a dual boot.

Very important point! 

If you installed via Wubi and you delete Windows, you will delete the Wubi install as well.  So, be sure to confirm that it is a separate non-Wubi install first.

---

### Post by eriktheblu on 2010-06-05
run
```
sudo update-grub
```
once you have deleted the partition (assuming Grub2 is installed).

---

### Post by 29732 on 2010-06-06
Although Ubuntu is a good OS, keep in mind that Ubuntu can't do EVERYTHING Windows can.
Sure, WINE and a few other programs can use windows programs, it cant run all Windows programs on there. For instance, I once tried to run VoipDiscount on Ubuntu WINE, and in the middle of the installation, it just hung on finding servers, and etc.
And if you play very graphical games on there like Bioshock for example (awesome game by the way) I heard the graphics won't run as smoothly, so it might occasionally be choppy in places...

But I don't know everything and if you're a VERY experienced Ubuntu user (I'm somewhat getting there) you just might find a way to fix all of those problems.

Well, I've gave you the warning so if you stilll think you should destroy Vista, it's all up to you.

---

### Post by Rubi1200 on 2010-06-06
Backing up is always an excellent move and carlee and Mark Phelps are absolutely right about Wubi.

The only point I would like to make is that I think it is always preferable to move/resize/delete/create partitions using GParted from the LiveCD rather than from within the installation itself. I base this on hard experience and the views of other, more experienced users who almost always suggest that this is the better method.

Good luck anyway!

---

### Post by acrazyplayer on 2010-06-06
> **Rubi1200 said:**
> Backing up is always an excellent move and carlee and Mark Phelps are absolutely right about Wubi.

The only point I would like to make is that I think it is always preferable to move/resize/delete/create partitions using GParted from the LiveCD rather than from within the installation itself. I base this on hard experience and the views of other, more experienced users who almost always suggest that this is the better method.

Good luck anyway!

Yeah using a LiveCD  is far better as you can not resize Ubuntu while using it. However you should delete Windows first from within Ubuntu then run "sudo update-grub" as said before to make sure you can boot back into Ubuntu after everything is done.

---

### Post by hatalar205 on 2010-06-06
> **29732 said:**
> Although Ubuntu is a good OS, keep in mind that Ubuntu can't do EVERYTHING Windows can.
Sure, WINE and a few other programs can use windows programs, it cant run all Windows programs on there. For instance, I once tried to run VoipDiscount on Ubuntu WINE, and in the middle of the installation, it just hung on finding servers, and etc.
And if you play very graphical games on there like Bioshock for example (awesome game by the way) I heard the graphics won't run as smoothly, so it might occasionally be choppy in places...

But I don't know everything and if you're a VERY experienced Ubuntu user (I'm somewhat getting there) you just might find a way to fix all of those problems.

Well, I've gave you the warning so if you stilll think you should destroy Vista, it's all up to you.

I am agree with you. Although I am a fan of linux and hate everything about Microsoft, and I deleted the pre-installed XP from my netbook immediately after I had bought, I want to say you that unfortunately Linux can't do everything all the time. Because of manifacturers ignoring Linux part, sometimes still I need windows. For example, I need to update my bios, and guess what. There is only windows installer version of bios updater. So I had to install Windows and updated bios. It was really a big headache. But again I deleted the windows partition last week. :)

---

