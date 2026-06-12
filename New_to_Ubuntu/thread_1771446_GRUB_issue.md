---
title: "GRUB issue"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by Lash009 on 2011-05-30
So, I have a problem booting which has really confused me. While upgrading 10.10 to 11.04 my computer froze (completely froze; no mouse movement or anything). And when I tried to reboot it (I have it installed on a 16GB flash drive), my computer went straight to booting Windows XP :( . I've tried a bunch of different things and I believe that it is an issue with my boot-loader not always detecting GRUB. When I started my computer with a Live CD (Ubuntu 10.10) and my normal flash drive plugged in, I got a GRUB screen. I tried to run Ubuntu with the first Linux kernel on the list... it froze. I tried to run it with the recovery mode for that kernel... kernel panic. finaly I tried an older kernel and it booted up Ubuntu 11.04 complete with Unity. Unfortunately, I've never been able to do this again; it only happened once. I tried to do this same thing again today (booting with the older kernel) and it froze, I successfully ran recovery mode for that older kernel, and ran the grub recovery thingy, then rebooted. Now I can't seem to even get to grub anymore.
My gut says to try to re-install GRUB, but I figured that I should check with you guys first and see what you think about that idea. I'm a bit confused by the varying results that I'm getting from just trying to run it. 
So what do you think?

---

### Post by cmwatford on 2011-06-02
The only thing I can think of is reinstalling GRUB and then trying to fix your broken packages if you can get to a terminal.
```
sudo dpkg --configure -a
sudo apt-get install -f
```

[Here](https://help.ubuntu.com/community/Grub2#Reinstalling from the LiveCD) is a guide for reinstalling GRUB if you need one.

---

