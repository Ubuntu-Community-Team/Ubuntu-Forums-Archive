---
title: "Can't set proper display resolution in Karmic"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by captgadget on 2009-10-31
I've read several posts but it appears there is not a clear cut answer to the resolution problems. I have an Intel 865G chip and when I go to system>preferences>display it tells me the monitor is unknown and I have only two choices for display settings:800X600 or 640x480. It's a LCD 19" monitor and worked perfectly fine in Jaunty. Some posts say to change the Grub settings and some say add some info to Xorg but others say Xorg no longer exists. I'm baffled.

thanks is advance

---

### Post by trulan on 2009-10-31
I can't help you with your intel chip but I can try to clear up the confusion about xorg.conf.  

xorg.conf no longer exists by default.  X will automatically configure itself without it.  However, if xorg.conf is present, X will use the settings stored in it.  So if you know how to edit xorg.conf to your liking, go ahead and do it. I think running xorg-configure as root will generate a basic xorg-conf, just like you had in Jaunty.

But I would think it should work out-of-the-box, especially on an Intel chip.  So I don't know...

---

