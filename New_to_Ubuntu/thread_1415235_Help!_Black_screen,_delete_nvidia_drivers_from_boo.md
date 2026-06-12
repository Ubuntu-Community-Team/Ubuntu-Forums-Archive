---
title: "Help! Black screen, delete nvidia drivers from boot?"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by andreuther on 2010-02-24
Where to begin?

I just downloaded ubuntu 9.10 as a duel os with Windows 7 and I have a NVIDIA GEFORCE G210m graphics card.
I downloaded the 190.42 driver from nvidia.
When I went to the nvidia settings it told me that x server wasn't working and that i had to run xorg-config or something like that, and then restart x server. I did all of this. 
I also played around with compiz.

When i restarted and choose umbuntu it goes to the black screen.
I can get into safe mode.

 just want to save my openoffice.org files! 

is there any way to just delete all changes i made?

when I go to nano there is no list with nvidia in it, there isn't a list at all.

Thanks for the help in advance!

---

### Post by Greenwidth on 2010-02-24
At the command prompt type:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
and reboot.

The above renames the settings for the x server so that it is not loaded at boot but configures 'on the fly' - which should bring you back to where you were before, ie no Nvidia driver.

I had this trouble with my desktop which was fixed by using the 195(beta) driver:
[http://www.nvidia.co.uk/object/linux_display_ia32_195.30_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_195.30_uk.html)

However, looking through the info, I do not the 210M listed in any of the newer driver 'supported products'..

Maybe someone with the same card could help you further.

---

