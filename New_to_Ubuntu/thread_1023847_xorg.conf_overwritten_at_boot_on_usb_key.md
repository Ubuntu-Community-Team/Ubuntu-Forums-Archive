---
title: "xorg.conf overwritten at boot on usb key"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by jpmur on 2008-12-28
Hello,

I have created a persistent usb key with ubuntu 8.10 .

After boot, I used the nvidia driver 177 .
I updated the xorg.conf with nvidia-xconfig. 
Then restarted gdm.
All is OK then.

But each time I boot, xorg.conf is overwritten by a basic file.
I had to copy the xorg.conf from nvidia I saved before and then restart gdm.

Why ?  

JP

---

### Post by jpmur on 2008-12-30
I installed last nvidia driver : 180.18
No problem to install it and start gdm first time.

But at next boot, same problem.

In Xorg.0.log, only one error : "(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)"

Why it works when I start gdm manually, but **not at boot time** ?

Any idea ?

JP

My video card is on the motherboard (MSI P7NGM) and is a 9300, based on 730i chipset.

---

### Post by octaedro7 on 2009-03-28
Same thing here, xorg.conf is restored to the basic on each restart.
Annoying!!
I'm running a persistent usb install of Jaunty beta.
Hopefully some guru shows up to help us.

---

