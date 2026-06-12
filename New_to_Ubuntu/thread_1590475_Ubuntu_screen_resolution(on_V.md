---
title: "Ubuntu screen resolution(on V"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by TheLowestAnimal on 2010-10-07
Soo... I installed Ubuntu(newest version) on to Virtual Box, everything went fine till I noticed the resoulution for the screen was running @ 800x600.
Not being big enough for my screen I attempted to change it, but the only option I get is for this one and an even smaller resolution.

I've been looking online and I saw some fixes using the /etc/X11/xorg.conf
but that doesn't seem to be fixing it for me. Whenever what I think is the xorg.conf data comes up; after using the terminal to retreive it, people say it's supposed to have data that I need to alter on it but for me it shows up blank with nothing on it.
Oh, I also tried doing a fix orginally through the monitor under prefences I think and it doesn't detect my monitor or anything, it just says "UNKNOWN" on the screen.

Any help resolving this will be greatly appreciated, Thx  in advance.:confused:

---

### Post by yetiman64 on 2010-10-07
> **TheLowestAnimal said:**
> Soo... I installed Ubuntu(newest version) on to Virtual Box, everything went fine till I noticed the resoulution for the screen was running @ 800x600.
Not being big enough for my screen I attempted to change it, but the only option I get is for this one and an even smaller resolution.

I've been looking online and I saw some fixes using the /etc/X11/xorg.conf
but that doesn't seem to be fixing it for me. Whenever what I think is the xorg.conf data comes up; after using the terminal to retreive it, people say it's supposed to have data that I need to alter on it but for me it shows up blank with nothing on it.
Oh, I also tried doing a fix orginally through the monitor under prefences I think and it doesn't detect my monitor or anything, it just says "UNKNOWN" on the screen.

Any help resolving this will be greatly appreciated, Thx  in advance.:confused:
Have you installed the guest additions package yet, as it generally supplies the necessary kernel modules for graphics, mouse integration and other advanced Virtualbox features?
I've never had low graphics problems after installing the guest addition addons.

---

### Post by Toz on 2010-10-07
Just an FYI.

Virtualbox does not yet support the latest version of X that ships with ubuntu 10.10 and therefore virtualbox additions do not work (meaning you won't get the extended screen resolutions). There are two options:

1. There is a patched version of virtualbox additions that works and is available on the virtualbox forums (can't find link now). I've installed it, it works, but I find it slow and sluggish. 

2. There is a second fix where you can install the ose virtualbox additions that supposedly work ([http://tutorial.downloadatoz.com/how-to-fix-ubuntu-10-10-virtualbox-guest-additions-problems.html](http://tutorial.downloadatoz.com/how-to-fix-ubuntu-10-10-virtualbox-guest-additions-problems.html)) - I haven't tried them yet.

There will be a new version of Virtualbox released shortly that will support this version of X - we may just have to wait for it.

/ToZ

---

### Post by TheLowestAnimal on 2010-10-08
Ok, cool

@ yetiman64
     Yeah, I already tried guest additions. I think I'll take another look and make sure I did everything right, just to be on the safe side.

@ Toz  Thanks a whole bunch

       I'll try to do the second method and then post how it works here.
       If that doesn't work I'll look around to find the first fix

I really don't wanna have to wait for the new VBox

Thanks you guys have been a big help and at least I now have some idea of where to start to resolve this issue...

---

### Post by TheLowestAnimal on 2010-10-08
@ Toz
 It seems that the fix you suggested worked...I think.
  I followed the instructions it gave and restarted Ubuntu,,, it showed
  no signs of improvement but then I randomly dcieded to reload from a
  snapshot I had; Now I know when I took this snapshot it had a resolution 
  of 800x600 or something close to that range. When it loaded it had fit to
  my screen.
 
 So unless anyone else has some insight as to why it suddenly fixed itself
  I'm kinda forced to believe it was the solution you gave me. :popcorn:

---

