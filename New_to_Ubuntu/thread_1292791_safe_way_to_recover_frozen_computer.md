---
title: "safe way to recover frozen computer?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-16
My laptop, while running Ubuntu, just locked up.  I left it on.

tech info:  it locked up/froze when i was listening to a trial of sirius satelite radio online, and testing the trackpad (see my other post minutes ago here) and mouse.  All of a sudden, sirius sound feed stops and unable to move mouse (or trackpad) pointer.

Safest way to get out of this?  Or is just turning the computer off recommended [i doubt that's the best recommendation]

---

### Post by CharlesA on 2009-10-16
I had a similar thing happen when I was streaming a movie from my media server. Ended up having to just hit reset. Couldn't SSH in to do a graceful shutdown. :mad:

I'm curious if there is a better way as well.

---

### Post by aljoriz on 2009-10-16
Try the following methods:

1.  PRESS CTRL+ALT+F1, if it returns to terminal type SUDO REBOOT, if this does not work for to the next

2.  Press and hold the buttons ALT+SYS RQ+K, if that does not work try

3.  Pressing and Hold ALT+SYS RQ buttons, release them and press the letters R E I S U B 

if all else fails do a hard reset.

---

### Post by mgranet on 2009-10-16
Press and hold Ctrl-Atl-PrintScreen. Now press REISUB, while holding Ctrl-Alt-PrintScreen, giving about 15 seconds between each letter. I generally use my nose to accomplish this task.

---

### Post by mjp29 on 2009-10-16
> **mgranet said:**
> Press and hold Ctrl-Atl-PrintScreen. Now press REISUB, while holding Ctrl-Alt-PrintScreen, giving about 15 seconds between each letter. I generally use my nose to accomplish this task.

Ctrl-Alt-PrintScreen does nothing

Will try other responders method but thanks for your attempt to help me

---

### Post by aljoriz on 2009-10-16
rats I forgot to add CTRL to the combo that is CTRL+ALT+Print Screen or Sys Rq

---

### Post by mjp29 on 2009-10-16
> **aljoriz said:**
> Try the following methods:

1.  PRESS CTRL+AL+F1, if it returns to terminal type SUDO REBOOT, if this does not work for to the next

2.  Press and hold the buttons ALT+SYS RQ+K, if that does not work try

3.  Pressing and Hold ALT+SYS RQ buttons, release them and press the letters R E I S U B 

if all else fails do a hard reset.

ctrl-alt-f1 does nothing

thanks for your attempt to help though

i may end up just turning it off

but i will leave it on if someone here thinks they can force it out of this

---

### Post by mgranet on 2009-10-16
It's a tricky one to perform. The important part is that at no time can you release Ctrl-Alt-PrintScreen/SysRq keys. If you do, even for a split second, you have to re-try. This is why I hold the left Ctrl-Alt keys with my left hand, the PrintScreen/SysRq key with my right, and one by one, slowly, type REISUB (and NO other keys, or you have to start over) with your nose. It makes you look....special...but it's the only way I can get it to work reliably.

---

### Post by mjp29 on 2009-10-16
> **aljoriz said:**
> Try the following methods:


2.  Press and hold the buttons ALT+SYS RQ+K, if that does not work try

3.  Pressing and Hold ALT+SYS RQ buttons, release them and press the letters R E I S U B 

if all else fails do a hard reset.

2nd method does not work (even with function key held down) and i assume the "K" in 2nd method is just the letter "K" on keyboard?

will try your 3rd method now

---

### Post by mjp29 on 2009-10-16
> **mgranet said:**
> It's a tricky one to perform. The important part is that at no time can you release Ctrl-Alt-PrintScreen/SysRq keys. If you do, even for a split second, you have to re-try. This is why I hold the left Ctrl-Alt keys with my left hand, the PrintScreen/SysRq key with my right, and one by one, slowly, press REISUB (and NO other keys, or you have to start over) with the nose. It makes you look....special...but it's the only way I can get it to work reliably.

ok i'm going to try this

is "REISUB" a button or i am to type those keys (and do they have to be typed all caps)

this is interesting

---

### Post by aljoriz on 2009-10-16
if you decided to turn it off, make sure that its not writing on the Hard Disk

---

### Post by mgranet on 2009-10-16
No, you just type out r e i s u b

No caps, no spaces.

---

### Post by CharlesA on 2009-10-16
[Some infos about the REISUB thing.]("http://kember.net/articles/231/reisub-the-gentle-linux-restart")

That sounds quite handy.

---

### Post by mjp29 on 2009-10-16
> **mgranet said:**
> It's a tricky one to perform. The important part is that at no time can you release Ctrl-Alt-PrintScreen/SysRq keys. If you do, even for a split second, you have to re-try. This is why I hold the left Ctrl-Alt keys with my left hand, the PrintScreen/SysRq key with my right, and one by one, slowly, type REISUB (and NO other keys, or you have to start over) with your nose. It makes you look....special...but it's the only way I can get it to work reliably.


i held down buttons while wife typed reisub (both lower caps and all caps) and i even tried again holding down ctrl-alt-print screen-function while she typed it in

nothing works

looks like power off is going to be only solution thus far - i'll leave it on a while longer if anyone thinks there's a way out - i am curious about this

p.s. I personally believe this all happened because of the trackpad (that I never use) but see my trackpad post here

---

### Post by mgranet on 2009-10-16
It is. I forget what the REI part does, but S syncs the hard disk cache, U unmounts the disk, and B reboots. It is the only safe way that I'm aware of to force a restart on a hard freeze without the risk of a corrupt file system.

---

### Post by mgranet on 2009-10-16
Are you giving it a good 15-30 seconds between each letter? Also, since you have already attempted it and failed, it might be preventing you from attempting again.

---

### Post by mjp29 on 2009-10-16
> **mgranet said:**
> Are you giving it a good 15-30 seconds between each letter?


a good 15 or 30 seconds between each letter - no i didn't do that 

i'll try that [to my wife's dismay]

---

### Post by mjp29 on 2009-10-16
> **mgranet said:**
> Are you giving it a good 15-30 seconds between each letter? Also, since you have already attempted it and failed, it might be preventing you from attempting again.


ok I held down ctrl-alt-print screen for many minutes while i typed reisub every 30 seconds (then i released)

nothing happened at it took me like 3 minutes to pull this off

i felt like i was in some torture chamber where my hands were stuck to a wall and i could not move away - like a caged animal   LOL

---

### Post by tarps87 on 2009-10-16
If REISUB is failing it looks like it is a completely frozen system. (REISUB is usually the last fall-back), it looks like you will need to pull the plug, unless anyone else know a secret way.

(REISUB) Raising Elephants Is So Utterly Boring

---

### Post by mgranet on 2009-10-16
LOL. I never said it was fun, only effective. ;)

In this case, I think it seems to be truly stuck, and so would perform the old 'hold the power button until it dies' trick, which only requires one finger and 6 seconds. ;)

---

### Post by mjp29 on 2009-10-16
> **aljoriz said:**
> rats I forgot to add CTRL to the combo that is CTRL+ALT+Print Screen or Sys Rq

i tried all 3 methods and no go

i even tried reisuo like a link said would just shut it down



I'm going to turn it off now and reboot.

For those curious what made this lockup it was what appears to be a common problem with the trackpad on a laptop and perhaps streaming.  see my post at [http://ubuntuforums.org/showthread.php?t=1292790](http://ubuntuforums.org/showthread.php?t=1292790)  [to see what i was doing when laptop locked up]

anyways i'm rebooting it now - enough with the insanity LOL

---

### Post by mjp29 on 2009-10-16
> **mgranet said:**
> LOL. I never said it was fun, only effective. ;)

In this case, I think it seems to be truly stuck, and so would perform the old 'hold the power button until it dies' trick, which only requires one finger and 6 seconds. ;)


Yes, I think it is truly stuck and I'll hold down the power key with one figure with much delight [lol]

This will be useful to me in the future if it isn't a truly stuck system - I'll know what to do, because believe me when one does this 2 or 3 times (taking up to 3 minutes) one kinda gets this ingrained and hard wired into their mind.

I did wander if there would be a difference between holding down the power button or just pulling power (or yanking battery out) of laptop.

One final note is this:  if one strategically places their right hand pinky finger on the prnt screen button then one can (on a laptop) reach all the other keys and do it without using nose.

this has helped the dexterity of my hands also - LOL

one has to find humor in certain situations, don't they

---

### Post by aljoriz on 2009-10-16
on a related note, I have an OLD CD when I'd mount it would cause a SYSTEM LOCK UP ... needless to say i didn't use that CD again.

---

