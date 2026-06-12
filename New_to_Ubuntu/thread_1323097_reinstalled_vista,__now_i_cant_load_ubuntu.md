---
title: "reinstalled vista,  now i cant load ubuntu"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by copracr on 2009-11-11
how do i get my menu back that asks if i want to start vista or ubuntu? 

 i formatted my c: to get rid of a bad xp instalation and could only find a vista disc so i loaded that.   Now i have no option to load linux.  Linux is on a second hdd and it looks untouched when i explore with the live cd.

---

### Post by bradleypariah on 2009-11-11
You need to re-install GRUB.  Windows isn't friendly to Linux' boot process.

Check this out:

[http://www.youtube.com/user/NixiePixel#p/u/38/WtBBl6HvdpM](http://www.youtube.com/user/NixiePixel#p/u/38/WtBBl6HvdpM)

Nixie Pixel is an attractive Nerd woman that roams these forums and posts tutorials youtube.  This will make it easy.  Enjoy!  :-D

---

### Post by copracr on 2009-11-11
I should of stated Im using karmic koala and that video said not for KK.  You're right though,  that chick is attractive.

---

### Post by bradleypariah on 2009-11-11
Rough...

Here's a 4-year-old post that is still being posted on to this day about the subject:

[http://ubuntuforums.org/showthread.php?t=24113&page=23](http://ubuntuforums.org/showthread.php?t=24113&page=23)

---

### Post by Zoot7 on 2009-11-11
Here's instructions to re-install GRUB 2 to the MBR:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
That should get Ubuntu up and running again. You also might need to run sudo update-grub to have grub 2 detect Vista.

Sadly it's not as simple as the old 3 commands that used to do it with GRUB legacy.

---

