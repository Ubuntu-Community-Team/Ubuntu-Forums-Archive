---
title: "video card drivers"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by blairm on 2008-12-07
Hi,

Have recently bought a new computer with Vista 64 (wanted it for gaming) and I want to dual boot Ubuntu with it.
Completely new to 64-bit world so a couple of questions...
- Can I run a 32 bit Ubuntu and a Vista 64 on the same machine? (have a copy of Gutsy)
- See AMD has linux drivers for my video card (HD4850) and have read those are better than the open source ones; should I be downloading the 32 bit or 64 bit driver?
- Resolution on the live CD won't go to my monitor's native resolution - will the Video driver fix that?

And finally, am I able to test these things on the live cd to make sure it all works before installing.

Thanks,

Blair

---

### Post by linux_tech on 2008-12-07
> Hi,

Have recently bought a new computer with Vista 64 (wanted it for gaming) and I want to dual boot Ubuntu with it.
Completely new to 64-bit world so a couple of questions...
- Can I run a 32 bit Ubuntu and a Vista 64 on the same machine? (have a copy of Gutsy)  Yes but its easier to have Vista installed 1st, then install ubuntu.  How to apcguides cover dual boot install quite well-
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

 Tell us more about your hardware.  ```
sudo lshw | less
``````
sudo lshw -C video
```
If you have 32 bit hardware then you should run 32-bit ubuntu; if you have 64 bit hardware then you should run 64-bit ubuntu.

>  See AMD has linux drivers for my video card (HD4850) and have read those are better than the open source ones; should I be downloading the 32 bit or 64 bit driver?  
more on HD4850 here- [http://ubuntuforums.org/showthread.php?t=961861](http://ubuntuforums.org/showthread.php?t=961861)
>  Resolution on the live CD won't go to my monitor's native resolution - will the Video driver fix that?
What resolutions are available under current driver and which are you using?
```
 xrandr
```


>  And finally, am I able to test these things on the live cd to make sure it all works before installing.   Running the live cd will give you some 
indication.  Go for it. 

Thanks,

Blair[/QUOTE]

---

### Post by sayems on 2008-12-07
-Yes, you can run Ubuntu 32-bit on 64-machine. but I highly recommend you to install Ubuntu 8.10 instead of Gusty. Gusty might not work with your graphics card.

-You can activate Proprietary FGGLRX graphics driver, It will automaticly install all the latest driver for your ATI Radeon HD 4870.

---

### Post by binbash on 2008-12-07
yes to all ,for 4850 read this [http://www.phoronix.com/forums/showpost.php?p=48886&postcount=10](http://www.phoronix.com/forums/showpost.php?p=48886&postcount=10)

---

### Post by blairm on 2008-12-07
Thanks for your help everyone.

Played round a bit and finally got the driver installed - to be honest, I'm not sure how I did it, but I think I used instructions from the unoffical ATI linux wiki. (was exhausted by the time I sorted it out and I must have tried half a dozen methods!)

Cheers,

Blair

---

