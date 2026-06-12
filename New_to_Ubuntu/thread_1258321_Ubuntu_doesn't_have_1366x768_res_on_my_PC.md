---
title: "Ubuntu doesn't have 1366x768 res on my PC"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by nintengeek on 2009-09-04
I'm having issues with Ubuntu, it's looking weird and stretched.  Resolution is currently set to OFF and the only options available 1280x768, Off, 800x600.  I need 1366x768.  I am on a Gateway NV5214u.

---

### Post by nintengeek on 2009-09-04
I have an AMD processor

---

### Post by overdrank on 2009-09-04
Hi and welcome, you may look under system, administration, hardware drivers to see if any drivers are available for your system. 
Moved to Absolute Beginner Talk

---

### Post by cwsnyder on 2009-09-04
Which driver are you using for your ATI video subsytem?  The proprietary driver or the vanilla ATI Linux driver?  Also which version of that driver, if you know it?

I know from other forums that the proprietary ATI driver has been undergoing some fairly massive changes, with the Intel and nVidia drivers seeming to be in better shape at last report.  The vanilla ATI driver will not support video acceleration, but, when you set up a custom xorg.conf file, you should be able to set up the 1366x768 resolution, given the technical parameters for vertical and horizontal refresh needed for that resolution.

---

