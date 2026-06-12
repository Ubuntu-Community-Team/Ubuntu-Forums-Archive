---
title: "hangs after splash screen"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by davebridges on 2010-05-02
I tried upgrading to 10.04, but after the screen that says UBUNTU it goes black then eventually shuts off.  The live CD does the same.  I dont see the grub menu, so i cant go into recovery mode but i am thinking it might have shut off mid-upgrade.  Is there any way to force into grub?

---

### Post by madjr on 2010-05-02
older versions work?

what video card you have?

if live-cd hangs is sign to not install

---

### Post by davebridges on 2010-05-02
older versions did work... the video card is a builtin intel that comes with a dell laptop, im not sure what type

---

### Post by davidmohammed on 2010-05-02
strong suspicion that you are suffering from the dreaded intel 855GM issues with lucid.

Given that you said its failed mid-way through upgrade, I would roll back to your previous backup (you did make one didn't you :-) ) and then check what type of graphics card it is.  If its a intel i8xxx type then don't upgrade to lucid until the first "service pack" (the 10.04.1) release.

---

### Post by shof2k on 2010-05-02
> **davidmohammed said:**
> strong suspicion that you are suffering from the dreaded intel 855GM issues with lucid.

Given that you said its failed mid-way through upgrade, I would roll back to your previous backup (you did make one didn't you :-) ) and then check what type of graphics card it is.  If its a intel i8xxx type then don't upgrade to lucid until the first "service pack" (the 10.04.1) release.

Is there an issue with i8xx cards?  If so, why wasn't anything added to the compatibility notes for the release?

---

### Post by davebridges on 2010-05-03
ok thanks... guess ill wait and re-load once this bug is fixed

---

