---
title: "How do I know if my TV is supported by Ubuntu"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by kafka201 on 2009-12-19
The title kind of says it all.  My mom's TV is an Olevia and when I plug the VGA cable in and hit the key to switch outputs the TV says "Not supported" or something like that.  I'm headed to my dad's for the holidays and was wondering if there was a way to tell ahead of time if it was supported.  He has a Sharp TV if that matters.
Thanks

---

### Post by 3rdalbum on 2009-12-19
"Not Supported" is a reference to the resolution that Ubuntu is using, not to Ubuntu itself.

I believe you need to boot up the computer with the TV on and with the VGA cable plugged in already. When Ubuntu's X server starts up, it will see the TV through the VGA cable and query it for what resolutions it supports. When it recieves the answer, it will make sure that X uses the TV's native resolution. It only does this on startup, not afterward.

Also make sure that your VGA cable is working properly.

In short, every kind of screen output device that can plug into VGA is supported with Ubuntu.

---

### Post by Dark_Stang on 2009-12-19
For the most part, a monitor is a monitor. Did you try to logout then log back in after hooking up the monitor?

---

### Post by kafka201 on 2009-12-20
Ah, thanks, I'll give that a shot as soon as she finishes watching.

---

