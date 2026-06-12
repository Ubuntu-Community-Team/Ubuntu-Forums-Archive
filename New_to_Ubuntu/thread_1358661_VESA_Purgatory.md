---
title: "VESA Purgatory"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by jsaporta on 2009-12-18
Using 8.04 LTS for AMD64.
Installed an ATI driven video card.  ASUS, EAH4359 Silent.

I cannot get more than 800 x 600 on the display.  The display is capable of 1280 x 1024 @ 64 kHz horizontal, 60Hz vertical.   However System->Preferences->Screen Resolution is not allowing any options finer than 800 x600.

Asus does not support Linux drivers for this product AFAICT.

How can I fix this?  Some of the "control panel" windows are larger than my screen, and that is not fun.

Thanks,
John

---

### Post by Chesamo on 2009-12-18
Have you tried manually configuring X?

[http://ubuntuforums.org/showthread.php?p=8302145](http://ubuntuforums.org/showthread.php?p=8302145)

---

### Post by jsaporta on 2009-12-18
(this issue is partially resolved)

Chesamo,
Thank you for the pointer HOWTO pointer.  I am able to get my screen to more dense resolutions.

However, when I use the GUI to change resolutions (system->preferences->screen resolution) I see a green halo (the shape of a rainbow) across the background image.  That is, the background image (and the appearance of the windows) gets changed.  

This problem can be corrected by booting into recovery mode (esc during grub), running xfix, then restoring my xorg.conf file, and never changing the screen resolution again.

Speculation here, there is some autodetetction that is not working.  Furthermore, the error persists and gets corrected only when I use brute force (xfix).

 Please note:  I am using a KVM switch, this may be a factor hindering whatever hardware or software automation is failing.

How do I fix this?  Is it time to learn how to specify modelines?

---

