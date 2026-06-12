---
title: "Trying to redownload Vista out of Ubuntu"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by maxrsurf on 2010-05-07
Help! im a complete Ubuntu noob. I accidentally deleted vista and now am stuck with ubuntu. I have the vista cd but it cant play on ubuntu. Ive tried to set the cd priority in BIOS to #1 but the CD option isnt even shown in BIOS. Im really really lost...

---

### Post by QIII on 2010-05-07
Are you putting the CD in the tray, shutting down and restarting?

---

### Post by Rasa1111 on 2010-05-07
"stuck with Ubuntu"..
what a terrible problem to have!  lol

it should 'play' fine if you reboot the PC with the disc in the drive. 

now.. if i were *stuck* with vista..
i would be freakin out for sure. lol

---

### Post by maxrsurf on 2010-05-07
No it wont play the cd at all

---

### Post by Legendary_Bibo on 2010-05-07
[http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html](http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html)

Problem solved

---

### Post by ankspo71 on 2010-05-07
Are you sure the boot device is not marked as disabled making it hidden?
There should be something like this below shown in your bios...
> boot device priorities:
first boot device [floppy]
second boot device [hard drive]
third boot device [disabled]
fourth boot device [disabled]

If you select any of them, you should be able to switch from "disabled" to "cdrom" etc, then arrange them up and down in the list to change priority.

If you only see the hard drive boot priorities, you are looking in the wrong place in the bios. Example:
> 
Hard drive priority:
first hard drive [ATA-120blahblahblah]
second hard drive [disabled]

---

### Post by mike555 on 2010-05-07
I think it must be the Windows CD , after all if your computer wont start on a cd how did you install Ubuntu??

---

### Post by diablo75 on 2010-05-07
> **mike555 said:**
> I think it must be the Windows CD , after all if your computer wont start on a cd how did you install Ubuntu??

Probably with Wubi....

---

### Post by Mark Phelps on 2010-05-07
Vista doesn't come on a "CD"; it only comes on a DVD.

If you're asking can you install it from inside Ubuntu, the answer is no.  You will have to boot from the DVD and install that way.

But first, you'll need to make sure you have free space on your drive to install Vista. If you don't have that, you will need to use GParted to shrink the Ubuntu partition to make some free space -- and since you're running Ubuntu, you can't do that from inside Ubuntu.

The easiest way is to download and burn the GParted LiveCD (from distrowatch.com) and boot from that to do your partition work.

---

