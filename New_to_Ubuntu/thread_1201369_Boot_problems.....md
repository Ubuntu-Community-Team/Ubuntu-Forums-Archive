---
title: "Boot problems...."
date: 2009-07-01
forum: New to Ubuntu
---

### Post by bell2jd on 2009-07-01
Okay, so here's my problem. I'm going to explain it, but it might seem like kind of a roundabout way of doing it.

For a long time, I've had this problem. When I start up my computer, (It's a Dell Inspiron 1520 with Jaunty on it, but I had this problem before I updated from 8.10) sometimes it doesn't boot. sometimes it boots fine, but other times it doesn't boot coorrectly. when it hangs it always hangs at about the same spot. most of the time it's on "Starting Hardware abstraction layer hald", but sometimes it hangs on "Starting Bluetooth" (which by the way, my computer does not have, but that doesn't seem to be a problem most of the time, just occasionally), and sometimes it hangs on "Starting GNOME Display Manager". The real problem is that it is intermittent. This boot hangup only happens some of the time, but when it does, nothing will happen. Once it hangs, I get a message that says "wait for START_ALIVE timeout after 2000 ms", and then nothing. it just sits forever, and every 61 seconds it tells me that CPU#0 has been stuck for 61 seconds.

So, to sum it up:
Dell, Inspiron 1520, Ubuntu 9.04 (but it was a problem with 8.10 also)
Hangs on boot
Intermittent, it only happens sometimes, though usually a number of times in a row before it starts working right.
doesn't always hang on the same thing
most of the time it's the HAL, but it can also be bluetooth or even GDM.

Things I've tries to fix it:
I've reeinstalled HAL, but that didn't seem to fix it. other than that, I was afraid I would screw things up worse.

Thanks in advance for any ideas anyone might have.

James

---

### Post by nhasian on 2009-07-01
have you tried a fresh install?  can you try the ramtest on the liveCD?  also download the hard disk diagnostic tools from your HD manufacturer and run a hard disk test.  Finally check to make sure all the fans in your computer are functioning properly and your equipment is not overheating.

---

