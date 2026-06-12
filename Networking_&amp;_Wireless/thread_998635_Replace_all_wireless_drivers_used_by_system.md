---
title: "Replace all wireless drivers used by system"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by Geomancer626 on 2008-12-01
How do I go about replacing all the wireless NIC drivers used by Intrepid Ibex with the ones used by Hardy Heron? Is it even possible? I know it has something to do with kernel modules, but I don't know which ones or how to replace them.

---

### Post by Ayuthia on 2008-12-01
I am sure that it is possible, but it would not be easy.  You would have to get the source for the kernel modules (depends on which wireless card you have), find out the differences between the current source and the one in Hardy, patch the current kernel module with the differences, try to compile.  There is a good chance that you will run into errors just because the code to the kernel has changed.

This is most likely not something that a person coming into Linux would want to try.  You will need some knowledge of C and the kernel (along with compiling kernels in Debian/Ubuntu) to figure out what is happening.  You will also need to know what modules your wireless card is using so that you can track down the source.  The source could be in the linux-image, linux-restricted-modules, linux-ubuntu-modules, linux-backport-modules, and possibly others.

---

### Post by Geomancer626 on 2008-12-01
Wow, it may just be easier for me to downgrade to 8.04 then. I have an Alfa AWUSO36H. The driver was broken after updating to 8.10.

---

