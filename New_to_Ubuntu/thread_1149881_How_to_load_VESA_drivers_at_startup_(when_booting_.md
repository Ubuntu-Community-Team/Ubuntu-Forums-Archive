---
title: "How to load VESA drivers at startup (when booting from LiveCD)?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by pstein on 2009-05-05
When I boot from Ubuntu 9.04 CD then the initial menu (with e.g. the keymap and language menu) is displayed but the actual full Ubuntu is not successful booted later.
After some minutes only the cursor is visible on a black screen.
 
It seems to me that the problem is (as in other Linux Live CDs) that the graphic cpu is not correctly recognized.
 
For other Linux-CDs I have to pass some additional parameters at startup e.g.
 
xmodule=vesa
 
to thell the system to load the vesa drivers.
 
How do I achieve this for Ubuntu?
 
Where can I specify alternative VESA graphic/video drivers
 
Peter

---

### Post by cariboo on 2009-05-05
Try safe graphics mode, press F4 at the menu screen and select safe graphics mode, then select Try without changing.

---

### Post by pstein on 2009-05-06
> **cariboo907 said:**
> Try safe graphics mode, press F4 at the menu screen and select safe graphics mode, then select Try without changing.
 
This does not help. Even after I selected "safe graphics mode" Ubuntu boot sequence ends up on a black screen with a blinking cursor.
 
Any other way to boot?
 
My notebook and video card is: 
Samsung X20 Notebook (XVM 1730 V) 
with 128MB Intel Graphic Media Accelerator GMA 900 
with Chipset Intel 915GM/GMS resp Intel 82915GM

---

### Post by Bradtek on 2009-05-06
try adding the parameter
vga=791

---

### Post by pstein on 2009-05-06
> **Bradtek said:**
> try adding the parameter
vga=791
 
This is an improvment. I can hear now music jingles and the boot process
is longer but at the end the screen is still black.
 
Any other parameters to try?
 
Peter

---

