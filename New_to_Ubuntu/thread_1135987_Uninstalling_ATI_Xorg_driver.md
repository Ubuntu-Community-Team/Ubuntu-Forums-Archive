---
title: "Uninstalling ATI Xorg driver"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Mario Fanelli on 2009-04-24
I've a Compaq 6715s laptop PC with the ATI Radeon X1250 onboard video card (this is what the HP official documentation and Windows XP driver says). I've installed Ubuntu 9.04 AMD64 without problems. I've installed the propetary driver for the Broadcom wireless card and all feel good. Only a flickering video problem. I've installed the ATI Xorg driver using the add/remove software manager. The procedure don't have problems. When I reboot the PC, the video displays coloured bars and the system in freeze.

How is the procedure for uninstalling the ati xorg driver and restore the installation one without reinstall Ubuntu?

Thanks for the help. Bye, Mario.

---

### Post by cariboo on 2009-04-24
Start you computer in recovery mode, press esc when you see the grub menu and select recovery. At the menu select drop to root prompt and type:

```
dpkg-reconfigure -phigh xserver-xorg
```

The above command will reset /etc/X11/xorg.conf back to the defaults, one finished type exit, then select resume. This should get you back to a useable desktop.

---

### Post by Mario Fanelli on 2009-04-25
Thanks for the help Cariboo, I try but the PC freezing again.

---

### Post by abzman2000 on 2009-04-25
I have this exact same problem, by doing the exact same thing the xorg file is very short and contains almost no information compared to what it used to , I already tried the dpkg thing.  what is the package that coresponds to the ati x.org driver so I can apt-get remove the thing

---

### Post by peakshysteria on 2009-04-25
Have you tried to uninstall it via Add/remove since you originally installed from Add/remove? If this doesn't do the trick, severalthreads in the forums mentions other methods. Markbuntu have earlier helped me with Ati troubles. His recommendation seems to be;

> You need to run the uninstaller script usr/share/ati/fglrx-uninstall.sh

Similar threads/similar problems mentioned:

[http://ubuntuforums.org/showthread.php?p=6930367](http://ubuntuforums.org/showthread.php?p=6930367)

[http://ubuntuforums.org/showthread.php?t=1056539](http://ubuntuforums.org/showthread.php?t=1056539)

[http://georgia.ubuntuforums.org/showthread.php?t=1108415&page=4](http://georgia.ubuntuforums.org/showthread.php?t=1108415&page=4)

---

### Post by Mario Fanelli on 2009-04-29
I can't use the add/remove wizard because the PC freezing before.
Thanks for the trick.
When I can, I reproduce the crash and I will try to solve it. In these days I'm waiting for two twins and I don't have time for the PC.

Thanks, Bye!:KS:KS

---

