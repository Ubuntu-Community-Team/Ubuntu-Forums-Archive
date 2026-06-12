---
title: "Is there a way to rotate my monitors video-out 90 degrees?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by diablo75 on 2009-03-24
Lets say I have one of those monitors that can rotate by 90-degrees, giving me a much longer looking monitor instead of wide (common for desktop publishing and document writing).  Someone I know has such a monitor and would like for Ubuntu to have a quick way to toggle back and forth between normal wide-screen video out and rotated long-screen video.  Any ideas on how to do this?  They have an nVidia video card, if that's of any concern.

Thanks in advanced!

---

### Post by kanikilu on 2009-03-24
I don't have a screen that can do this, but a search came up with this:

[http://ubuntuportal.blogspot.com/2007/02/how-to-setup-pivot-screen-rotation-with.html](http://ubuntuportal.blogspot.com/2007/02/how-to-setup-pivot-screen-rotation-with.html)

---

### Post by LowSky on 2009-03-24
this should do it, 

[post #20]("http://ubuntuforums.org/showthread.php?t=301380&page=2")

[Post #26]("http://ubuntuforums.org/showthread.php?t=301380&page=3")

---

### Post by diablo75 on 2009-03-24
> **kanikilu said:**
> I don't have a screen that can do this, but a search came up with this:

[http://ubuntuportal.blogspot.com/2007/02/how-to-setup-pivot-screen-rotation-with.html](http://ubuntuportal.blogspot.com/2007/02/how-to-setup-pivot-screen-rotation-with.html)

I used the above guide to add the:

```
Option          "RandRRotation" "on"
```

To the appropriate spot in my xorg.conf.

However, this did not present a Left or Right rotate option in my screen resoultion settings box.  The only option there was "Upside Down".

In order to rotate the way I want, I've created two shortcuts in my panel, one which executes:

```
xrandr -o left
```

And another that issues the command:

```
xrandr -o normal
```

---

