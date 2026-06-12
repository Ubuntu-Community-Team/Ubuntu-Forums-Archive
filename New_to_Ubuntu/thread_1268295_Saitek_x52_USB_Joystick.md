---
title: "Saitek x52 USB Joystick"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-09-16
The latest kernel does not seem to recognize my Saitek USB joystick. It does see my Saitek Rudder pedals. Anyone else had this issue? Any resolution out there yet?

Thanks Much.

---

### Post by kainalu on 2009-11-16
I just got one in the mail today, and of course, same problem. Ive discovered that the Linux kernel team and Ubuntu bug team know about it. You can manually recompile the kernel to support it, however, Im not going to do all that, and have opted to retrograde back to 8.10 (the last known working out-of-the-box version for this stick) Supposedly 2.6.28-16-generic works, but that isn't a kernel for 9.10 either

[http://ubuntuforums.org/archive/index.php/t-1255083.html](http://ubuntuforums.org/archive/index.php/t-1255083.html)
[http://ubuntuforums.org/showthread.php?t=1264257&highlight=saitek](http://ubuntuforums.org/showthread.php?t=1264257&highlight=saitek)
[http://ubuntuforums.org/showthread.php?t=1327165&highlight=saitek](http://ubuntuforums.org/showthread.php?t=1327165&highlight=saitek)
[http://bugzilla.kernel.org/show_bug.cgi?id=14049](http://bugzilla.kernel.org/show_bug.cgi?id=14049)
[http://forums.x-plane.org/index.php?showtopic=40322&st=20](http://forums.x-plane.org/index.php?showtopic=40322&st=20)
[https://bugs.launchpad.net/ubuntu/+bug/421812](https://bugs.launchpad.net/ubuntu/+bug/421812)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300143)

---

### Post by kainalu on 2009-11-16
I found that by booting Linux-Image-2.6.28-16-generic, the joystick works well, however, I have no sound, no compositing, and a desktop framerate of around 1. When launching the game, that 1 frame per second starts to look reeeeal nice compared to what you get in the game.  It reminds me of installing XP with NortonAV on a pII w/ 64MB and running MSFS2004. 

Maybe your results will differ, so if you want to give it a shot

-go to synaptic and search for Linux-Image-2.6.28-16-generic, if     
  it exsists, install it.  (Mine was left around from prev.   
  version, so no need to install) 

-install it and reboot.

-during reboot, hit escape on grub and choose the 2.6.28 kernel. boot and "enjoy". :mad:

For me, this aint worth it... Back to 8.10 I go!!! hi ho, hi ho!

---

### Post by ncc1701e on 2009-12-19
I just upgraded to the latest Ubuntu 9.10 Karmic Koala. I continue to have trouble getting Ubuntu to see my Saitek x52. Ouput of the 'lsusb' command shows that ubuntu does see it connected to the machine but the software in which i want to use it use it (x-plane 9.31) does not. I did not have such problems in the earlier kernels of 9.04.

In researching the topic apparently it seems someone has found a solution. I stumbled accross it while roaming on the x-plane linux forum:

Please see:

[http://forums.x-plane.org/index.php?showtopic=42109](http://forums.x-plane.org/index.php?showtopic=42109)

I have not yet executed this solution since I do not know anything about how to recompile a kernel but if/when I do it I will report my findings. 

I just thought I'd throw this out there in our community for other having the same trouble. Any guidance on how to recompile a kernel to a newbie would be greatly appreciated. Long live the Ubuntu Nation!

---

