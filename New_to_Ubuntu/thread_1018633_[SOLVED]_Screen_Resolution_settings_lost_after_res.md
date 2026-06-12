---
title: "[SOLVED] Screen Resolution settings lost after restart."
date: 2008-12-22
forum: New to Ubuntu
---

### Post by James Vine on 2008-12-22
Hi all,

In my quest to get ubuntu running at more than 800x600 I have installed a new graphics card (nvidia Ge Force 6200A) in place of my onboard graphics chip.

All fine, except......
Initally boots to 800x600
can use gksudo displayconfig-gtk to change resolution to 1280x800
All enhanced wobbly window things working!
Lovely!

Reboot

Login screen 1280x800
Login
Umbuntu drum noise
Big mouse pointer
800x600 again

Aaaaaagh!

Any ideas?
Please!****

---

### Post by namdung on 2008-12-22
Is the driver showing in System--->Administration-->Hardware Drivers?

Also try rebooting in Recovery Mode and fix the XOrg server.

---

### Post by James Vine on 2008-12-22
Hi, 

Yes, driver shows and is enabled will boot in recovery mode, fix and let you know what happens!

---

### Post by James Vine on 2008-12-22
Hurrah! Now works perfectly! 

Thankyou.

---

