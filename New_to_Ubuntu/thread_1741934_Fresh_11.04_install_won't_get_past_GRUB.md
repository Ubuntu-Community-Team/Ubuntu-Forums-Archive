---
title: "Fresh 11.04 install won't get past GRUB"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by Billabong81 on 2011-04-28
Hey guys, I just did a fresh install of 11.04.  First boot took a long time (5ish minutes) and told me I didn't have the hardware to run unity, so it booted me into classic.  I figured it was a video card issue, as my nVidia GTX465 has needed to have drivers downloaded for it in the past in 10.10.  I downloaded the nvidia drivers and went to restart my computer.

Now when I boot the computer, GRUB comes up with normal options (ubuntu, safe mode, mem test, Windows 7 loader).  I select the ubuntu install and it just sits on a screen with the purple box with black border (grub text removed).  After a few minutes, it proceeds to a blank black screen.

Any ideas?

---

### Post by cariboo on 2011-04-28
Start in recovery mode, and select failsafeX from the menu. This should take you to the desktop, where you can make sure that nvidia-current is installed correctly.

---

### Post by Billabong81 on 2011-04-28
Thanks for the reply.  Right when I booted using failsafeX, got warnings that my graphics and display were not recognized and such.  Once I finally got booted, I opened the drivers menu and found the nVidia 173 drivers were present, but not active.  Currently downloading version current.  Will update with results!

Update: Seems to be working using the current drivers instead of 173.  Cool beans!  Thanks cariboo907!

---

