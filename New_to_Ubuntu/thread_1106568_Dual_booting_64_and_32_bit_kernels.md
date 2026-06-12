---
title: "Dual booting 64 and 32 bit kernels"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by jrcraft on 2009-03-25
I have Ubuntu 8.10 AMD64 installed on my new system. I'd like to run Boxee and other 32-bit programs. Does anyone know of a way to install x86 without killing my current installation? I ran a search and didn't come up with anything 'cept dual booting with Windows.

---

### Post by Old_Grey_Wolf on 2009-03-25
Since you are running a 64-bit OS, some 32-bit applications may not work with the 64-bit OS. I would try running the 32-bit application on the 64-bit OS; not supported doesn't mean it will not work. If the 32-bit application will not run on a 64-bit OS, then you can try several things. Dual boot with a 64-bit OS and a 32-bit OS. Both the 64-bit and 32-bit OS could be Ubuntu. You could also try using a Virtualization product like VirtualBox, VMware, etc., and see if the 32-bit application will work in a 64-bit Virtualized host environment.

---

### Post by 3rdalbum on 2009-03-25
If Boxee requires 32-bit libraries, you can get these by using the Getlibs utility.

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by jrcraft on 2009-03-25
How do you install 32-bit Ubuntu in a dual boot with 64-bit? Do I need separate partitions?

Boxee is weird. I've installed the 32-bit libraries for other software, but this one is just really complicated to get working. Even if you go through all of the installation recipes for Boxee on AMD64, it isn't necessarily even going to work anyway. So I think a 32/64 dual-boot may be a good alternative.

---

### Post by miegiel on 2009-03-25
> **jrcraft said:**
> How do you install 32-bit Ubuntu in a dual boot with 64-bit? Do I need separate partitions?

Yes, root partitions need to be separate. But you can use a combined home partition and swap partition.

---

