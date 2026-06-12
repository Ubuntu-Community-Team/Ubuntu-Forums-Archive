---
title: "WebCam Problem"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by Intzi1992 on 2011-08-29
Hello... i am new to Ubuntu Sofware and i am trying to solve the problem with my webcam's but i cant make it.. I have 2 camera's the one appear to the LsUSB like:

**Bus 002 Device 004: ID 046d:092f Logitech, Inc. QuickCam Express Plus**

And the other like

**Bus 002 Device 005: ID 046d:08b5 Logitech, Inc. QuickCam Sphere**

Can anyone tell me if there are drivers for my camera's and if yes how can i install them?

**Thx :D**

---

### Post by lkjoel on 2011-08-29
What is your problem exactly? Can Ubuntu find them?

---

### Post by no2498 on 2011-08-30
webcam drivers are in the kernel 
with the cams plugged in
open a terminal type dmesg click enter
that should tell what drivers they use

---

### Post by Intzi1992 on 2011-08-30
**Ok thx a lot for answering to my thread... i found the problem...**

---

### Post by konstantinth on 2011-09-10
the type is V-UAP41logitech...i don't know why my computer can't find my webcam..can you help me??i don't know much of ubuntu..i install it recently.

---

### Post by snip3r8 on 2011-09-10
> **Intzi1992 said:**
> **Ok thx a lot for answering to my thread... i found the problem...**
If you post the solution and mark the thread as solved it may help other users with the same problem.

> the type is V-UAP41logitech...i don't know why my computer can't find my  webcam..can you help me??i don't know much of ubuntu..i install it  recently.

Open up the terminal and type lsusb and press enter,then copy and paste the output here.

---

