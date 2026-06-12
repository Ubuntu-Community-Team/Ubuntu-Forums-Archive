---
title: "Black Screen"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by akmal710 on 2011-02-13
Hi 
When I start my computer I just get the Acer logo screen and after that a cursor blinks and there is no error or any message ...
 
What next do I need to do, to get in Ubuntu.
 
Thanks

---

### Post by drs305 on 2011-02-13
> **akmal710 said:**
> Hi 
When I start my computer I just get the Acer logo screen and after that a cursor blinks and there is no error or any message ...
 
What next do I need to do, to get in Ubuntu.
 
Thanks

You may not see the Grub2 menu if you have a single OS computer (Ubuntu) or have Grub2 set up to auto-boot Ubuntu. It's possible you have a video problem.

You can try to correct this by editing the Grub2 options passed to the kernel during boot.

Turn on or reboot the computer and hold down the SHIFT key. This should display the Grub2 menu. Highlight the first Ubuntu entry, then press "e" to enter the editing mode.

Cursor to the end of the "linux" line, which probably ends with "quiet splash". If so, add **nomodeset** to the end of the line.

Press CTRL-x to boot.

If it successfully boots, go to System, Administration, Additional Drivers. Hopefully your video card driver is displayed. Add the driver and see if that corrects the problem.

---

