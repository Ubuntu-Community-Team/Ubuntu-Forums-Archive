---
title: "realtek driver and 3.18 kernel in ubuntu 14.04 64"
date: 2015-03-22
forum: Networking &amp; Wireless
---

### Post by xigen on 2015-03-22
I want to try 3.18 and see if the rumors that my new Focusrite 6i6 usb audio interfece will 'just work' with the new kernel.

Upon installing kernel and rebooting:
[http://linuxg.net/how-to-install-kernel-3-18-6-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/]("http://linuxg.net/how-to-install-kernel-3-18-6-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/")

My networking stops working.

I then try to re-install the realtek drivers:
```

<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8168B/8111B, RTL8168C/8111C, RTL8168CP/8111CP, RTL8168D/8111D, RTL8168DP/8111DP, and RTL8168E/8111E Gigabit Ethernet controllers with PCI-Express interface.

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

		# ./autorun.sh	(as root or with sudo)

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8168
		# ifconfig -a

```


... and I get error messages.


How would you suggest I get networking back?

---

### Post by Jordy_Kroeze on 2015-07-27
Hello,

I got the same problem, its working in 3.16.44 but cant get it working in 3.18 or 3.19
Did you fixed this problem?
And how?

---

