---
title: "Will not wake up"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by tuxisapenguin on 2011-07-22
Hi all!

I have a brand new Samsung n145-JP02 netbook with Ubuntu 11.04 installed. Everything works perfectly except hibernation/suspending. Whenever I close the netbook and leave for a while, the screen will not turn on. I always have to remove the battery because holding the power button does not work. This is really getting annoying and was hoping anyone in the community could have a solution?

Thanks!

---

### Post by papibe on 2011-07-22
Try forcing it like this: (1) go to text mode by pressing crtl+alt+F1, then (2) go the graphic session by pressing crtl+alt+F7.

Hope it helps.

---

### Post by wildmanne39 on 2011-07-22
Hi, have look at this link on freezing issues maybe it will help.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by 2F4U on 2011-07-23
Very often, suspend/hibernate problems are due to graphics drivers. Can you provide information about your hardware and what graphics drivers you are currently using?
On one of my notebooks (old ThinkPad X31 with ATI Mobility Radeon M6) I had the same problem than you, i.e. the notebook would not wake up from suspend/hibernate. I was able to fix the problem by adding "nomodeset" (without the quotes) to the grub line.

---

