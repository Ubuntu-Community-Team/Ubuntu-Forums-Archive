---
title: "blank desktop background image after login"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by itastelikelove on 2010-02-18
I'm a Linux first-timer, and trying to get Xubuntu running on my old laptop, because it had too much difficulty installing regular Ubuntu (256 mb ram, 367 Mhz Intel Celeron). I don't want to dual-boot, or anything fancy like that (not yet anyway), just wipe everything and run some kind of Linux.

Xubuntu seems to install just fine (I've done this twice now), goes through the shtick, reboots itself and seems to run OK (for a little while at least- I didn't play around too much, except to see that it really ran). Then I turn it off. When I turn it on again, it works its way up to the login screen, and I give it my username and password. 

Then everything disappears. Sometimes I get a Xubuntu loading screen, sometimes I don't. Either way, after that all I get is the background image from the desktop. No icons, no bars, no commands, I can't right-click for options. I pressed every button on the keyboard, including a few in likely-seeming combinations. The only results were A) ctrl+alt+del seems to bring up a login window. Same result as logging in normally. and B) the 'print screen' button brings up a 'Save screenshot as' window which I can browse around in and see all of the folders on the computer.

That's it. That's all I get for my first experience with Linux. I want to love it, I really do. But if it doesn't run, it doesn't run...



*note* - my knowledge with computers is mostly in the form of problemsolving via poking around looking for likely solutions or searching forums for relevant posts. when it comes to actual technical knowledge or using command-lines or what-have-you, it's probably best to assume that I know next to nothing. I can and WILL look stuff up, but it takes time. This IS mostly a learning project for me, but still...

---

### Post by itastelikelove on 2010-02-18
Most of the threads I've found about similar problems mention using

```

sudo nano /etc/X11/xorg.conf

```and inserting Driver "vesa", but when I try that, the window comes up completely blank, no devices listed or anything. There is supposed to be something there, right?

And I can't seem to get into any kind of recovery mode, either. 

What do I do now?

---

### Post by itastelikelove on 2010-02-26
well, I fixed my problem quite on accident, but it was a very easy solution, and it works everytime. I even reinstalled a few times to test it. Same problem each time, same solution worked perfectly each time. 

1. Made a Damn Small Linux CD
2. Started and set up DSL, but DID NOT actually install anything from the disk (unless it did so automatically without asking permission
3. Removed the disk and restarted the computer.
4. Xubuntu started up perfectly, and required no additional tweaking

Not sure why it worked, but it did. I haven't seen this solution anywhere else, so I figured I would submit it for curiosity and posterity, if nothing else.

---

