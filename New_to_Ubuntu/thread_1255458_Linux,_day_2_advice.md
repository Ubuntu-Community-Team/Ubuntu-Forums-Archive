---
title: "Linux, day 2 advice"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by DamITman on 2009-09-01
I've been using windows for 12 years and the transition was almost seamless for me. As a Linux beginner my best educated advice is to read every update before you install it. 

If you're as reckless & MS friendly as I was, you will probably not think to do so. This can complicate many things, for instance, with the EEEbuntu flavor there is a custom kernel update (linux-kernel-eb)  that will completely kill your atheros drivers, and in my case broke add & remove completely.

The most important thing I've learned, since first boot into Linux yesterday, is to know your drivers, know your chipsets, and know how to manually diagnose & replace the driver in the event an update kills it.
If you've played with MS-DOS before, adapting to Ubuntu will be much easier I've noticed.

Be prepared to re-install several times or study very tediously after you first ditch windows. Even consider a bit of study before the switch, A live disk/usb-drive as well as using it in a virtual machine can make transition even more simple.

I still have much to learn, but from one beginner to another, I hope this will help someone.

---

### Post by Me887799 on 2009-09-01
Don't blindly copy/paste bits of commands you find on google.  The chance is slim but someone could try to be an *** and make you accidentally remove /
Plus, it's good to learn the commands instead of just copy/pasting.

In the same vein as your post it's good to actually be careful with what your installing, especially updates, so you're able to know what you changed and it really does take out a lot of guess work if something breaks.

You can find out pretty much everything spec wise for your computer by using terminal by entering

> sudo lshw

---

### Post by steveneddy on 2009-09-01
> **DamITman said:**
> I've been using windows for 12 years and the transition was almost seamless for me. As a Linux beginner my best educated advice is to read every update before you install it. 

If you're as reckless & MS friendly as I was, you will probably not think to do so. This can complicate many things, for instance, with the EEEbuntu flavor there is a custom kernel update (linux-kernel-eb)  that will completely kill your atheros drivers, and in my case broke add & remove completely.

The most important thing I've learned, since first boot into Linux yesterday, is to know your drivers, know your chipsets, and know how to manually diagnose & replace the driver in the event an update kills it.
If you've played with MS-DOS before, adapting to Ubuntu will be much easier I've noticed.

Be prepared to re-install several times or study very tediously after you first ditch windows. Even consider a bit of study before the switch, A live disk/usb-drive as well as using it in a virtual machine can make transition even more simple.

I still have much to learn, but from one beginner to another, I hope this will help someone.

Great advice.

Don't forget the most important thing:

It is only an operating system. Just use what suits your needs and above all else, have fun.

---

### Post by DamITman on 2009-09-01
> **Me887799 said:**
> Don't blindly copy/paste bits of commands you find on google.  The chance is slim but someone could try to be an *** and make you accidentally remove /
Plus, it's good to learn the commands instead of just copy/pasting.

In the same vein as your post it's good to actually be careful with what your installing, especially updates, so you're able to know what you changed and it really does take out a lot of guess work if something breaks.

You can find out pretty much everything spec wise for your computer by using terminal by entering


Hah, yes, the random hd wipe codes! I ran into one of those several hours after first install. Needless to say I do the Konsole work myself now. Goodbye blind-eyed MS mentality. :D

Thanks for the code though, I'm gonna read up about its functions right now, every little bit helps!

---

