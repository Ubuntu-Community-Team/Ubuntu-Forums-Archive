---
title: "blank screen when starting desktop"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by doctor15 on 2010-05-31
Hi,

I'm new to linux and am setting up a media pc.  I'm only using it for a few specific purposes and am worried about performance, so I installed a minimal installation of ubuntu server lucid.

From the command line, everything seems to be working fine.  When I try to go in to the desktop however, by entering "startx",  I get an almost completely blank screen except for in the very top left corner it says "<user>@<computer>/etc/X11/xorg.conf []" (I'm not in front of that computer right now, so the path might be slightly off).

Any ideas what would cause this?

I tried disabling KMS and setting up my own xorg.conf but that caused other unrelated problems, so I decided KMS would probably be my best bet.

I'm running Radeon 9800 and have the default open source drivers (I didn't install anything additional).

Is there a step I missed or any additional packages required?  Any pointers in the right direction would be greatly appreciated!

Thanks!

---

### Post by mbzn on 2010-05-31
Hi, and welcome

I would suggest doing a complete install and then remove the unwanted packages, it's probably not the best solution but should get your GUI going.

---

### Post by Paddy Landau on 2010-05-31
If you're worried about performance, then I agree with mbzn's post.

Any program that's installed and *not* running will not affect your performance in any way (unless you have a tiny disk).

If you have an old computer, you can try [Lubuntu]("http://lubuntu.net"). It's a light-weight variation on Ubuntu, hoping for official endorsement by the next release. See some [simple comparisons]("http://www.linux-mag.com/cache/7520/1.html").

---

### Post by doctor15 on 2010-05-31
Thanks for the replies!

I can do that, but I'm still curious what the underlying problem is.  Is that the error I would get if a necessary package is missing?

---

### Post by lrgmmc on 2010-05-31
well i think you still need a window manager. a nice light weight one is icewm can be installed with ```
sudo apt-get install icewm
```
then when you startx you will get a nice enviroment.

---

