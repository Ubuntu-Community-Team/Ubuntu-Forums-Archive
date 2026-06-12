---
title: "Network card not in kernel, but I have kernel module source...help"
date: 2004-11-09
forum: Networking &amp; Wireless
---

### Post by killerfish on 2004-11-09
Hello,

Just realized this sub-forum existed...  I posted this up one level as well...

I'm new to Ubuntu and Debian, but not Linux. My motherboard is the ASRock Combo-Z it's based on the ULI 1689 chipset (ALi) . Everything is detected and working perfectly except my integrated network card. ...I expected this. BUT, I have the source code for my network driver straight from ULI . I have had it working in the past on Gentoo because I had access to the Kernel Source directly on the install CD.

To compile & install the network driver, I basically need to patch the kernel and compile and install it as a Module.. Since I do not currently have network access, how the heck to I get the ubuntu kernel source to my PC? Is there somewhere I can download it?

thanks!
KF

---

### Post by az on 2004-11-09
The kernel source is on your cd.  Just use synaptic.

However, you need to configure it to match the kernel that you are using.  You need to copy the /boot/config-2.6.1whatever... file to the kernel source directory and name it .config.  Read up on building your own kernel.

You can make it easy on yourself and install just the kernel-headers and work with those.

install these packages:

build-essential linux-headers-2.6-386 kernel-kbuild-2.6-3

Maybe also try module-assistant.

Use the kernel-headers directory as your kernel source directory when prompted...

---

### Post by killerfish on 2004-11-09
Thanks!  It's compiling now.  Looks like it will work!  Time to get to know this distro!

---

### Post by killerfish on 2004-11-09
bingo! Posting from my machine now... Thanks!

---

### Post by technaut2005 on 2005-04-02
[QUOTE=killerfish]bingo! Posting from my machine now... Thanks![/QUOTE]
Think you might be able to share the module with me as I use the same motherboard as you do???

---

