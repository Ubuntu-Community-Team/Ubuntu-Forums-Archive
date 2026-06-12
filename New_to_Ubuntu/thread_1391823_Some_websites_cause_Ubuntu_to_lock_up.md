---
title: "Some websites cause Ubuntu to lock up"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by mistypotato on 2010-01-27
Is anyone else having a problem with websites occasionally locking Ubuntu up completely needing a power switch shut down and re-boot?

It happens about once a month or so.  Not too big a deal but I find it odd that a website should at any time be able to lock up my computer so that I can't even open a terminal and issue a kill command or anything.

---

### Post by bkratz on 2010-01-27
> **mistypotato said:**
> Is anyone else having a problem with websites occasionally locking Ubuntu up completely needing a power switch shut down and re-boot?

It happens about once a month or so.  Not too big a deal but I find it odd that a website should at any time be able to lock up my computer so that I can't even open a terminal and issue a kill command or anything.

Never had that happen. Can you give a sample URL to test?

---

### Post by HarrisonNapper on 2010-01-27
Also, is it Ubuntu or FF? Can you switch ttys? Ctrl-Alt-F2 to test switching to 2, then switch back to 7,8,9 or whichever X is in for you. Also, if you get in that situation, hold down Alt and PrtScr and while holding both down, press the following keys in order: R, E, I, S, U, B

Cheers.

---

### Post by oldsoundguy on 2010-01-27
> **mistypotato said:**
> Is anyone else having a problem with websites occasionally locking Ubuntu up completely needing a power switch shut down and re-boot?

It happens about once a month or so.  Not too big a deal but I find it odd that a website should at any time be able to lock up my computer so that I can't even open a terminal and issue a kill command or anything.

These are usually sites that do not realize the Internet Explorer is not the only browser used and the site manager has geared content JUST to IE (thus shutting out 50% or more of their potential customers!)

You CAN (if you are using FireFox) try running "Default User Agent" (a plug in) and run it in IE mode.  Works MOST of the time.

as to being able to kill a process, I installed the force quit applet in the panel so I no longer have to deal with those lock-ups by using terminal.

But you can re-set .. (will need to launch your windows again) by using RightAlt/PrintScreen/K key combiniation.

---

### Post by J V on 2010-01-27
I'm guessing flash is the problem here, if you are on 64bit, downlaod the deb from adobe, the 32bit occasionally had memory leaks that locked up the computer here too...

---

### Post by warfacegod on 2010-01-27
When my wife goes on facebook her computer will sometimes slow to a crawl because of the site trying to run scripts. I had to install NoScript Firefox addon.

---

### Post by Hospadar on 2010-01-27
If you don't know, you can switch to a tty (text only terminal) with Ctrl-Alt-F# (f1, f2, etc)

---

