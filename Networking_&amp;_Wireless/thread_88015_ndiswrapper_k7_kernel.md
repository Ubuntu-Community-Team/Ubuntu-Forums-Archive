---
title: "ndiswrapper k7 kernel"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by milstead on 2005-11-09
I am using ndiswrapper.
It seems to work well on the i386 kernel (2.6.12-9-386) but does not work when I load a k7 kerrnel.

I am using a Sempron 64 chip. And no - I don't want to run a 64 bit OS!

Any ideas or similar experience ?

Timie Milie.

---

### Post by Kyral on 2005-11-09
IIRC, NDiswrapper is a kernel module right (Its been a LONG time since I used it), so if you change kernels you have to recompile it (or download a version) so that it will interface with the new kernel

---

### Post by milstead on 2005-11-09
Yes, it is a module. Yes  I have downloaded and installed the correct module for the different kernel. It just doesn't work.

Timie Milie.

---

### Post by ivanhelguera on 2005-11-09
For what it's worth, I did not have to do anything after switching to a k7  kerne7 - I just installed linux-k7, checked that eveyting ran as before (except for the kubuntu, instead of ubuntu, splash screen), and unloaded the linux-386. I'm using an athlon XP-M 2800. 
Best, 
IH

---

### Post by CamB on 2005-11-14
Have you got 1gb (or more) of memory by any chance?

I'm not sure if it has been fixed in the last couple of months, but as of August ndiswrapper didn't support highmem (which is supported by the k7 kernel, if you have that much ram). I worked around the problem by adding mem=900mb to the kernel startup line in grub.

---

