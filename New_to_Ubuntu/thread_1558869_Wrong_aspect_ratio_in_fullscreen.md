---
title: "Wrong aspect ratio in fullscreen"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Queseq on 2010-08-22
Hi, I posted this in the Multimedia support forum but it got buried so I thought this might be the correct place for it.

I've got an AAO 150 with an Intel GMA 950. Whenever I use scummVM or dosbox in fullscreen the image is stretched across the whole screen rather than having the correct aspect ratio. The odd thing is that this worked fine with an older version of UNR (9.04 I think) but now I have UNR 10.04 it doesn't do what I want. Any idea what could have changed and how to fix it?

---

### Post by finny388 on 2010-08-23
are you sure it not because of newer versions of scummvm or dosbox?

I found this on scumm's **[readme]("http://scummvm.svn.sourceforge.net/viewvc/scummvm/scummvm/tags/release-1-1-1/README?view=markup"):**

> Ctrl-Alt a - Toggle aspect-ratio correction on/off
 	Most of the games use a 320x200 pixel
 	resolution, which may look squashed on
 	modern monitors. Aspect-ratio correction
 	stretches the image to use 320x240 pixels
 	instead, or a multiple thereof

---

### Post by Queseq on 2010-08-24
I don't think the version of scummvm has changed, and I have the 'correct aspect ratio' box ticked in the settings. Will give ctrl-alt-a a try though, thanks for the reply.

I thought this would be an easy fix but is it more a hardware issue than software?

---

### Post by Vaphell on 2010-08-24
does intel driver provide some sort of configuration panel? nvidia and ati do and there you can configure the way picture is stretched

---

### Post by Queseq on 2010-08-24
If they do I can't find any way of accessing it. I thought it might be a problem with the X drivers but can't find anything about picture stretching on their wiki.

---

### Post by Vaphell on 2010-08-24
[http://www.linuxquestions.org/questions/linux-software-2/aspect-ratio-scaling-with-intel-gpus-and-linux-793488/](http://www.linuxquestions.org/questions/linux-software-2/aspect-ratio-scaling-with-intel-gpus-and-linux-793488/)

you can try that

---

### Post by Queseq on 2010-09-04
Thanks, turns out ```
xrandr --output LVDS1 --set "scaling mode" "Full aspect"
``` works for me.  I also found a bug posted on launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/458571").  Unfortunately there doesn't seem to be a way of including this in xorg.conf so I have to run the command during start-up which is a bit annoyance. It does work though so I'm marking this solved.

---

### Post by mgol on 2010-12-28
> **Queseq said:**
> Unfortunately there doesn't seem to be a way of including this in xorg.conf so I have to run the command during start-up which is a bit annoyance.

Isn't it enough to put this command into the ~/.xprofile file? You might not have to invoke it manually after each start.

---

### Post by Queseq on 2011-01-05
That's what I meant by runing during start up. The annoying bit was that it made the screen flicker.

I've now moved to Arch Linux which doesn't have this problem, probably because it has more up to date intel drivers.

---

