---
title: "Bootsplash screen takes for ever to appear after upgrading to 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by diablo75 on 2010-05-01
I just upgraded to 10.04 and have a little problem with the boot splash screen.  Before upgrading, it would appear within a couple seconds after GRUB went away and remain without flickering or anything like that until the system was fully loaded.

Now, when it boots, it's a solid black screen with a blinking cursor in the upper left corner and it stays that was for probably 10 or 15 seconds while the hard drive is busy loading a bunch of stuff.  It eventually appears, but only for a few seconds with a little bit of flickering and then the desktop shows up after that.

On the side I was wondering if anyone knows how to force this bootsplash screen to show up at a different screen resolution.  It almost looks like it's loading it at 640x480 or lower for compatibility purposes, even though my video card has 768 MB of RAM (nVidia GeForce 9600).

---

### Post by WorMzy on 2010-05-01
Plymouth (new boot splash program) doesn't play well with propriety drivers. So if you've installed them, your splash screen will be hideous. Removing them fixes the problem, but disables compiz effects. AFAIK, there is no solution for this.

---

### Post by xumuk37 on 2010-05-01
yet... Hi there! I have same problem (ugly low resolution at boot). Tried to fix it adding vga parameter to kernel in grub, but this makes it worse: color pixels instead of letters. Somebody has any idea how to fix it?

---

### Post by teh603 on 2010-05-01
Having been one of the testers from alpha 3, I must say that you're lucky if Plymouth appears at all. Some of us still can't get it to appear, and others only see it on shutdown. And that's with open source drivers, too.

Plymouth just doesn't play well with anything, proprietary or otherwise.

---

### Post by xumuk37 on 2010-05-01
I would agree with you if I haven't see [COLOR="Blue"][this]("http://www.youtube.com/watch?v=qaSg2rRj4HQ")[/COLOR]

---

### Post by diablo75 on 2010-05-01
Darn.  Is there a timeline out there that projects the devs doing anything to remedy this?  It's just sad that I upgraded to a version of Ubuntu that makes the system look "sloppy".

---

### Post by WorMzy on 2010-05-01
> **xumuk37 said:**
> yet... Hi there! I have same problem (ugly low resolution at boot). Tried to fix it adding vga parameter to kernel in grub, but this makes it worse: color pixels instead of letters. Somebody has any idea how to fix it?

I tried vga codes too, and got the same result as you. Now I've just disabled splash in grub, reams of text looks better that what plymouth looks like at the minute.

---

