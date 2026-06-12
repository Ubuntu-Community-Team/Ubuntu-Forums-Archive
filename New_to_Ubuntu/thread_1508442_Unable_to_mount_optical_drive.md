---
title: "Unable to mount optical drive?"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by UnlimitedBrigade on 2010-06-13
Hi guys. Second day of using Ubuntu so far and I like it alot. Finally was able to set up dual screens after a long 30mins or so after some research with the only issue is that I haven't the slightest clue on how to have 2 seperate wallpapers applied to each screen. 

Anyways, on to the point...

**For some reason I can't mount my CD/DVD drive. I have tried:**
$ sudo mount -t iso9660 /dev/sr0 /media/cdrom

**With the return of:**
mount: no medium found on /dev/sr0

I was using the same optical drive to install Ubuntu and found it strange that it would not work after the installation was complete. I have a screenshot but I'm not sure what good it will do for you guys helping me out there. The eject function doesn't even work and it states that it was picked up as a SCSI device, when in fact it is connected as an IDE device. Could this be the issue?          

](*,)

[IMG]http://img22.imageshack.us/img22/8874/screenshotep.png[/IMG]

---

### Post by Bucky Ball on 2010-06-13
Try putting a cd in it.

---

### Post by UnlimitedBrigade on 2010-06-13
I just tried a few. Still no luck.

---

### Post by techunit on 2010-06-13
Unless I am misunderstanding you I believe that you don't unmount a CD or DVD you eject it. you have to have the CD in the Drive. Hope this helps.

---

### Post by garvinrick4 on 2010-06-13
screenshot looks fine.

Try 

```
sudo eject /dev/sr0
```  (last being the number 0)

Should open your Opltical drive.

---

### Post by UnlimitedBrigade on 2010-06-13
> **garvinrick4 said:**
> screenshot looks fine.

Try 

```
sudo eject /dev/sr0
```  (last being the number 0)

Should open your Opltical drive.

Command didn't work. And thank you all for your input btw.

---

### Post by UnlimitedBrigade on 2010-06-13
I think you can probably close this thread now. It's very odd, but after having a CD inside my drive for about 5 hours, it finally decides to read it. I don't know how, or maybe I'm just going crazy but yes it's reading CDs now or seems to be doing so intermittently.

---

### Post by UnlimitedBrigade on 2010-06-15
Scratch that. My optical driver is still having issues. I don't know why but it's not reading anything lately. I've tried every type of cd/dvd you can probably think of and it still does not recognize it.

I have tried going to Places> and it doesn't even show up. Help?

---

### Post by sandyd on 2010-06-15
run```

gksudo gedit /etc/fstab
```
if there is a line that begins with "/dev/sc0", replace the line with
```

/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0
```
if not, create a new line at the bottom of the file with these contents
```

/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0

```

---

### Post by sandyd on 2010-06-15
the rest of the thread is here btw
[http://ubuntuforums.org/showthread.php?t=1235151](http://ubuntuforums.org/showthread.php?t=1235151)

---

### Post by Bucky Ball on 2010-06-15
... or try another optical drive and make certain this is not a hardware problem. They generally don't last forever ...

---

