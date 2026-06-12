---
title: "I have found drivers for my network card, but I don't know how to install them"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by gdp77 on 2007-07-03
I got a GIGABYTE P35-DS3 (p35 chipset). Everything works with ubuntu 7.04 except the network. I have found the linux drivers for lan (Realtek 8111b) [here](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false), but I don't know how to install the driver.

Please help me. I know that u will give me some kind of listing. If u are kind enough, please explain to me what each command does, so I don't stay noob for ever. Thank u

---

### Post by Rui Pais on 2007-07-03
hi,
You need the compiler kit first.
Do on a terminal:
```
sudo apt-get install build-essential
```
then on the directory that you have the tar.bz2 file do:
```
tar xvjf r8168-8.001.00.tar.bz2
```
then go to the created directory (r8168-8.001.00/) and read the README that contain the instructions.

good luck

---

### Post by GeeZor on 2007-07-03
the guy said he doesn't have network...

---

### Post by Rui Pais on 2007-07-03
> **GeeZor said:**
> the guy said he doesn't have network...

Oops... (damn Ubuntu that make default installs without gcc :frown: )


In that case you have two ways.
Use the default install CD or get packages from network, from another box or os with internet (but this 2nd method it's much harder...)

You can add your Ubuntu Install CD to sources with:
```
sudo apt-cdrom add
```
then you can get build-essential with the apt-get command i post early.


[COLOR="Gray"]To get packages from net go [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=names&subword=1&version=all&release=all"), and download the version for your release/architecture. 
The problems are dependencies... you probably need to get most of the packages listed there (don't  which are installed by default).
[/COLOR]Try this only method if, for some reason, you don't have the install CD!

---

### Post by GeeZor on 2007-07-03
that should indeed do the trick  :)

---

### Post by gdp77 on 2007-07-11
ok guys, thank you for helping. I managed to install build essentials from Ubuntu cd. The problem is that drivers from realtek's site refuse to install, as r1000.ko file is missing... 

Searching for a while in the net I found out that new linux kernel 2.6.19 supports realtek 8111b. The problem is that I don't have internet connection in order to upgrade my kernel 2.6.15 (feisty). So I need to boot from windows, download the kernel and then install it in ubuntu.

I am a noob, so I need a how-to. Any links available please? How can I install new kernel without internet connection?

---

### Post by 5-HT on 2007-07-11
> **gdp77 said:**
> Searching for a while in the net I found out that new linux kernel 2.6.19 supports realtek 8111b. The problem is that I don't have internet connection in order to upgrade my kernel 2.6.15 (feisty). So I need to boot from windows, download the kernel and then install it in ubuntu.

I am a noob, so I need a how-to. Any links available please? 
Here's a guide for compiling a vanilla kernel from kernel.org: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) > **gdp77 said:**
> How can I install new kernel without internet connection? Once you get the kernel tarball over to your ubuntu partition, you won't need any internet connection for the compilation.

OTOH: You could always compile your own Ubuntu kernel by grabbing the kernel source and any needed dependencies from packages.ubuntu.com (select a kernel source >2.6.19 though). 
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

FWIW: I wouldn't simply download a newer pre-built kernel from packages.ubuntu.com as that could lead to breakage. You can give it a shot though and may get lucky.

---

### Post by Rui Pais on 2007-07-11
Hi again.

yes compiling a kernel could solve the problem. But to compile the kernel you may need to get more packages yet (like bin86 and kernel-package)  from the net and manually install them, not to mention that compiling a kernel is not an easy task for someone without experience (something that i advise to do for fun and learning, but not for solve a situation).

Much more easy is simply compile the kernel module you need. 
Have you done the instruction on the README file? Do you get any error during compilation?


Getting the kernel precompiled is a nice idea, you can get it from here:
[http://packages.ubuntu.com](http://packages.ubuntu.com)

you will need:
[linux-image-2.6.20-16-generic]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-image&searchon=names&subword=1&version=feisty&release=all")
and
[linux-headers-2.6.20-16-generic]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-headers&searchon=names&subword=1&version=feisty&release=all")

But i'm not sure if i understand what Ubuntu version do you have. 
You say you have 7.04 but your kernel is a 2.6.15... thats a 6.04 (Dapper) one. 
Have you done an upgrade somehow from dapper? Are you sure that you don't have the correct kernel?
Check:
```
uname -a
```
```
ls /boot/vmlinuz-*
```
```
lsb_release -c
```

---

### Post by gdp77 on 2007-07-11
> You say you have 7.04 but your kernel is a 2.6.15... thats a 6.04 (Dapper) one. 

That was a typo. I got 2.6.20-15. The latest is 2.6.20-16 ? I'll try what u suggest and I hope it works... Otherwise I have to wait untill Ubuntu 7.10...


> Much more easy is simply compile the kernel module you need.
Have you done the instruction on the README file? Do you get any error during compilation?

yes I've done the procedure and I got an error. Stand by a few minutes and I'll post a print-out then. Maybe u can help me before I try to compile kernel.

---

### Post by Rui Pais on 2007-07-11
> **gdp77 said:**
> That was a typo. I got 2.6.20-15. The latest is 2.6.20-16 ? I'll try what u suggest and I hope it works... Otherwise I have to wait untill Ubuntu 7.10...

Ah, ok. I doubt it that 20-16 has something that 20-15 don't. It's just a security update.
Do you know whats exactly the name of the kernel module you need (i'm a little short on time to do a search...) 
its r1000, r8168 or r8111?



> 

yes I've done the procedure and I got an error. Stand by a few minutes and I'll post a print-out then. Maybe u can help me before I try to compile kernel.
Ok, no prob.

---

### Post by gdp77 on 2007-07-11
> Ah, ok. I doubt it that 20-16 has something that 20-15 don't. It's just a security update.
Do you know whats exactly the name of the kernel module you need (i'm a little short on time to do a search...)
its r1000, r8168 or r8111?

I need [this](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)



Ok. These are the instructions in order to install driver.

> <Linux device driver for Realtek Ethernet controllers>

  This is the Linux device driver released for RealTek Ethernet controllers, which are listed as following.
	1. RTL8169S/SB/SC (Gigabit Ethernet with PCI interface)
	2. RTL8168B (Gigabit Ethernet with PCI-Express interface)
	3. RTL8101E (Fast Ethernet with PCI-Express interface)

<Requirements>

  - kernel source tree (supported versions 2.4.x)
  - compiler/binutils for kernel compilation



<Quick install with proper kernel settings>

  Unpack the tarball :
	tar vzxf r1000_vX.YZ.tgz

  Change to the directory:
	cd r1000_vX.YZ

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a




<Force Link Status>

1. Force the link status when insert the driver.
	If the user is in the path ~/r1000, the link status can be forced to one of the 5 modes as following command.

	#insmod ./src/r1000.o speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

	,where
		SPEED_MODE	= 1000	for 1000Mbps
				= 100	for 100Mbps
				= 10	for 10Mbps
		DUPLEX_MODE	= 0	for half-duplex
				= 1	for full-duplex
		NWAY_OPTION	= 0	for auto-negotiation off
				= 1	for auto-negotiation on
	For example:
	#insmod ./src/r1000.o speed=100 duplex=0 autoneg=0
	will force PHY to operate in 100Mpbs Half-duplex.

2. Force the link status by using ethtool.
	a. Insert the driver first.
	b. Make sure that ethtool exists in /sbin.
	c. Force the link status as the following command.

	#ethtool -s eth? speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

	,where
		SPEED_MODE	= 1000	for 1000Mbps
				= 100	for 100Mbps
				= 10	for 10Mbps
		DUPLEX_MODE	= half	for half-duplex
				= full	for full-duplex
		NWAY_OPTION	= off	for auto-negotiation off
				= on	for auto-negotiation on


this is what happens when i type ```
sudo make clean modules
```

> george@linux-desktop:~/Desktop/r1000_v1.06$ sudo make clean modules
Password:
make -C src/ clean
make[1]: Entering directory `/home/george/Desktop/r1000_v1.06/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags
make[1]: Leaving directory `/home/george/Desktop/r1000_v1.06/src'
make -C src/ modules
make[1]: Entering directory `/home/george/Desktop/r1000_v1.06/src'
make -f Makefile_linux24x
cc1: error: /lib/modules/2.6.20-15-generic/build/include/linux/modversions.h: No such file or directory
make[2]: Entering directory `/home/george/Desktop/r1000_v1.06/src'
gcc -mcmodel=kernel -mno-red-zone -DLINUX -D__KERNEL__ -DMODULE -O2 -pipe -Wall -I/lib/modules/2.6.20-15-generic/build/include -I. -DMODVERSIONS -DEXPORT_SYMTAB -include /lib/modules/2.6.20-15-generic/build/include/linux/modversions.h -D__SMP__ -c r1000_n.c -o r1000_n.o 
cc1: error: /lib/modules/2.6.20-15-generic/build/include/linux/modversions.h: No such file or directory
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/module.h:10,
                 from r1000.h:1,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h:77: error: &#8216;CONFIG_X86_L1_CACHE_SHIFT&#8217; undeclared here (not in a function)
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h:77: error: requested alignment is not a constant
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h:233: error: requested alignment is not a constant
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/kobject.h:25,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/module.h:17,
                 from r1000.h:1,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/rwsem.h:24:65: error: asm/rwsem.h: No such file or directory
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/module.h:17,
                 from r1000.h:1,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/kobject.h:174: error: field &#8216;rwsem&#8217; has incomplete type
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/memory_hotplug.h:7,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/mmzone.h:443,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.20-15-generic/build/include/asm/local.h:4,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/module.h:19,
                 from r1000.h:1,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/notifier.h:62: error: field &#8216;rwsem&#8217; has incomplete type
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/mm.h:4,
                 from /lib/modules/2.6.20-15-generic/build/include/asm/pci.h:8,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/pci.h:746,
                 from r1000.h:2,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/mm.h:4,
                 from /lib/modules/2.6.20-15-generic/build/include/asm/pci.h:8,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/pci.h:746,
                 from r1000.h:2,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_msecs&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:274: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:274: error: for each function it appears in.)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:280:46: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_usecs&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:285: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:293:46: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;msecs_to_jiffies&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:298: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:306:46: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;usecs_to_jiffies&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:311: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;timespec_to_jiffies&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:330: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:332: error: &#8216;SHIFT_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_timespec&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:349: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;timeval_to_jiffies&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:371: error: &#8216;SHIFT_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:371: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_timeval&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:387: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_clock_t&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:401: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;clock_t_to_jiffies&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:412: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_64_to_clock_t&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:432: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/mm.h:4,
                 from /lib/modules/2.6.20-15-generic/build/include/asm/pci.h:8,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/pci.h:746,
                 from r1000.h:2,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/sched.h: At top level:
/lib/modules/2.6.20-15-generic/build/include/linux/sched.h:326: error: field &#8216;mmap_sem&#8217; has incomplete type
/lib/modules/2.6.20-15-generic/build/include/linux/sched.h: In function &#8216;dequeue_signal_lock&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/sched.h:1309: warning: implicit declaration of function &#8216;local_irq_save&#8217;
/lib/modules/2.6.20-15-generic/build/include/linux/sched.h:1311: warning: implicit declaration of function &#8216;local_irq_restore&#8217;
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/fs.h:358,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/mm.h:15,
                 from /lib/modules/2.6.20-15-generic/build/include/asm/pci.h:8,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/pci.h:746,
                 from r1000.h:2,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/quota.h: At top level:
/lib/modules/2.6.20-15-generic/build/include/linux/quota.h:290: error: field &#8216;dqptr_sem&#8217; has incomplete type
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/mm.h:15,
                 from /lib/modules/2.6.20-15-generic/build/include/asm/pci.h:8,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/pci.h:746,
                 from r1000.h:2,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/fs.h:552: error: field &#8216;i_alloc_sem&#8217; has incomplete type
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/mm.h:15,
                 from /lib/modules/2.6.20-15-generic/build/include/asm/pci.h:8,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/pci.h:746,
                 from r1000.h:2,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/fs.h:916: error: field &#8216;s_umount&#8217; has incomplete type
In file included from /lib/modules/2.6.20-15-generic/build/include/asm/pci.h:8,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/pci.h:746,
                 from r1000.h:2,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/mm.h: In function &#8216;lowmem_page_address&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/mm.h:539: warning: implicit declaration of function &#8216;__page_to_pfn&#8217;
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/pci.h:746,
                 from r1000.h:2,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/asm/pci.h: In function &#8216;pci_dac_dma_to_page&#8217;:
/lib/modules/2.6.20-15-generic/build/include/asm/pci.h:104: warning: implicit declaration of function &#8216;__pfn_to_page&#8217;
/lib/modules/2.6.20-15-generic/build/include/asm/pci.h:104: warning: return makes pointer from integer without a cast
In file included from /lib/modules/2.6.20-15-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.20-15-generic/build/include/linux/netdevice.h:568,
                 from r1000.h:3,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/irq.h: At top level:
/lib/modules/2.6.20-15-generic/build/include/linux/irq.h:172: error: requested alignment is not a constant
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/netdevice.h:568,
                 from r1000.h:3,
                 from r1000_n.c:5:
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h: In function &#8216;cli&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:204: warning: implicit declaration of function &#8216;local_irq_disable&#8217;
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h: In function &#8216;sti&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:208: warning: implicit declaration of function &#8216;local_irq_enable&#8217;
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h: In function &#8216;save_flags&#8217;:
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:212: warning: implicit declaration of function &#8216;local_save_flags&#8217;
r1000_n.c: At top level:
r1000_n.c:52: error: expected &#8216;)&#8217; before string constant
r1000_n.c:53: error: expected &#8216;)&#8217; before string constant
r1000_n.c:54: error: expected &#8216;)&#8217; before string constant
r1000_n.c: In function &#8216;r1000_init_board&#8217;:
r1000_n.c:274: warning: implicit declaration of function &#8216;pci_request_regions&#8217;
r1000_n.c: In function &#8216;r1000_init_one&#8217;:
r1000_n.c:511: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
r1000_n.c:550: warning: implicit declaration of function &#8216;pci_release_regions&#8217;
r1000_n.c: In function &#8216;r1000_open&#8217;:
r1000_n.c:672: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
make[2]: *** [r1000_n.o] Error 1
make[2]: Leaving directory `/home/george/Desktop/r1000_v1.06/src'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/george/Desktop/r1000_v1.06/src'
make: *** [modules] Error 2

And this is what happens after ```
sudo make install
```

> george@linux-desktop:~/Desktop/r1000_v1.06$ sudo make install
make -C src/ install
make[1]: Entering directory `/home/george/Desktop/r1000_v1.06/src'
install -m 644 -c r1000.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/
install: cannot stat `r1000.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/george/Desktop/r1000_v1.06/src'
make: *** [install] Error 2



That's why I am trying to upgrade kernel. Driver doesn't seem to work...

---

### Post by Rui Pais on 2007-07-11
ok i'm a little short in time right now and for the next 1 or 2 hours... I try to help then.

Mean while, it fails to compile cause thats an old source for 2.4 kernels, you are using 2.6. 
Where do you get the source? check if it as more update sources. On your 1st post you mention another version (i checked and seems to be removed from download site)

Do you know the exact model of your net card?

They mention too, on README, a r8169. MAybe that works with your card. Those drivers are very generic.
Try to load it with:
```
sudo modprobe r8169
```

check with:
```
lsmod | grep r8169
```

If is loaded then check what kernel says about card:
```
lspci | grep net
```

good luck.
(Later we can try to compile some sources if we can find something for 2.6)

---

### Post by gdp77 on 2007-07-11
I did what u said. (I don't have a clue what I am doing though). 

> george@linux-desktop:~$ sudo modprobe r8169
Password:
george@linux-desktop:~$ lsmod | grep r8169
r8169                  35720  0 
george@linux-desktop:~$ lspci | grep net
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
george@linux-desktop:~$ 


By the way in motherboard's manual it says that the lan is the Realtek 8111B

---

### Post by gdp77 on 2007-07-11
Ok.... I pinpoined the problem :

> As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)

Second edit: Powering off and unplugging the machine for a few seconds (around 10 usually does it) seems to reset the card, so it will work in Linux again until you boot Windows again. 


[detailed review of the problem](http://gentoo-wiki.com/HARDWARE_RTL8168)


Also, realtek has removed the 2.6.x drivers from their site. I already emailed the webmaster and we will see what happens.

---

### Post by gdp77 on 2007-07-11
YES!!!! I enabled wake-on-lan after shutdown and I now have internet from ubuntu... This is my first post :)

So, until realtek release drivers for 2.6.x kernel, problem solved with this workaround.

---

### Post by Rui Pais on 2007-07-11
> **gdp77 said:**
> YES!!!! I enabled wake-on-lan after shutdown and I now have internet from ubuntu... This is my first post :)

So, until realtek release drivers for 2.6.x kernel, problem solved with this workaround.

Congratulations!! 
for your working network and for your research :) Excellent job! 

I knew that there were issues with that cards but didn't know (or can ever imagine) it goes with options of  Windows on wake options ... :shock:
I learn something today :) 

About the "magic" commands, 
modprobe -> load module (drivers)
lsmod -> list modules 
lspci -> list pci interface/devices detected by kernel
grep just cut output that don't contain expression passed on grep command (or it will outputs loads of lines)

Just a last tip, 
If the module is not automatically detected/loaded at boot time, you don't need to do that manually each time,
just add a line to /etc/modules with only:
r8169

have fun around

---

### Post by fno on 2007-07-13
Can add to this that the r8169 drivers for the 8168 chip is really, really buggy. Even with a fresh kernel like the 2.6.22-8 one, samba doesn't play very well at all as a server.

---

### Post by PowerlessRacing on 2007-08-15
I'd just like to verify this solution for anyone that came across this post during a search (as I did).  I was slightly concerned after reading this thread that I would have to recompile the kernel.  No kernel modification or recompilation was necessary.

Enabling the "Wake-on-LAN after Shutdown" option in the Windows XP (32 bit home version - last one I was willing to pay for) and then a reboot into Ubuntu 64-bit immediately resolved the LAN issue with a vanilla install (no kernel modifications required).

Edit: I did install the drivers from Gigabyte's website for the LAN when I was booted into Windows before I had installed Ubuntu.  I don't know if that makes a difference for anyone.  

HW:
M/B: Gigabyte P35C-DS3R w/ onboard LAN
CPU: Intel Core 2 Duo E6750 @ 2.66GHz, no overclocking
CPU Cooler: Zalman CNPS9500AT Cooling Fan
Corsair DDR2 XMS2 2GByte Matched Memory Pair (1GB x 2)
Video: MSI NX8600GT 256MB OC Edition

Good Luck!

---

