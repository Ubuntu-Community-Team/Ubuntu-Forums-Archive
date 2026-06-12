---
title: "Error: No Suitable Mode Found Error: Unknown Command:&quot;Terminal&quot;."
date: 2010-07-12
forum: New to Ubuntu
---

### Post by jless on 2010-07-12
Just did a clean install of Ubuntu 10.04 on a Dell  Dimension 2100 Xp.
 It worked great but I'm  getting the following error messages at boot  up:
 
    Error: No Suitable Mode Found
    Error: Unknown Command:"Terminal".

It hangs there for about a minute then it continues booting OK.
I have Intel 82810 (CGC) Graphic Controller.

Please  let me know what I shoul do to fix this.

    Thanks

---

### Post by hdoan48 on 2010-10-17
> **jless said:**
> Just did a clean install of Ubuntu 10.04 on a Dell  Dimension 2100 Xp.
 It worked great but I'm  getting the following error messages at boot  up:
 
    Error: No Suitable Mode Found
    Error: Unknown Command:"Terminal".

It hangs there for about a minute then it continues booting OK.
I have Intel 82810 (CGC) Graphic Controller.

Please  let me know what I shoul do to fix this.

    Thanks

I have the same problem. It's just an annoyance because after the display of the messages, the system continues to boot and everything after is working fine for me. I have an old Compaq Deskpro EN with the Intel 82815 Graphics Controller and a Samsung Syncmaster 216BW with a native resolution of 1680x1050.
I have done so many suggestions found on this forum (modify /etc/default/grub, Xorg -configure, etc) to get rid of these 2 messages but nothing seems to work.

---

### Post by WanderingAlbatross on 2010-10-17
This is not related to X.org because it happens near the beginning of grub loading.  This is far before X comes along.  I have the same problem.  It is new since we tried to put a splash screen on the grub menu.  We have the infamous Intel 855 graphics card.  Sounds like an adventure.

---

### Post by WanderingAlbatross on 2010-11-01
The problem is that the Grub loader is trying to use a splash screen.  For some reason your computer is not agreeing with using graphics this early.  You should make sure it sticks to text.

[http://ubuntuforums.org/showthread.php?t=1501143&page=2](http://ubuntuforums.org/showthread.php?t=1501143&page=2)

At least this was our problem.  If you try this and it works, please mark this Thread as solved.

---

### Post by ayenack on 2010-11-01
Cool tag line WanderingAlbatross... wish I'd thought of that. LOL.

---

### Post by WanderingAlbatross on 2010-11-16
Hey bro,

It's open source.  You can use it if you want.  I am glad to help.

---

