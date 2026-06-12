---
title: "Will a USB install work on any Laptop"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by MiTavis on 2009-10-17
I have a HP compact nc6000, an aspire one netbook and an HP Pavilion dv7-2173d.
I installed Ubantu 9.04 on the USB sata drive (140 GB) by removing the hard drive from the nc6000.
 
I have the following problems:
I can not play DVDs with movie player
I have no sound on the HP Pavilion
The wireless network does not work on the netbook.
 
If I fix a problem for one Laptop will it cause problems with the others.
 
I am looking for solutions to all the issues. I have seen some posts but I am not sure that there have been any true fixes

---

### Post by mbeichorn on 2009-10-17
Linux is amazingly versatile and able to be run on multiple computers, but not as efficiently as it is when it is configured for a single system.

The fact that Linux boots on both computers is amazing, just try that with Win or OSX

The best solution is of course to deploy ubuntu on all of the machines, but since you are not, you probably want to just try fixing one project at a time and backup vigorously in case an edit causes a problem on another machine.

Another alternative may be to look for a distro designed for machine swapping such as puppylinux.

As to your problems:

DVD: If it is not the hardware, try the codec at Medibuntu
Sound: Try using Synaptic to get more of ALSA, having the full audio driver may help
Wireless: try disableing and enabling networking.

Good Luck!

---

