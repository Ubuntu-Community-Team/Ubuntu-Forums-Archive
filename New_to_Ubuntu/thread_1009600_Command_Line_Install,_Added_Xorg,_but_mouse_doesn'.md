---
title: "Command Line Install, Added Xorg, but mouse doesn't work."
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Warpnow on 2008-12-12
I did a command line install of ubuntu and added xorg andfvwm-crystal on my Acer Aspire One netbook, but the mouse won't work.

It works on a default ubuntu install, what would make it not work?

---

### Post by kerry_s on 2008-12-12
is the xorg.conf empty?
if so, in terminal:
[B]sudo su
Xorg -configure
cat xorg.conf.new > /etc/X11/xorg.conf
[/B]

---

### Post by Warpnow on 2008-12-12
Okay, I thought for sure that would work, as when I do Xorg -configure it tells me: Xorg detected your mouse at device /dev/input/mice. Please check your config if the mouse is still not operational, as by default Xorg tries to autodetect the protocal.

The cat command you gave didn't seem to do anything, so I did:

cp xorg.conf.new /etc/X11/xorg.con

Booted up, but still have the same problem...

Did I do something wrong? The xorg.conf in /etc/X11/ now has data in it which seems to list a mouse, but it just doesn't work...

---

### Post by Warpnow on 2008-12-12
Haha, when checking to see (earlier) if the mouse had been turned off via hardware, thinking I was turning it on, I turned it off.

Now that it works so I can tell the difference between off and on I was able to turn it back on.

Thank you SO much.

---

