---
title: "Realtek PCIE Gigabit Lan 10/100/1000 driver."
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by MCope on 2007-12-07
I was able to down load the tar and extract.   I attempted to perform the make on the file based on what was listed.  I got as far as the end of the last comment.
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8168B/8111B 
	and RTL8168C/8111C, Gigabit Ethernet controllers with PCI-Express 
	interface.

<Requirements>

	- Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
	- Compiler/binutils for kernel compilation

<Quick install with proper kernel settings>

	Unpack the tarball :
		# tar vjxf r8168-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8168-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8168.ko (or r8168.o in linux kernel 2.4.x)

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8168
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate the ethX.
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

Under my wired connections,it displays the driver as grayed out.  For whatever reason I can't seem to get it activated.

Any suggestions would greatly be appreciated.  If there is a complied version anyone is aware of please let me know.
Thanks,
Mike

---

### Post by fineas on 2007-12-08
There are some issues with this specific card. Check here [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
it might be helpful

---

