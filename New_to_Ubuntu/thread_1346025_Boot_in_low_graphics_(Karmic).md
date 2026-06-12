---
title: "Boot in low graphics (Karmic)"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Letterbomb05 on 2009-12-04
Hey, a problem has recently come about on Ubuntu 9.10...
For some reason, I think for the past week or so Ubuntu sometimes boots in what I think is low graphics mode... I'm given a login screen but it's the white text on black background, as if I was running Ubuntu Server Edition. I end up having to reboot one or sometimes several times until it boots normally. No idea why this is happening.

This gets quite annoying... any help is much appreciated!
- Aaron.

---

### Post by drumz on 2009-12-05
I'm seeing the same thing on two different systems.  My home server (Kubuntu only, dual AMD Opteron system) it happens constantly and has been this way for a couple of days.  Yesterday it started on my laptop (Intel), but if I shut it down and restart it it works OK.  On my server if I hit the esc key twice as soon as the 'low graphics mode' dialog appears it finishes booting perfectly fine.

There's a bug filed [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/485651](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/485651)  and here [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/485033](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/485033) that has the same thing we're seeing.  It seems that if you switch to GDM instead of KDM for the login screen it 'fixes' the problem.

The second link I provided has you rename a file that fixes it.

There are also several other threads on the forums here with people reporting the same problem.

---

