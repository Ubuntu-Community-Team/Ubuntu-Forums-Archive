---
title: "Problem, Flash on 64-bit sytem."
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Solaris242 on 2011-02-17
Hey, sorry about this, I know it has been posted before a lot of times, but I've searched through just about every last post with no luck.

About 2 months ago (for the first time), I switched to Ubuntu 10.10, Maverick Meerkat from XP.  I love it.

Flash worked fine for me originally, but about a week ago it stopped.  Nothing involving it plays.

I looked into flash square (after finding about the troubles 64 bit systems have with 32 bit flash) but I cannot get it to install.  

The terminal commands from half a dozen sites have done nothing.

I know a little, but not much about computers (I mean about their core workings, especially Linux).  Pretty much a nothing+2 in terms of knowledge.

I love Ubuntu, and what I love about it most is that when a problem occurs, you can fix it.  I just can't figure this one out.

Help?

---

### Post by kerry_s on 2011-02-17
for all media, just install "ubuntu-restricted-extras" & you won't have to worry, it will install flash & keep it up-to-date.

---

### Post by Solaris242 on 2011-02-17
Just looked, in that section I have nothing between ubuntu-mono and ubuntu-sounds.

---

### Post by Solaris242 on 2011-02-17
Okay, now have something working (found instructions on how to force Firefox to find the libflashplayer.so file).

It works, but not with trouble.  Still, better than it has been for a while.

---

### Post by kerry_s on 2011-02-17
> **Solaris242 said:**
> Just looked, in that section I have nothing between ubuntu-mono and ubuntu-sounds.

sounds like you don't have all the repo's on.

---

### Post by cascade9 on 2011-02-17
If your running 64-bit, you really dont want the flash version from the repos (its 32-bit in a wrapper, and that is....er...crap). 

Try flash-aid- 

[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)

[http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)

---

### Post by Kirboosy on 2011-02-17
+1 Flash aid is very good. I use it on my 64 bit system flawlessly. :)

---

### Post by Cracklepop on 2011-02-18
If for some reason you don't like FlashAid, you can do what it does manually:
 - download this .zip then rightclick it to extract the .so it contains: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)
 - put the .so in ~/.mozilla/plugins (show hidden files in the View menu, create the plugins folder if necessary)

---

