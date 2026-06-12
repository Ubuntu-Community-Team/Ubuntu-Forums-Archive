---
title: "resizing partitions in ubuntu"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by the wombat on 2009-03-18
Hey, so I was ripping music/videos from of a certain "fruit-based" music player to my rythmbox library. After ripping about 1.5 gb, it just froze. after restarting and getting the GDM memory error, I got in and pulled up Gparted. My ubuntu partition for some reason only had about 3 gbs of memory, with windows using only 30 of the 90gb its partitioned. But i cant resize the ntfs because it appears locked in Gparted.

I am wondering the steps needed to take to unlock the ntfs filesystem so i can resize its partition to give ubuntu a little more breathing room. Hopefully the forums can come to my rescue once again lol ;)

---

### Post by MasterSander on 2009-03-18
Try defragmenting the windows partition and try running the gparted live cd

---

### Post by Helios1276 on 2009-03-18
Are you using Vista, Xp etc

---

### Post by Therion on 2009-03-18
**Problem: ** You can't manage a partition while it's mounted, and guess what the NTFS partition does when you boot your PC?  That's right... It mounts.

**Solution:** gParted (now called Parted Magic) LiveCD.  [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by mlentink on 2009-03-18
Boot with the ubuntu live cd. Unmount the windows partition. resize.

---

### Post by Helios1276 on 2009-03-18
Just to add:

If it is Vista you *may* experience difficulty resizing the partition. If so hit up Google for the fix, I'd go into detail but you have yet to specify.

---

### Post by the wombat on 2009-03-18
hey, im running windows xp sp3-ubuntu 8.10 so ill give that fragmenting and booting with the live cd a shot and respond my results, thanks a ton!

---

### Post by DaveG825 on 2009-03-18
Yeah, to keep things simple, just boot from your Ubuntu LiveCD and use the Partition Editor to resize your NTFS partition. Also, keep in mind what Helios said. Vista doesn't like getting it's home compressed. :P

---

### Post by the wombat on 2009-03-18
ok, so i think it worked. I used a program called partition magic, and moved 60 gbs from ntfs to ubuntu, only one quick question, when opening my home folder or destop folder i see that only 4.8 mbs of space is available,is this normal? to have such a small amount of space? a screen shot of the new Gparted is attached. so hopefully my problems are solved? thanks for all your help again =D>


-the available space for my home/video/doc/etc. folders has been fluctuating from 8kb all the way to literally nothing!! idk what to make of it, im baffled

---

