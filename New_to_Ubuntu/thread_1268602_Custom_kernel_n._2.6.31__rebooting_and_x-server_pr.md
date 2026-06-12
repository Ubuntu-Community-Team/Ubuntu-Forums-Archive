---
title: "Custom kernel n. 2.6.31  rebooting and x-server problem"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by rumca.js on 2009-09-17
**Hello**

I have been experiencing freezes lately on my ubuntu laptop. I checked my memory with memtest it showed that memories are working properly. I have seen that on ubuntu freezes may happen (the topic I read in this forum yesterday had 60 pages).
So I had too much time and I thought I may test the new kernel. I found stable release of 2.6.31.

This was my first time i build my own custom kernel.

I copied .config file from boot folder, from previous stable release I found in synaptic packages /boot/config-2.6.28-15-generic

after running make xconfig  I changed two things in config. One to not include debug information for kernel - with it resulting object would have 50Mb size; I also changed in processor label of xconfig tree toshiba support - because it wasn't checked and I am running toshiba sattelite. On the other side Dell machine was supported by default. 

After make && make modules_install &&  make install
i runned mkinitramfs -o /boot/initrd.img-2.6.31 /lib/modules/2.6.31
which resulted in creating image file

**Problem number 1:**
sudo grub-update gives output it detects kernel number 2.6.31  and says it modyfies menu.lst in /boo/ directory. However it doesn't change a bit! How to affect the system to automaticly add new kernels into the list.

**Problem number 2:**
After modifying by myself grub and adding new kernel to the list, system boots. It goes through loading phase correctly, however it encounters problems while login screen. The screen becomes black, there are visible only 2 or 3 weird ubuntu signes on the top of the screen. It is not displayed correctly.

I thought that it may be a problem of X-server so I tried to run the text-console-mode  Ctrl-Alt-F1 to modify some things maybe run script for automatic reconfiguring x-server; After this happened something else. Computer rebooted. Every time I push the magic combination the laptop reboots.

---

### Post by KyleRaynor on 2009-10-15
ok, old thread. It sucks no one has answered before now, but did you recompile/install your video drivers?

And shame on anyone who knew the answer that ignored his question.
SHAME SHAME(shakes finger)

---

