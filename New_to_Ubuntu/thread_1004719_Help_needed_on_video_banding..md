---
title: "Help needed on video banding."
date: 2008-12-07
forum: New to Ubuntu
---

### Post by LeeHamo on 2008-12-07
Hi,

I get really bad video slowdown and banding on youtube when im watching videos, it all started after I bought a new lcd monitor, spent days trying to setup resolution, messing with xorg.conf and all such things and ive managed to get my desired resolution but im not happy with this banding issue,

Is it possible ive messed up xorg, would it be an option for me to wipe my xorg and start again cause I assume all the info inside it determins how well my monitor performs?

any help appreciated, if you want me to post any settings please ask and also tell me how to do it.

Thanks in advance.

---

### Post by phidia on 2008-12-07
You don't say what version of ubuntu you're using or what your video card specs are but the problem could be in how flash is installed. Check the multimedia guide [here]("http://ubuntuforums.org/showthread.php?t=766683&highlight=tube").

If it was working fine before the monitor change you can reconfigure your xorg by opening a terminal and entering  > sudo dpkg-reconfigure -phigh xserver-xorg that will back up your present xorg.conf.

---

### Post by LeeHamo on 2008-12-07
Sorry about that,

Im using 8.04 Hardy and my GFX card is nvidia Gforce 7600 GS OC PCi-e.

Ill check the guide.

---

### Post by LeeHamo on 2008-12-07
If I run that reconfigure thing will I have all the bother again setting my screen res and refresh rate? and will I have to do something else once I run that>?

---

### Post by phidia on 2008-12-07
> **LeeHamo said:**
> If I run that reconfigure thing will I have all the bother again setting my screen res and refresh rate? and will I have to do something else once I run that>?

The dpkg command will create a new xorg.conf-you can add to that or revert back to your previous xorg. If the problem is the change in monitor then maybe that will get it working.

---

