---
title: "Ubuntu Boot Screen"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by t.schnabel on 2011-01-19
Hey i'm new to Ubuntu so i dont know what i did, but whenever i boot into ubuntu (i have a windows 7 partition) the logo and 5 dots do not show that it is loading. it still runs fine, i just liked seeing that screen. if someone can help me out it would be greatly appreciated.

---

### Post by theozzlives on 2011-01-19
It depends on your video. I have one machine that don't do Plymouth and one that only does it most of the time.

---

### Post by smurphy_it on 2011-01-19
Yup that could be one cause.  Other cause is it could have the quiet splash removed or commented out from /boot/grub/grub.cfg

Top of that file will tell you some steps to go about to have that put back in.

Careful messing with grub though, as it can make your system un-bootable.

---

### Post by psycho5 on 2011-01-20
If you're using ATI or NVIDIA cards and you installed the "additional hardware" for using 3d effects and such, then there is a fix for the boot screen, just follow this link:

[http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/comment-page-1/#comment-43661](http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/comment-page-1/#comment-43661)

---

