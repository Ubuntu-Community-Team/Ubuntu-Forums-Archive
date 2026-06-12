---
title: "Oh dear. Updates installed, now 10.04 is FUBAR."
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Zappanale on 2010-06-22
I seem to have come a cropper.
My laptop dual boots W7 (which I am using now) and Ubuntu 10.04. Earlier today, Update manager installed some new packages, but now, upon loading ubuntu, the purple loading screen appears as normal, after which the screen goes black and does nothing. No log on screen, etc. 
Fortunatly, I have backups of just about all the important stuff, although I'd rather not do anything that involves losing data unless it's necessary.

Any ideas on getting ubuntu workign again? Thanks.

---

### Post by Dougie187 on 2010-06-22
Does anything come up on the screen?

What graphics card do you have? If you have a discrete card, did you install the proprietary drivers prior to installing these updates? I don't remember which updates were installed, but if it was a new kernel and you were using proprietary graphics drivers then you have to reinstall them using a terminal.

---

### Post by Zappanale on 2010-06-22
No, nothing appears at all. No log in screen, nothing at all but pure darkness. This means I can't access the terminal either.
My grapics card is an ATI Mobility Radeon HD 3400. And I have recently installed their proprietry drivers, as I was having problems otherwise. 
Thanks.

---

### Post by Dougie187 on 2010-06-22
When you get to the black screen, can you try pressing ```
CTRL+ALT+F1
```

See if that gets you to a terminal.

---

### Post by Zappanale on 2010-06-22
Sadly, nothing. The screen simply stays black.

Thanks anyway. I'm glad most of the important stuff is backed up now...

---

### Post by TRoe on 2010-06-22
Did you install your ATI driver by hand? If so, I seem to recall that certain updates could break your configuration and you then have to reinstall the driver by hand.

---

### Post by Zappanale on 2010-06-22
Well, I did it through the terminal... is that what you mean by hand?

The problem is, since nothing, even a terminal comes up, I have no way of installing any drivers =(

---

### Post by philinux on 2010-06-22
> **Zappanale said:**
> Well, I did it through the terminal... is that what you mean by hand?

The problem is, since nothing, even a terminal comes up, I have no way of installing any drivers =(

Can you get into recovery mode from grub. If grub menu not appearing it means there's only one OS on the system. You need to press the Shift key right after the bios post.

---

### Post by Zappanale on 2010-06-22
Well, I can access recovery mode, the only trouble is, after that my knowledge of linux fails me. I am, after all, a beginner.

But, if it helps, recovery mode seems to work.

---

### Post by olbrannon on 2010-06-22
> **Zappanale said:**
> Well, I can access recovery mode, the only trouble is, after that my knowledge of linux fails me. I am, after all, a beginner.

But, if it helps, recovery mode seems to work.

Had a similar issue with ati 3300 driver purple to black then just freezes...nothing.

Here is how I fixed it. Found in forums and searches. When purple screen comes up hit <TAB> key - should have a grub menu Hit the 'e' key and add 'nomce' to the end of the second line. Mine booted normally and I had to edit a menu.lst file iirc to fix it permanently. YMMV Good luck

---

### Post by -humanaut- on 2010-06-22
The new kernel 2.6.**-23 killed my Xorg you need to adjust your grub to so you can log into the older kernel if you have a proprietary video card if you can get to a terminal type

sudo nano /etc/default/grub

and heres how mine looks just copy the bold part[B]
GRUB_DEFAULT=5
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10[/B]

after you adjust it then run

sudo update-grub

and reboot when it goes to a black screen hit escape and choose your last good kernel.

---

