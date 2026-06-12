---
title: "Ubuntu Installation problem on Toshiba L635 (first time installation)"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by Kalimoor on 2011-06-14
Hi, I am having a big problem on first-time installation of Ubuntu OS on my Toshiba L635-00K. I download the Ubuntu partition version, that is, the one allows you to choose between going to window or ubuntu. When I enter the interface and it says it is almost finishing copying the files, then BOOM, the interface disappeared and I'm back to the console, and it has so many lines of messages, there are too many lines, so I just select the ones with texts,

[115.757022] 	panic occured, siwtching back to text console
		BUG: scheduling while atomic: mount.ntfs/417/0x10000100
		Module linked in: ........... a lot of things that I don't know
		CPU 0
		Module linked in: ........... a lot of things that I don't know
		Pid: 417, comm: mount.ntfs Tained: G     D     2.6.38-8-generic #42-Ubuntu TOSHIBA Satellite L635/Portable PC
		........... several things that I dont know
		Process mount.ntfs (pid: 417, threadinfo ffff8800aa07a000, task ffff8800364e2dc0)
		Call Trace:
			............
		Code:
			............

and the screen just freezes right there.

I'm a noob when it comes to Operating Systems, does anyone know what kind of problem it is?

Thanks.

---

### Post by Quackers on 2011-06-14
Welcome to UF.
Those lines indicate a kernel panic.
It may be that you need to use an acpi-related boot option - some Toshiba users require one.
Try booting from the live cd and at the choice screen choose "try Ubuntu" and see if the desktop loads.
If it doesn't have a read of the link below and use one of the boot options mentioned (ie noapic, nolapic or acpi=off).
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

