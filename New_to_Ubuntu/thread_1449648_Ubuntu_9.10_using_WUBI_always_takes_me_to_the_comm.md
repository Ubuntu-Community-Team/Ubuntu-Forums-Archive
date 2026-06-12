---
title: "Ubuntu 9.10 using WUBI always takes me to the command prompt"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Jeff.Smith on 2010-04-08
SO, I've installed Ubuntu 9.10 using WUBI on my ASUS UL30A-X5 and after the installation finishes within windows and I reboot it takes me to the ubuntu installation screen where the installation is completed. All of this works fine. Then once ubuntu reboots after completing it's ubuntu installation it takes me to DOS looking screen with a command prompt instead of loading into ubuntu. I'm no good with commands and don't really know what to do from here. I've tried reinstalling it but that doesn't work I get the same result. Is this a hardware problem or is there something I can do to get to the regular graphical ubuntu?

Thanks,
Jeff

---

### Post by lisati on 2010-04-08
Does it ask for your username? If so, try logging in, and entering the command:```
startx
```
Let us know how you get on.

---

### Post by Jeff.Smith on 2010-04-08
No it doesn't ask for anything. It just says I can press tab for a list of commands, gives a version number for the grub (whatever that is) which is like 1.97beta an then just gives me a command prompt. I think it says sh bash or something similar behind the cursor.

---

### Post by lisati on 2010-04-08
OK. It looks like "grub" has been messed up. I'm not sure how to proceed, but there seem to be a number of threads relating to similar problems.

---

### Post by Jeff.Smith on 2010-04-08
I'll do a search of previous threads then, and if there are questions from that point on, I'll repost them here. Thanks.

---

### Post by Newt_Othis on 2010-04-08
Hi Jeff,

Try downloading this updated wubildr file:

[http://launchpadlibrarian.net/36920146/wubildr](http://launchpadlibrarian.net/36920146/wubildr)

copy it to root of your C drive in Windows - (Assuming that's your system partition).

Worked a treat for me after doing a fresh Wubi install this morning.

Newt

---

### Post by 3rdalbum on 2010-04-08
Try booting up the Ubuntu CD and installing it that way, rather than using Wubi.

---

