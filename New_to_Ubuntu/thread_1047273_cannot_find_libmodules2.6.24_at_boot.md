---
title: "cannot find /lib/modules/2.6.24 at boot"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by ET! on 2009-01-22
i compiled and installed the kernel 2.6.24...but when i boot i get the message 
"cannot find /lib/modules/linux-2.6.24"

 at boot along with 

"cannot find /lib/modules/linux-2.6.24\temp.dep" 


in the black screen.then im getting <initramfs> prompt...but after booting it in another kernel the /lib/modules/linux-2.6.24 was in proper place...what went wrong??:confused:

---

### Post by Titan8990 on 2009-01-22
It looks like you didn't compile the modules for your kernel.

Typically, you don't want to compile custom kernels in Ubuntu. There are other distros that provide much better support for this (or require).

Examples:

Gentoo
Arch Linux
Slackware

---

### Post by ET! on 2009-01-22
i downloaded the kernel from "kernel.org"....i have previously installed kernels but didnt get such messages...can you tell me how to fix this???

---

### Post by ET! on 2009-01-22
can any one help me out...stuck with this for a long time..and i need the kernel working very badly...

---

### Post by Titan8990 on 2009-01-22
I can tell you right now, you will **never** get a vanilla kernel to work in Ubuntu.

Like I said in my last post, if you want to do custom kernels yourself, you should be using a different distro.

I recommend Gentoo.

---

