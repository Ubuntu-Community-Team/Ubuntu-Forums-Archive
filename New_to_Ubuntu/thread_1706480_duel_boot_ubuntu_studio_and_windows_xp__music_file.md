---
title: "duel boot ubuntu studio and windows xp / music files"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by bluemoonshine on 2011-03-13
**I have a desktop computer with the c: drive running windows xp pro ,I have a empty hard drive I plan on installing Ubuntu Studio on. **

**Question, After I do that I would like to I would like to move /copy my windows music folder over to the ubuntu music folder.**

I really dont have the money right now to back them all up on a data dvd dont have external hard drive either ,just two hard drives on one pc ,well that and 4 or 5 pratice pc's 


 I need a simple explanation ,I've read and searched as much as I could and I'm still not sure how to do it, I think I have info overload. 

If I like the my Ubuntu choice maybe I'll scrap that windows xp or just keep it not sure yet it depends on my music files.

---

### Post by TechWiz2100 on 2011-03-14
So long as both devices are in the computer at the same time, Ubuntu should detect your windows hard drive and give you the ability to mount it from Places > <Your Hard drive here>

Also if you cannot set up both hard disks in the same computer you can use one of the other computers to set up an FTP server like Filezilla or Cerberus FTP and connect to the FTP from Ubuntu to get the files.

---

### Post by pi3.1415926535... on 2011-03-14
Well assuming that you can have both drives connected to the computer at once, do so. Then boot into Ubuntu. Next you will want to mount the windows drive. To find the mount point, open gparted (alt+f2, gksu gparted), then you will enter your password. Once gparted is open, find the location of your windows drive and partition, for example /dev/sda1 or the likes. Do not change anything while in gparted. Then mount the drive (alt+f2, gksu mount <drivelocation>, then enter password). Next open the file browser and find the drive, click on it, then navigate to the file with your music and copy it. Then paste it in your Ubuntu music folder. Again, do not change any Windows system files.
Edit: Response already posted

---

### Post by ~Hinterland on 2011-03-14
I would really backup everything before installing.. 
It only takes a problem install or choosing the wrong disk/partition and it's gone.

---

### Post by pi3.1415926535... on 2011-03-14
I believe the OP said that they were installing to an empty hard drive.

---

### Post by TechWiz2100 on 2011-03-14
> **~Hinterland said:**
> I would really backup everything before installing.. 
It only takes a problem install or choosing the wrong disk/partition and it's gone.

OP says s/he has multiple drives so s/he can install with the blank drive then toss in the windows drive. Problem solved.

---

### Post by bluemoonshine on 2011-03-15
> **~Hinterland said:**
> I would really backup everything before installing.. 
It only takes a problem install or choosing the wrong disk/partition and it's gone.
  
That's probably what would happen to me.

---

### Post by bluemoonshine on 2011-03-15
> **pi3.1415926535... said:**
> I believe the OP said that they were installing to an empty hard drive.
  
Yes I'm installing Ubuntu on the empty hard drive. I'm sure my bios have the option  of which  I want to boot to then i can play with the ubuntu see what it is like . then if all goes well move the music files to it.

---

### Post by bluemoonshine on 2011-03-15
> **pi3.1415926535... said:**
> Well assuming that you can have both drives connected to the computer at once, do so. Then boot into Ubuntu. Next you will want to mount the windows drive. To find the mount point, open gparted (alt+f2, gksu gparted), then you will enter your password. Once gparted is open, find the location of your windows drive and partition, for example /dev/sda1 or the likes. Do not change anything while in gparted. Then mount the drive (alt+f2, gksu mount <drivelocation>, then enter password). Next open the file browser and find the drive, click on it, then navigate to the file with your music and copy it. Then paste it in your Ubuntu music folder. Again, do not change any Windows system files.
Edit: Response already posted

 that sounds simple enough to figure out.

---

### Post by bluemoonshine on 2011-03-16
thanks for the help, Its enough for now ,Im waiting on a borrowed external HD to be safer then do the install and see how it goes ..

Thank you all again , this help forum is way beyond what i could ever get from , well you know who..

---

