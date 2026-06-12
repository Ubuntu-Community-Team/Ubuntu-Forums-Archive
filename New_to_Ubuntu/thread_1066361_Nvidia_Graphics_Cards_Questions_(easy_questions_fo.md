---
title: "Nvidia Graphics Cards Questions (easy questions for you guys)"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Shpega on 2009-02-10
I have a Radeon 9500 series card, which I come to find out is one of the worst ones to have with 8.10, I heard that Nvidia ones all pretty much work too.  So I bought an e-GeForce 6200, which I have yet to open since  I read in the release notes that noone of the GeForce cards support 3d acceleration, now I'm not looking for hardcore gaming or anything, the 3d desktop effects and video playback are pretty much all I'm looking for.  So will this card work for me (if I open it I bought it) or if not, is there a list of cards that actually work, all I can find are lists of ones that don't (which so far seem like every one I own)  Thanks in advance for any info.

---

### Post by AnonCat on 2009-02-10
Nvidia cards do support 3D acceleration in Linux as long as you use the proprietary driver.  The open source driver does not allow 3D acceleration.  Ubuntu should notify you of the card and give you options for installing the proprietary driver when you install the card.  You can also use envy (sudo apt-get install envy-ng) to install the proprietary driver for you.

---

### Post by Shpega on 2009-02-10
So just to double check, before I unwrap this thing, all this just pertains to the linux drivers, the proprietary ones will work?

"nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade."

---

### Post by Temposs on 2009-02-10
Most nvidia cards support 3d acceleration, as far as I know.

Take a look at this page, which is the official nvidia page for their *nix drivers: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

This page: [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

It lists GeForce 6200 as a supported card. So, if you have a GeForce 6200, it should work. I'm not sure if the "e-GeForce" part changes anything, but it's pretty close, in any case.

---

### Post by Vadi on 2009-02-10
Does System &#8594; Administration &#8594; Hardware Drivers not suggest a driver for you?

---

### Post by Shpega on 2009-02-10
Thanks for the quick replies guys, I'll give it a shot, so I'm sure I'll be posting in a little bit on why my screen went black.:)

---

### Post by RomeReactor on 2009-02-10
Hi. Just to comment, I have an EVGA GeForce 6200 and it does indeed work as intended using the **nvidia-glx** drivers from the repositories. I suggest you uninstall the FGLRX driver and you should probably change the driver to either **vesa** or **nv** in /etc/X11/xorg.conf before installing the card.

---

