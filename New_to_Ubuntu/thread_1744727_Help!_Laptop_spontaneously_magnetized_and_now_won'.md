---
title: "Help! Laptop spontaneously magnetized and now won't boot from live usb????"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by xpaperbackwriterx on 2011-04-30
So, I was in the middle of installing ubuntu 11.04 instead of my vista+ubuntu 10.10 dual booting system. Ubi-timezone failed the first time, so I was going to try again with the third-party boxes unchecked.  But then I had to go to a church thing, and my laptop spent a night in my mother's car, sad and empty of an OS. And now it will not boot from my liveusb. HELP! D:

I have a Dell Inspiron 1525.

Look down for new info

---

### Post by xpaperbackwriterx on 2011-04-30
Making new live usb and hoping it helps. :\

---

### Post by xpaperbackwriterx on 2011-04-30
made new live usb on my windows computer. Now it at least respons to it, but all I get is:
SYSLINUX 4.01 debian-20100714 EDD Copyright (C) 1994-2010 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot: _

What does this mean and what do I do?

---

### Post by KL_72_TR on 2011-04-30
> **xpaperbackwriterx said:**
> So, I was in the middle of installing ubuntu 11.04 instead of my vista+ubuntu 10.10 dual booting system. Ubi-timezone failed the first time, so I was going to try again with the third-party boxes unchecked.  But then I had to go to a church thing, and my laptop spent a night in my mother's car, sad and empty of an OS. When I tried to try again this morning, I noticed that the top lefthand corner, just above my screen, has spontaneously magnetized and now metal things stick to it.  And now it will not boot from my liveusb (which was also in my mother's car). HELP! D:

I have a Dell Inspiron 1525.
   	 	 	 	p { margin-bottom: 0.08in; }  It is not magnetized, it is electrostaticity. And usually that happened only in the surface of an object.
 So let's hope this is the case. To discharge it is simple: take off the battery and touch it with something metallic.
 But it is unknown if any component of the laptops hardware has been affected.
 I don't think this is the case at all. The problem must be something else.

---

### Post by xpaperbackwriterx on 2011-04-30
Okay. :\ then I wonder what it is?

Taking off battery...touching to something metallic....didnt help but its probably not the issue anyways.

---

### Post by xpaperbackwriterx on 2011-04-30
I'm also downloading the .iso image so I can make a CD and try it, to make sure it isn't a problem with my USB being weird.

---

### Post by oldfred on 2011-04-30
Depending on what version of syslinux you used, it may have one of these (now older) bugs.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"

---

### Post by xpaperbackwriterx on 2011-04-30
So if I *do* have one of those bugs what do I do? I created my first live USB on maverick, then the second on Windows 7.

On a side note, the liveCD thing is not going to work out because disc image burner on my desktop decided to fail. And it's windows so I have absolutely no idea how to fix it.

---

### Post by oldfred on 2011-04-30
See the bug reports for work arounds. My comments are real short versions of the workarounds required i.e. help then enter or edit out UI in syslinux.cfg.

---

