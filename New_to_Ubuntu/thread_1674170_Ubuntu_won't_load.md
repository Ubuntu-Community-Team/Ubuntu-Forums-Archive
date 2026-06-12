---
title: "Ubuntu won't load"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by gallacey on 2011-01-23
Hello everyone,

I did something wrong and completely messed up my Ubuntu. I was trying to change how a partition mounted. In mount manager I changed the partition to mount from the computer/ directory. Now Ubuntu won't load, I only get a blinking cursor when I select it from the boot screen. Also, I edited fstab but I can't get into Ubuntu to revert to the backup fstab.   

Is there anything I can do to get it back?

---

### Post by [Snc] on 2011-01-23
> **gallacey said:**
> Hello everyone,

I did something wrong and completely messed up my Ubuntu. I was trying to change how a partition mounted. In mount manager I changed the partition to mount from the computer/ directory. Now Ubuntu won't load, I only get a blinking cursor when I select it from the boot screen. Also, I edited fstab but I can't get into Ubuntu to revert to the backup fstab.   

Is there anything I can do to get it back?

You can boot into a live CD/USB and revert back to normal or backup.

Allways have a live CD/USB ready when working on vital things!

---

### Post by gallacey on 2011-01-23
Is that the same as the CD I used to initially install Ubuntu? If not, I may be screwed as I do not have another Ubuntu CD. 

Is my only other option to reinstall?

---

### Post by [Snc] on 2011-01-23
> **gallacey said:**
> Is that the same as the CD I used to initially install Ubuntu? If not, I may be screwed as I do not have another Ubuntu CD. 

Is my only other option to reinstall?

Yes, the installation cd gives you the option to Try ubuntu prior to installing... I attached a screenshot.

---

### Post by [Snc] on 2011-01-23
> **gallacey said:**
> Is that the same as the CD I used to initially install Ubuntu? If not, I may be screwed as I do not have another Ubuntu CD. 

Is my only other option to reinstall?

Also you can create a bootable USB simply with an ISO (downloaded from ubuntu.com) and UNetbootin (Windows and Linux versions available...)

---

### Post by gallacey on 2011-01-23
> **'[Snc] said:**
> Yes, the installation cd gives you the option to Try ubuntu prior to installing... I attached a screenshot.


Okay, I'm going to try that and report back. Thank you.

---

### Post by gallacey on 2011-01-23
> **'[Snc] said:**
> Also you can create a bootable USB simply with an ISO (downloaded from ubuntu.com) and UNetbootin (Windows and Linux versions available...)

Is that better than the CD?

---

### Post by gallacey on 2011-01-23
Okay, that worked to allow me in a separate version of Ubuntu. I went to the directory that has the installed version to try to change the backup fstab to just fstab but I don't have the necessary permission. What do I need to do to get permission?

---

### Post by sandyd on 2011-01-23
> **gallacey said:**
> Okay, that worked to allow me in a separate version of Ubuntu. I went to the directory that has the installed version to try to change the backup fstab to just fstab but I don't have the necessary permission. What do I need to do to get permission?
```

gksu nautilus
```
go to the directory you mounted, it should be in /media

---

### Post by [Snc] on 2011-01-23
> **gallacey said:**
> Okay, that worked to allow me in a separate version of Ubuntu. I went to the directory that has the installed version to try to change the backup fstab to just fstab but I don't have the necessary permission. What do I need to do to get permission?

```
sudo cp *file to copy* *file to copy to*
```or just run ```
sudo nautilus
``` from the terminal and copy it via the file manager GUI

or Alt+F2 and then run gksu nautilus and also copy it via the file manager

ps. better safe then sorry, also make an extra backup of the file you want to replace.

sorry for the late response ;)

---

### Post by gallacey on 2011-01-23
Okay, I switched the fstab files. Rebooting and be back.

---

### Post by gallacey on 2011-01-23
Woohoo, that worked! Thanks so much for your help [Snc] and sandyd.

My lesson for the day is: don't mess with things that you have no idea about.

Okay, so here's the problem that I was trying to solve in the first place.

My drive is partitioned and my music files are in one partition. When I try to play music files, the player I was using did not seem to find the partition unless I went to Places and selected it. 

The partition does not show on the desktop unless I go to Places and select it, so I figured it was not mounting automatically. Now I don't know if that is the case or if it's just the player.

If a partition mounts automatically, should it show on the desktop upon loading?

---

### Post by [Snc] on 2011-01-23
> **gallacey said:**
> Woohoo, that worked! Thanks so much for your help [Snc] and sandyd.

My lesson for the day is: don't mess with things that you have no idea about.

Okay, so here's the problem that I was trying to solve in the first place.

My drive is partitioned and my music files are in one partition. When I try to play music files, the player I was using did not seem to find the partition unless I went to Places and selected it. 

The partition does not show on the desktop unless I go to Places and select it, so I figured it was not mounting automatically. Now I don't know if that is the case or if it's just the player.

If a partition mounts automatically, should it show on the desktop upon loading?

Great :)

Well, if you click "Places" -> "Computer" then you should see if the volume is mounted, by seeing a CD player like "eject" button next to it, if there is none, its not mounted.

ps. Yes, it should show up on the desktop and it will auto mount if being accessed, but i guess you want it to mount automatically?

---

### Post by [Snc] on 2011-01-23
> **'[Snc] said:**
> Great :)

Well, if you click "Places" -> "Computer" then you should see if the volume is mounted, by seeing a CD player like "eject" button next to it, if there is none, its not mounted.

ps. Yes, it should show up on the desktop and it will auto mount if being accessed, but i guess you want it to mount automatically?

After a little search of the forum i found this:

[http://ubuntuforums.org/showthread.php?t=1498130](http://ubuntuforums.org/showthread.php?t=1498130)

I recognized it :) because i also used it some time ago ;) it works

---

### Post by gallacey on 2011-01-25
> **'[Snc] said:**
> Great :)

Well, if you click "Places" -> "Computer" then you should see if the volume is mounted, by seeing a CD player like "eject" button next to it, if there is none, its not mounted.

ps. Yes, it should show up on the desktop and it will auto mount if being accessed, but i guess you want it to mount automatically?


Sorry it took me a while to get back here.

I only see the eject button if I click on the partition to access it first, when I initially click on places it is not there. So I'm guessing that the volume does not mount until I access it. I am going to read the link that you provided and hope that resolves that issue. 

Thanks so much for your help, it is greatly appreciated.

---

