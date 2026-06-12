---
title: "grsecurity installation"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by Fika on 2010-03-16
Hi

Can someone guide me how to install the grsecurity suite for ubuntu 9.10? I have tried the tar and gz packages but I am not familiar enough with linux apparently to make it work. This a total noob question but is there some way I can click and install grsecurity? 

Thank you

---

### Post by chaanakya_chiraag on 2010-03-18
You need to do something called recompile the kernel, which I would not advise at this stage of your Linux "schooling". If you really want to though, I might try it sometime in the future, so I'll tell you the exact steps once/if I get it working.

---

### Post by box2 on 2010-09-25
This has probably been answered elsewhere, but I'm doing it right now myself so might as well write it down too.

There are ubuntu binary packages (.deb's) for it here:
[http://kernelsec.cr0.org/]("http://kernelsec.cr0.org/")

_**Go to the bottom and it will tell you to**_:
1) Add ```
deb http://ubuntu.cr0.org/repo/ kernel-security/
``` to your /etc/apt/sources.list 
2) Download their GPG key
3) apt-key add kernel-security.asc
4) apt-get update
5) apt-get install linux-image-grsec

You're also going to want to install the gradm2 package for administering grsecurity's RBAC.  You will then have to reboot into your new kernel for changes to take effect.  FYI, cr0.org is linked to directly from grsecurity.net so you can probably trust that they're legit.

These .deb's are not incredibly new, but they can probably get you up and running pretty quickly.  For me, I had an error ```
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27.29-4-grsec_1.0_i386.deb (--unpack):
 trying to overwrite '/lib/firmware/kaweth/trigger_code.bin', which is also in package linux-firmware 0:1.34.1
```

I didn't really feel going through the effort of fixing an older kernel than what I'm already running... and not only that I want more configuration options which only come from when you are compiling your kernel, so for that I need the source patch.  The source's are made for patching against the vanilla linux kernel (not the version optimized by the ubuntu team), but with some practice you may be able to use grsec sources to patch against an ubuntu kernel too.

For now I'm just going to try the latest testing release of grsec here:
[http://grsecurity.net/test.php]("http://grsecurity.net/test.php")

I also need a matching kernel version for one this patch.  [grsecurity-2.2.0-2.6.32.22-201009241805.patch]("http://grsecurity.net/test/grsecurity-2.2.0-2.6.32.22-201009241805.patch") is the latest grsec at the time of this writing and the filename means it is version 2.2.0 of grsec for kernel [2.6.32.22]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.22.tar.bz2") and was released on 2010-09-24 at 6:05 PM.

Compile instructions to come...

---

### Post by box2 on 2010-09-25
One thing that's good during longer compiles and stuff is to use screen.  This will save you in case your network connection drops, you won't lose the terminal that is compiling to garbage collection.  On the local console it's good too because you can open multiple terminals and do other things while your compile is going on.

1) sudo apt-get install screen
2) echo "term xterm-color" >> ~/.screenrc
(This will give colors to your screen terminal.)
3) screen
4) When you are back into a terminal prompt, continue with instructions below.  If you want to detach from the screen session, press ctrl+a (also written as ^a), then press d.  You will be dropped back into your original terminal.  To get back to what is going on inside the screen, use screen -r (for reattach).  If you are ever disconnected from the computer, you can log back in and use screen -r to reattach where you left off.

[GNU Screen]("http://www.gnu.org/software/screen/manual/screen.html") is a really great utility and has a huge amount of functionality, read the manpage for it sometime.

Ok compiling a vanilla kernel with ubuntu, first thing you need is the compiling tools:
1) sudo apt-get install kernel-package fakeroot build-essential ncurses-dev

And now the sources:
2) wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.22.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.22.tar.bz2)
3) wget [http://grsecurity.net/test/grsecurity-2.2.0-2.6.32.22-201009241805.patch](http://grsecurity.net/test/grsecurity-2.2.0-2.6.32.22-201009241805.patch)

Extract the kernel source tree:
4) tar -xvf linux-2.6.32.22.tar.bz2
5) cd linux-2.6.32.22

Now copy the configuration for your current kernel to the new source tree:
6) cp /boot/config-`uname -r` .config

These options were set by ubuntu when it was installing after it scanned your hardware.  It's fun to look at them, but don't change anything yet.  There is a nice graphic interface for that.  Now using this .config as a base we are going to generate a new .config that matches all the features of the source kernel:
7) make oldconfig

If it asks you questions and you don't know what to do, pressing enter is the safe choice.  If you want to try new things and know what you are adding, give it a try.  We want to make a backup of this so:
8) cp .config ../vanilla-kernel.config

Now we copy our patch into the tree and apply it:
9) cp ../grsecurity-2.2.0-2.6.32.22-201009241805.patch .
10) patch < grsecurity-2.2.0-2.6.32.22-201009241805.patch -p1

Now we look at all the modules and etc that are built into our kernel.  This is where you add or remove functionality, and also **where we set our grsec and pax options**.
11) make menuconfig

Look around a bit but don't remove things if you don't know what they are.  The only thing you gain from a smaller kernel is less functionality, and the amount of RAM it takes up is pretty insignificant.  With that said, if this is for a network server you probably don't need support for infrared, bluetooth, or sound.

12) Go to "Security options --->"

This is where you can go into both Grsecurity and PaX and enable the features you want.  A great document that explains all the options is [here]("http://en.wikibooks.org/wiki/Grsecurity/Appendix/Grsecurity_and_PaX_Configuration_Options").  Read through this more than once if you don't know exactly what options you want.  The general rule here is: if you don't know what something does, don't mess with it.  That being said, you may be coming back to this screen to recompile your kernel if you don't get it exactly the way you want.

This is the way I configured mine:

Grsecurity
-> * Grsecurity
--> Security Level (Medium)

I use Medium because I install a lot of custom software that might be written poorly and at higher settings grsec will break things like that.  A production server should be on High if at all possible.

-> Address Space Protection
--> * Harden module auto-loading
-> Role Based Access Control Options
--> * Hide kernel processes
--> (5) Maximum tries before password lockout
-> Filesystem Protections
--> * Proc restrictions
--> * Restrict /proc to user only
--> * Enforce chdir("/") on all chroots
--> * Deny sysctl writes
-> Kernel Auditing
--> * Fork failure logging
-> Executable Protections
--> * Dmesg(8) restriction
-> Network Protections
--> * TCP/UDP blackhole and LAST_ACK DoS prevention

PaX
-> * Enable various PaX features
-> PaX Control
--> * Use ELF program header marking
-->  MAC system integration (direct)
-> Non-executable pages
--> * Enforce non-executable pages
--> * Paging based non-executable pages
--> * Emulate trampolines
--> * Restrict mprotect()
-> Address Space Layout Randomization
--> * Address Space Layout Randomization
--> * Randomize kernel stack base
--> * Randomize user stack base
--> * Randomize mmap() base (and also everything underneath)
-> Miscellaneous hardening features
--> * Prevent various kernel object reference counter overflows
--> * Bounds check heap object copies between kernel and userland

Now exit all the way and save your changes.  Here comes compiling.  First we make sure everything is clean, **do this before every time you try to compile**:
1) make-kpkg clean

And now we compile.  In this step we are also telling the compiler (make-kpkg) to use all the CPUs or CPU cores as the computer has:
2) CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version "grsec2.2.0" kernel_image

This may take a while.  If you want some fun while compiling and you are inside of a GNU Screen, you can create a new screen terminal by pressing ^a then c.  In the new terminal run htop.  You can switch back to your compiling terminal at any time by pressing ^a twice.  For me this  will take a very long time because this computer is old old old.  So I will post again in a few hours.  If you have errors during your compile, read the errors and maybe paste them into google to figure out how to solve it.

---

