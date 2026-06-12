---
title: "I need help applying a patch, please"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Mint Sharpie on 2009-11-17
Hi everyone, I'm a bit of a newbie to the more technical aspects of Linux and I have the "display server broken" problem described here: [http://ubuntuforums.org/showthread.php?p=8335139#post8335139](http://ubuntuforums.org/showthread.php?p=8335139#post8335139)

The error message directed me to

[http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/](http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/)

which was followed up with

[http://blogs.gnome.org/hughsie/2009/08/14/blanking-in-gnome-power-manager-fixed/](http://blogs.gnome.org/hughsie/2009/08/14/blanking-in-gnome-power-manager-fixed/)

and linked me to this patch:

[http://cgit.freedesktop.org/xorg/xserver/patch/?id=db568f9eabf3450d8a023597ff007df355b13ea8](http://cgit.freedesktop.org/xorg/xserver/patch/?id=db568f9eabf3450d8a023597ff007df355b13ea8)

but I don't know how to implement it. What do I do with the code? I'd really appreciate any help anybody could give me.

Thanks!

---

### Post by rb0171610 on 2009-11-17
> **Mint Sharpie said:**
> Hi everyone, I'm a bit of a newbie to the more technical aspects of Linux and I have the "display server broken" problem described here: [http://ubuntuforums.org/showthread.php?p=8335139#post8335139](http://ubuntuforums.org/showthread.php?p=8335139#post8335139)

The error message directed me to

[http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/](http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/)

which was followed up with

[http://blogs.gnome.org/hughsie/2009/08/14/blanking-in-gnome-power-manager-fixed/](http://blogs.gnome.org/hughsie/2009/08/14/blanking-in-gnome-power-manager-fixed/)

and linked me to this patch:

[http://cgit.freedesktop.org/xorg/xserver/patch/?id=db568f9eabf3450d8a023597ff007df355b13ea8](http://cgit.freedesktop.org/xorg/xserver/patch/?id=db568f9eabf3450d8a023597ff007df355b13ea8)

but I don't know how to implement it. What do I do with the code? I'd really appreciate any help anybody could give me.

Thanks!
Try reading the manual pages for the patch program.  
```
man patch
```
First you need to know which file you want to patch, secondly you should make a backup copy of this file by renaming it to something .bak in case the patch does not solve your problem or has unexpected results.

---

### Post by Mint Sharpie on 2009-11-17
Thank you; so is the file that needs to be patched called "xserver"?

---

### Post by rb0171610 on 2009-11-17
> **Mint Sharpie said:**
> Thank you; so is the file that needs to be patched called "xserver"?
Probably not.  ;)

---

### Post by Mint Sharpie on 2009-11-17
How do I find out which one it is?

---

### Post by rb0171610 on 2009-11-17
> **Mint Sharpie said:**
> How do I find out which one it is?
Let me read through your original post links quickly and see if I can tell you.

---

### Post by inigopete on 2010-01-09
Bump - I found this thread through a search (thought I'd better do that before posting my own "I can't work this out either" thread!) and I could also really do with a step-by-step idiot guide on how and what to patch and where I'm likely to find it.

Thanks!

---

### Post by guybryant on 2010-04-09
Hi I had the same thing happen to me. I couldn't figure out how to apply the patch either so I just did what knew how to do, update.  I typed sudo apt-get update into my terminal and then installed all the updates.  After I did that and restarted my computer the error went away and hasn't come back.

---

