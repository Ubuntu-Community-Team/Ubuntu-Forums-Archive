---
title: "Ubuntu Stuck on pre-Login Screen"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Vyder on 2009-05-03
Hi

I have Ubuntu 8.10 and Windows Vista Dual boot on my Dell Inspiron 1420 laptop.

After the grub menu, a bunch of stuff scrolls past on a black screen and then a brown screen appears with a spinning wheel. And it gets stuck.

This screen usually appears just before it shows me the login screen.

It does not show the usual ubuntu loading bar.

I can boot in recovery mode and use ubuntu via command prompt. But i want the gui to start.

Any ideas whats wrong?

Thanks,
Vyder

---

### Post by e_james on 2009-05-04
It sounds to me that there are problems with the video driver / settings. What I did in similar circumstances was to boot up with the Live CD in safe graphics mode and copy the xorg.conf file to a usb drive. I also did the same with a Knoppix DVD, which just worked 'out of the box'. I then used these copies as guides to adjust the installed xorg.conf until I got what I wanted. 

Just in case other users are in need of the same solution, the computer in question was an eee Box B202 connected to a flat screen TV with a maximum resolution of 1024x768. The primary purpose was to play back divx files and the 'vesa' driver doesn't do that as well as I would like. The TV connection is vga and the computer is DVI-I with an adaptor, which is probably why the monitor detection has problems. Whose bright idea was it to use 1280x1024 as the default resolution? I thought one of the strengths of linux was the ability to work on older / limited hardware.

---

### Post by Vyder on 2009-05-05
I fixed it by uninstalling all the software I installed in my last working session. Traced the problem back to startup manager. I tried installing it again, and same thing happened. Guess startup manager doesnt work.

Thanks anyway.

---

