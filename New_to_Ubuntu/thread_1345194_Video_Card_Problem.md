---
title: "Video Card Problem"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Cooter2543 on 2009-12-03
I am trying to figure out what exactly my brother did to his computer, and myself not being an expert at Ubuntu, I am having some trouble.

Ubuntu 9.10 / Windows XP SP2
P4 @ 2.4 GHz
1GB DDR

The computer had a GeForce 5600XT in it. Somehow the screen started going black shortly after he booted it. So he took out the video card, and plugged the monitor to the integrated video, thinking that would solve the problem. Of course, it didn't, and then he called me up.

So here I am. When I boot the computer (with the integrated video), it loads GRUB fine, and will boot Windoze with no problem. But when I try to boot Ubuntu, a window pops up saying it is in low graphics mode, and that I need to reconfigure the monitor, video card, and drivers. I tried the selection to create a new display configuration and reboot, with no difference. I've tried to boot the restore mode and repair broken packages, but it finds no problems.

I'm guessing that Ubuntu still thinks that it's supposed to be using the GeForce card. Well, I plugged it back in, and the screen is completely black. It doesn't even show the BIOS screen. 

So how do I properly downgrade back to the integrated graphics?

---

### Post by jbrown96 on 2009-12-03
you probably need to remove the display configuration file, then repair the packages. boot into recovery mode and choose "root shell." Run the following command ```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.back
``` This won't delete (in case you need the file again in the future), but will instead rename it, so it won't load.

Then repair the display package. ```
dpkg-reconfigure xserver-xorg
``` This will walk you through a few screens. If you have a US keyboard layout, then you don't need to change anything. Just press enter to get through the screens. 

Try the xserver. ```
startx
``` This should get you into graphical mode. It may still complain about low graphics, but you should be able to change the resolution. Once you get that set, reboot. There may not be an option to reboot; instead, you may only be able to logout (this is because we manually started graphical mode); logout, which will take you back to the terminal, then ```
reboot
```

---

### Post by Cooter2543 on 2009-12-04
Thanks, it worked!
You guys are geniuses on this forum.

---

