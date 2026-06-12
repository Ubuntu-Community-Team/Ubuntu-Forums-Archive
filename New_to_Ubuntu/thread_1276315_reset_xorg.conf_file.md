---
title: "reset xorg.conf file"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by k33bz on 2009-09-26
I got a different computer for my son, used same HDD, boots up still with out messing with the MBR. Thankfully, lol.

Anyway, the xorg.conf file is still listing an s3 video card. Which the video card in there is not an s3. It was in the previous tower. So how can I reset this file where it will use the right driver for the right device.

The card that is in there right now is an ATI Rage.


If that card is not compatible I have several other cards that may work, but regardless I will still need to reset the conf file.

---

### Post by yeats on 2009-09-26
This can be done by booting into recovery mode and selecting "fix x server" (or whatever the actual wording is).  You can also do this from the command line:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

which will automatically generate an xorg.conf file while backing up the current one.

---

### Post by k33bz on 2009-09-27
Actually I did try that command, however it did not work for me. 

I did find something that did work, actually two different things. One if you had a back up, use the back up. Well I didnt have one. Should of made a back-up, I usually do.

The other thing I found out you can do is delete the xorg.conf file. Then restarting the X session with startx. Doing this will create a brand new xorg.conf file with the absence of not having one.

---

### Post by baldwindc on 2012-09-29
I found one solution that works %100. 

If you're using a desktop, make sure the screen is plugged in. I use dvi and it was partially sticking out. Xserver couldn't recognize and halted on an internal error. I plugged the cable all the way in and it loads fine.

---

