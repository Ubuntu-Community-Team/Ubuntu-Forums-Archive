---
title: "Ubuntu 10.04.1 LiveCD Will Not Boot"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by AbbySciuto on 2010-09-27
When I attempt to boot from the LiveCD, I am able to access the GRUB menu.  However, when I attempt to boot normally (into LiveCD), the screen goes completely blank.  There is absolutely no output on the screen.  The drive appears and sounds like it is being accessed, but the screen remains blank.  Removing "splash" and "quiet" allows me to see the drivers load, but as soon as X starts, the screen blanks again.  Attempting a dump back to console (I'm assuming CTRL+ALT+F1) yields no result.  Attempting to startu using the Safe Video Mode yields nothing, as that entry apparently doesn't exist in the GRUB menu (The only options are Normal, Driver install or something, and OEM Install).

I also followed directions which told me to append "xforcevesa" to the boot parameters (which also yielded nothing).

My display resolution is 1280x800, and my adapter is an Intel HD Graphics.  The computer itself is an HP EliteBook 2740p.

Can anyone offer some help with this?  I'd like to boot Ubuntu off my external hard drive, but if X won't allow my computer to boot normally, I'll have to pass.

RELATED?  Lucid Puppy Linux 5.1.1 does the same thing, and there's the same lack of information about this problem.

---

### Post by wojox on 2010-09-27
When you get to your options screen where it will let you choose what you want to do press F6 and choose "nomodeset" (arrow down and choose it with your spacebar). See if that does anything.

---

### Post by AbbySciuto on 2010-09-28
> **wojox said:**
> When you get to your options screen where it will let you choose what you want to do press F6 and choose "nomodeset" (arrow down and choose it with your spacebar). See if that does anything.

This allows me to see (combined with the deletion of splash and quiet) all the stuff loading.  Once again, though, as soon as a GUI is loaded, the screen goes blank.  I've seen tutorials about this, so I know the window that asks if you want to try Ubuntu or install it should be next.  I can only assume that it's something wrong with how X is configured.  Is there any way at all to get to a command line interface and skip X entirely?

---

### Post by AbbySciuto on 2010-09-28
I've discovered something else.  Any Knoppix type OS will start X in VESA mode.  Only Ubuntu-based OSes will refuse to recognize VESA as a valid mode.

Guess I'll be using Knoppix for a while...

This seems like an odd problem, considering that Knoppix and Ubuntu have the same root (Debian).

---

### Post by Jolicoeur on 2010-09-28
I have this same problem.  I tried all of the suggestions but still end up with a black screen.  I really want to do a clean install with 10.04.1 rather than online update.  The only live cd that will load is the 8. one, then I update through the internet.

---

### Post by AbbySciuto on 2010-09-28
I wonder, does pressing ctrl-alt-numplus do anything?  On Slax it says if there's a black screen to press that a few times.

---

### Post by BigRedButton on 2010-09-29
I have no idea if this is relevant, but what kind of hardware are you all trying to boot this onto? In my experience, this usually happens when the computer simply runs out of gas. (yes, I know the livecd doesn't use much resources) But it may be worth trying the alternate install cd, whether it's a hardware issue or not.

---

### Post by AbbySciuto on 2010-09-29
> **BigRedButton said:**
> I have no idea if this is relevant, but what kind of hardware are you all trying to boot this onto? In my experience, this usually happens when the computer simply runs out of gas. (yes, I know the livecd doesn't use much resources) But it may be worth trying the alternate install cd, whether it's a hardware issue or not.

This computer (HP EliteBook 2740p 4GB RAM Core i7-620M 2.67GHz) is more than adequate to run 10.04.1.  Where is this alternate install CD you speak of?

---

### Post by joehillen on 2010-12-06
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

Also, did you end up solving your problem? How?

---

