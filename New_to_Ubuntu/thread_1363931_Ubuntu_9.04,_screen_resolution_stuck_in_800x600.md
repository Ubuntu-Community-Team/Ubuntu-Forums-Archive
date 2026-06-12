---
title: "Ubuntu 9.04, screen resolution stuck in 800x600"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by cormocodran on 2009-12-25
Hi,
I'm new to ubuntu and currently the monitor I'm using cannot display resolution higher than 800x600. The manual of the monitor mentioned that it supports resolution up to 1280x1024. I followed the the suggestion in [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)  but the problem is still not resolved. 
These are the steps that I did
```
cvt 1280 1024
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --output default --mode 1280x1024_60.00
```the last command give 
```
xrandr: Configure crtc 0 failed
```and there's no change in resolution.
However,  I noticed that the resolution option in Display Preferences now listing 1280x1024, but when i tried to apply that, it gives an error message, saying 

"could not set the configuration for CRTC 98"

Can anyone help me?

---

### Post by clhsharky on 2009-12-25
HI

What video chip do you have? And did you install drivers?

Sharky

---

### Post by gs777 on 2009-12-25
Are u using intel a video card? If yes u will have to install its legacy drivers .Try [this link.]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by cormocodran on 2010-01-02
gs777 and clhsharky,
Thanks for responding! But after I left  my computer for a week (new year holiday here is for a week anyway), I rebooted my computer and now the new, higher resolution works. I don't know how that happened, but I really can't complain anymore.

---

