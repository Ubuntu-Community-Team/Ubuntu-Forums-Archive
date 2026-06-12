---
title: "Gave up waiting for root device, Ubuntu will not boot"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by 602535 on 2009-12-31
Hey guys, I've been running ubuntu just fine for the last few days- this is actually my first time actually give it a real try so I put it on my MSI Wind.  Besides initial 'wow this is different' shock- I think I have a hang on things.

Though, I do have one problem, and I guess all things considered, it is rather big as the system will no longer boot.

Here's what happened:

I forgot I pulled out my laptop batter, and went to unplug the laptop from the wall ; tldr it turned off :P of course!  Now this is not the first time I've done this... forgetful me.  But this time, it wont boot.

When I power it on, it shows me a menu- booting from ubuntu or the recovery mode.

> if I try to boot, it shows the splash screen and then goes blank

> if I try the recovery mode, it shows a bunch of stuff, then finally:

"gave up waiting for root device."
& "ALERT! /dev/disk/by-uuid/00ff629b(etc) does not exist.  Dropping to a shell!"


If I could get some assistance with this, it would be great :)

---

### Post by danastasio on 2009-12-31
What file system are you using?
I know when i tested JFS and did this, it deleted entire directories, so this may have happened to you, however this is -extremley- unlikley with ext*

If you can boot into the liveCD make sure that everything is there in your home folder and nothing got deleted. then run the command ```
e2fsck -fvP /dev/sda
```

This will check the filesystem for errors and correct them.

---

### Post by 602535 on 2009-12-31
Hey danastasio, thanks for the response

Searching through some other posts, I found a thing that generates a result.txt file for I guess boot information.

According to that, the file system is ext4.

I am currently booting from a USB drive and it looks like everything is fine.

I ran the e2fsck -fvP /dev/sda but I might have not done so correctly- it does not appear to do anything except show possible commands to run it with.

---

### Post by 602535 on 2009-12-31
Odd... I restarted a few times- booting into my USB installed ubuntu, and now it works again.  

I don't know why... but I guess, perhaps I should stop pulling out the power eh.

---

