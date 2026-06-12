---
title: "Can't install NFORCE driver"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by matheus on 2005-10-19
Hello people I am fairly new to Linux and totally new to Ubuntu, so please have patience.

I have a fresh Ubuntu 5.10 (for AMD64) install and it didn't recognize the built-in network card. My system is a shuttle PC model SN85G4v3 with NVIDIA nForce&#8482;3 250 Northbridge ([http://global.shuttle.com/Product/Barebone/SN85G4%20V3.asp](http://global.shuttle.com/Product/Barebone/SN85G4%20V3.asp)).

I tried installing the drivers available from the NVIDIA site. I downloaded the NFORCE-Linux-x86_64-1.0-0306-pkg1.run file and ran it as root. After the license screen, it says:

**No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface.**

I clicked OK and proceeded. The next screen tells me that "gcc-version-check failed", it seems the kernel was compiled with 3.4 and my current compiler is gcc 4.0. I am not sure how to revert to 3.4 nor if this is necessary, so I just ignored the warning and proceeded.

The installer then builds the module name "nvnet.ko" (and I checked that it exists in the filesystem), but after building it show a screen saying:

**ERROR: Unable to load the kernel module 'nvnet.ko'. This is most likely because the kernel module was built using the wrong kernel source files. Please make sure you have installed the kernel source files for your kernel; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' rpm installed. If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' commandline option.**

Well, I am stuck at this point, because none of the packages available on Synaptic seem to be kernel sources (I did find kernel headers but I suppose this is not the same thing).

I believe it should be important to note that my kernel is 2.6.12-9-amd64-generic.

I appreciate any help solving this.

Matheus

---

### Post by stiiixy on 2005-12-16
I have this problem as well! The network works, but can't install the nvidia nforce drivers (32bit). It's a GigaByte 7NF-RZ (yeah an el cheapo yum-cha board). And I'm quite a n00b as well. :rolleyes:

---

### Post by nuclearfly on 2006-01-31
Hey guys, I seem to be having this same thing.  I get the kernel is differnt version message, but then after that all I get is a "driver installation has failed" message. 

Is there anyone with ideas on this?

---

