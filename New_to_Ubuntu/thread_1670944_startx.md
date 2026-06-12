---
title: "startx"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by gem85 on 2011-01-19
Hi All,
 
I'm new to Ubuntu and I'm currently working through the book "Unix in 10 minutes" to try to teach myself some basis.
 
I have typed **startx** into the Terminal (as root user), however, the following error is displayed:
 
**Fatal server error:**
**Server is already active for display 0**
**If this server is no longer running, remove /tmp/.X0-lock**
**and start again.**
 
**Please consult The X.Org Foundation support at **[**http://wiki.x.org**]("http://wiki.x.org")** for help.**
 
**ddxSigGiveUp: Closing log.**
 
Can anyone give me any guidance of how to overcome this? Or how to remove the tmp lock?
 
Thanks and apologies if this is in the wrong place!

---

### Post by spook1980 on 2011-01-19
sounds like you already have x started, so since x is already running the startx command will do nothing. 

startx is a command given to start a GUI when all u got is a command line

---

### Post by spook1980 on 2011-01-19
sounds like you already have x started, so since x is already running the startx command will do nothing. 

startx is a command given to start a GUI when all u got is a command line

---

### Post by cchhrriiss121212 on 2011-01-19
Ubuntu is a Linux OS, not Unix which are not the same thing. If you need a more relevant guide, try this:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Regarding the problem: X is already running, that is why you cannot start X.

---

### Post by corncob on 2011-01-19
I agree with Spook -- it sounds like X is already running but in a different terminal than the one you're in.  My GUI runs in terminal 7.  Press [CTRL][ALT][F7] to get there.

---

### Post by JKyleOKC on 2011-01-19
Looks like everyone is telling you the obvious cause, but not mentioning what is actually going on!

When you launch Terminal from the normal screen, it's running INSIDE of the screen process, and the X server had to be launched when you booted up in order to display that screen. That's why it's already running.

To practice learning the commands with your book, don't open a Terminal window. Instead, press CTRL, ALT, and F2 all at the same time to start a new "virtual console." This will give you a totally black screen with a "login:" prompt. Log in with your user name; you then get a "password:" prompt. Type your password but don't expect anything at all to echo, not even asterisks. After a couple of seconds, you should see a prompt just as if you were in a Terminal window. From there, you can do all the book exercises since you're at a pure console and X is not running in it.

While it's true that Linux is not Unix, that's like saying that a Ford is not a Chevrolet -- the differences between a Linux distribution and the original Unix are smaller than the differences between autos from two different manufacturers! Thus 99.9% of what your book has to say will still be applicable. Go for it!

---

### Post by cchhrriiss121212 on 2011-01-19
> Thus 99.9% of what your book has to say will still be applicable.
If it is suggesting he start X manually, then I doubt it is any use at all. New users do not need to know what X is let alone how to start it manually. Terminal use and editing system config files are not what Ubuntu is supposed to be like, it is supposed to be user friendly to non-technical types.

If someone *does* want to learn that stuff, then that is fine, but it is not necessary.

---

### Post by JKyleOKC on 2011-01-19
I fully agree that it's not necessary, but the original posting indicated that he DOES want to learn it.

---

### Post by JKyleOKC on 2011-01-19
duplicated when server timed out

---

