---
title: "Need help with monitor resolution"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by Tokyo Joe on 2010-01-30
I installed Ubuntu today and really like it so far, except the System Display Preferences doesn't list the resolution I need.  800x600 is the highest but the Native/Optimum                    Resolution for my monitor is                  1400                    x 1050.  My graphics chip is integrated Intel 82845G/GL.  I downloaded from the Intel site what I thought was the correct driver but the Administration/Hardware Drivers function doesn't recognize any "Proprietary Drivers".  Appreciate any help so I can fully enjoy my new OS.  Thanks!

Joe

---

### Post by DTM84 on 2010-01-30
I've been facing a similar problem with finding the correct ATI propriatary drivers on my system. 

A solution that might work for you is reconfiguring xorg to allow for other resolutions. 

This solution asumes that you have the right driver though. If you don't, you might not be able to get the resolutions you input into xorg to work.

You can look up how to reconfig xorg in the forums, but I'd probably hold off till you get a few more responses.

---

### Post by Pikestaff on 2010-01-30
If you haven't yet tried reconfiguring xorg... the command is:

```
sudo dpkg-reconfigure xserver-xorg
```

Which will allow you to tweak your settings a bit.  You might want to backup your original xorg.conf first, just in case:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

