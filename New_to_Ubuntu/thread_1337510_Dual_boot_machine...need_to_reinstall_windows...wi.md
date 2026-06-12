---
title: "Dual boot machine...need to reinstall windows...will it affect Ubuntu?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by jotto! on 2009-11-25
I have had a major crash....another reason to ditch MS all together but....but....I want to reinstall windows. I could opt for a repair install but if I reinstall, I like to know its clean.

Is there any way to back up my ubuntu as it is now and just re format the whole drive, load windows and then reinstate my ubuntu or would I need to to a clean install of it?

I installed ubuntu from within windows and have both the 9.04 and 9.10 flavours on disk...

Help!

---

### Post by scragar on 2009-11-25
You will be safe to reinstall as long as you pick the right partition, I'd still back up before that though, just incase you make a mistake.
Once windows has been reinstalled you'll need to reinstall grub from a liveCD.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jotto! on 2009-11-25
But if I re format the drive I will lose everything.
Is there any way to back up my ubuntu installation as it is and then restore it after a clean windows install? Im happy to reinstall ubuntu but it would be nice to have it as it is now.

---

### Post by scragar on 2009-11-25
If you have somewhere to put it, an external HD, or a larger internal HD you can back up the entire partition to an image, then restore it if anything goes wrong(USE A LIVECD TO BACK IT UP AND RESTORE IT).

First you'd wanna check your partition name, it's whatever is mounted on /
```
mount
```
EG: my output(first 5 or so lines)```
**/dev/sda3 on / type ext4 (rw)**
none on /dev type tmpfs (rw,relatime,mode=755)
none on /proc type proc (rw,relatime)
none on /sys type sysfs (rw,relatime)
```
Then using your liveCD mount the destination for your backup, then do this in a terminal. Make sure you copy it right, so as to avoid corrupting your partition:
```
sudo dd if=**/dev/sda3** of=**/path/to/backup/mount/location**/backup.img
```
Change the bold parts as needed.
Restoring is easy enough:
```
sudo dd if=**/path/to/backup/mount/location**/backup.img of=**/dev/sda3**
```

---

### Post by doas777 on 2009-11-25
> **jotto! said:**
> But if I re format the drive I will lose everything.
Is there any way to back up my ubuntu installation as it is and then restore it after a clean windows install? Im happy to reinstall ubuntu but it would be nice to have it as it is now.

windows does not need to format the drive, only the partition that you choose to install to. I would suggest that you just format the partition that windows is currently on, and install to it. 

the only other part of the drive that windows will write to, is the MBR (first sector of the disk). when the mbr gets rewritten, you will not be able to boot ubuntu, untill you reinstall grub into the mbr, as  scragar suggests. after you have reinstalled grub, both windows and ubuntu shoudl be able to boot.

here are instructions on how to do that:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

as for your ubuntu backup, I recomend that when you get a chance, that you create a seperate home partition, that way if you reinstall ubuntu, it's easy to keep all your personal files and user settings. all you would have to do is reinstall your apps, and reapply any system settings.

---

### Post by jotto! on 2009-11-25
Thanks for all the info guys!

I think I will re format my 300gb HDD but have multiple partitions. At present, I have only the one with both windows and ubuntu.

Im thinking it makes sense to keep them separate so that when ms goes tits up again...and it will....I can just reformat that particular partition keeping ubuntu intact with just the need to reinstall grub.

Might try another flavour of ms....vista or 7. I like XP as it seems fairly stable but at the end of the day, I can see me switching to ubuntu completely.

---

