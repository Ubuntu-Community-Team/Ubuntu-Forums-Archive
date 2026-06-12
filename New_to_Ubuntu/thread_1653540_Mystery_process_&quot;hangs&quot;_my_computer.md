---
title: "Mystery process &quot;hangs&quot; my computer"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by kroq-gar78 on 2010-12-27
Hello Ubuntu Forums,

I have installed Ubuntu 10.10 on my external hard drive some time ago. I installed LXDE and XFCE on Ubuntu to see how fast they were, and I still have GNOME. Recently, a mystery process &quot;hangs&quot; my computer to where I can only type in things on open terminals. My desktop icons are becoming &quot;transparent&quot; where I minimized a window. I saw the CPU meter in the applet in the top panel, and it said my 2nd CPU is going at full (lighter color filled to top). I can see my external HDD's light flashing but I don't hear any noises from it. It could be that I have recently started using chrome. When my computer locks (screensaver), I can't wake it up and just get 2 blank screens (2 monitors).

This time, I'm using my computer and this happens. I try to run the top program but it doesn't run (just a blank line). I can't even interrupt the commands w/ CTRL-C.

Anybody know why this is happening?
Thanks in advance.

UPDATE: It just got locked (I'm on a separate computer to post this), and the screensaver went away. Strangely, no password prompt is coming up.

UPDATE 2: After 14 hours (overnight), still the same thing is happening.

---

### Post by kroq-gar78 on 2010-12-28
*bump*

It's now been almost 24 hours and still the same thing. I just tried to to to a tty shell but now my mouse disappeared.

UPDATE: The shutdown screen (the text one) just popped up and it says "Kubuntu 10.10". I'm not using Kubuntu (I installed kubuntu-desktop to try it out and *tried* to remove it. I'll try to put up a picture.

---

### Post by kroq-gar78 on 2010-12-29
So, it's now been 48 hours and still nothing. Here are the pics. There are two monitors, and both show the same thing.

*bump* *bump*

Should I just hard reset it?

---

### Post by Rubi1200 on 2010-12-29
Try Ctrl+Alt+Del to shutdown.

But, to get back to the problem.

Please post the _full_ specifications for the computer.

This sounds as if it might be either graphics or RAM related.

Without knowing the specifications, we cannot really advise you further.

Thanks.

---

### Post by kroq-gar78 on 2010-12-29
Rubi,

Control-Alt-delete didn't work (no response after ~10 min). The only response was it showing the white text and "Kubuntu 10.10" as I described before. Apparently, it went into "sleep" or something like that (I pressed a random key later and same thing). That's why only the orange text could be seen. Please look at the attached picture to see what I mean.

To get my hardware specs (I haven't written them down before; I really need to :S) I would have to do a hard reset. Should I do it to get the hardware specs?

Thanks in advance.

---

### Post by NightwishFan on 2010-12-29
First do this: Hold Alt+SysRQ and type slowly one at a time (while holding the former) R E I S U B. If that does not work, hard reset it.

---

### Post by Rubi1200 on 2010-12-29
Okay, try this (it's a bit of a test for your fingers, but should work):

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted. REISUO will do a shutdown rather than a restart.

edit: oops, beaten to it

---

### Post by kroq-gar78 on 2010-12-29
uhh...... well, that reset it all right, but now it had a weird BIOS screen and says "keyboard failure" :S 

UPDATE: OK it booted back. I'll get the specs for you. I'll use lshw

UPDATE: The output of the command is too long (can't scroll up to it in terminal), so here is some stuff from the "sysinfo" GUI prog:

System tab: for some reason, the program crashes when I click on it.
CPU:
Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
Freq: 1861.863 MHz
L2 Cache: 2048 KB
RAM:
total: 3021 MB
Swap total: 3067 Mb
Graphics card:
GeForce 7300 LE
PCI-E 16x
512 MB
450 MHz

Tell me if there's any more specific info you need. Thanks.

---

### Post by Rubi1200 on 2010-12-29
Do you have desktop effects (Compiz) enabled? I would try turning that off for a start.

Also, you have an NVidia graphics card. Are the drivers all installed?

See here:
[http://ubuntuforums.org/showpost.php?p=10191728&postcount=6](http://ubuntuforums.org/showpost.php?p=10191728&postcount=6)

---

### Post by kroq-gar78 on 2010-12-29
would desktop effects be enabled if the visual effects is "none"? Seems like a simple ques, yes, but I have compiz-config on my comp. I seem to remember that none of the FX worked, so should I worry about still?

I have the latest (version current) driver. I don't know what you mean by "all", but I have that one (latest).

---

### Post by kroq-gar78 on 2011-01-02
*bump*

Okay, it happened again. What do I do?

---

### Post by sodra on 2011-01-02
From My experience, Google Desktop uses 100% of the cpu, see if you have that or not.
I had a similar problem months ago.

If you have Google Desktop, uninstall it

---

### Post by kroq-gar78 on 2011-01-02
No, unless it installs when chrome installs. Thanks for the tip, I'll keep it in mind.

---

### Post by kroq-gar78 on 2011-01-03
So, it happened again. If nobody posts anything that I need to do on the computer within 18 hours while it's like this (I doubt you even can do anything when its like this), I'm going to do that REISUB thing to reset it.

P.S. What does the REISUB thing do (as in besides restarting the computer)

UPDATE: I'm just restating it. My bro needs to get something off of it.

---

