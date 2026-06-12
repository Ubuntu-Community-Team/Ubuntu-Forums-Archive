---
title: "difficulty granting permissions for USB drive"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by soulful on 2010-06-21
Greetings all!
   
  This may be my first post, but I'm not an absolute noob: I've been with Ubuntu since Hardy Heron.
   
  I'm having trouble setting permissions on a folder on an external (USB) drive, which I was able to do in HH.
   
  When I try and grant permissions to "others" (via right click, properties in Nautilus), the settings aren't accepted.  The permissions in the drop-down box revert immediately to their original settings.
   
  I can access the troublesome folder on the external hard drive from Mac OS if I provide the credentials of the owner of the folder. I can't access it from Windoze XP regardless of what I do.
   
  However, I was able to provide unrestricted read/write access to a folder on my system drive without a problem.
   
  I did try two external drives, both with the same result.  This second one was fresh out of the box and formatted in Ubuntu for the first time, so I think there's no issue with not being the "owner" of the drive.
   
  Anything I can try?  As I mentioned I'm not a complete newb, but if your solution involves a console window, I'd appreciate your taking the time to spell it out.
   
  I did have a bit of a fish around for other posts on the subject but didn't find anything.  Apologies if I've overlooked a solution posted elsewhere, or posted it in the wrong forum...

---

### Post by soulful on 2010-06-24
Nobody then? :confused:

---

### Post by soulful on 2010-06-29
I'm on 10.04.  Looks like I forgot to note that in my OP. :sad:

If there's any other information I could provide that would make this easier to diagnose, kindly let me know...

---

### Post by Iowan on 2010-07-06
Moved to Absolute Beginner Talk by request.

---

### Post by philinux on 2010-07-06
> **soulful said:**
> I'm on 10.04.  Looks like I forgot to note that in my OP. :sad:

If there's any other information I could provide that would make this easier to diagnose, kindly let me know...

Try using ```
gksu nautilus
```

Be careful with the root browser.

---

### Post by nothingspecial on 2010-07-06
What permissions do you want to assign to it?

Is it a file system that supports linux file permissions? (I ask because you mention plugging it in to windows)

---

### Post by soulful on 2010-07-06
Thanks for the replies! :D

@philinux:

Thanks, but I was already using "sudo nautilus"

@nothingspecial:

The file system is msdos.  (What filesystems support privileges in linux anyways? A pointer to an explanatory article would be appreciated!)

I've actually never physically plugged the drive in question into a windows system: when I say "I can't access it from Windoze XP" I mean across the LAN here.

I'm basically trying to give everyone read/write permissions, so that unauthenticated users (anyone in the house) can use it as a backup drive.

This is the second external hard drive I've tried.  I had successfully granted everyone read/write permissions on a folder on the previous external drive under Hardy Heron, but then when I upgraded to 10.04 and plugged the old drive in, I couldn't do the same thing, so I thought I'd try a new drive to ensure I was the owner of the drive.

---

### Post by soulful on 2010-07-11
...anyone?  (Surely I can't have stumped entire the ubuntu/linux community.)

> **nothingspecial said:**
> Is it a file system that supports linux file permissions? (I ask because you mention plugging it in to windows)
So am I OK with msdos here?

---

