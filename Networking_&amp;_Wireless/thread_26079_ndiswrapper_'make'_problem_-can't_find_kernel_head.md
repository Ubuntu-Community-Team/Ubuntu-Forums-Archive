---
title: "ndiswrapper 'make' problem -can't find kernel headers/source"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by EndersGame on 2005-04-11
OK, this should be really simple, so I don't know if I messed something up somewhere or what.  I'm trying to install ndiswrapper to get my wireless to work.  I downloaded ndiswrapper-source and am trying to follow the instructions on their website.  However, I keep getting an error saying something like
> Can't find kernel sources in /lib/modules/2.6.10-5-386/build; give the path to kernel sources with KSRC=<path> argument to make

I'm sure this is something silly.  Can anyone help?

Thanks.

---

### Post by alastair on 2005-04-11
Install the kernel headers for your kernel version (seemingly 2.6.10-5-386). Search Synaptic (or similar) for "headers".

---

### Post by az on 2005-04-11
Here:

[http://apqi.com/ubuntu/ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb](http://apqi.com/ubuntu/ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb)
[http://apqi.com/ubuntu/ndiswrapper-utils_1.1-1_i386.deb](http://apqi.com/ubuntu/ndiswrapper-utils_1.1-1_i386.deb)

I assume that the version included on your cd is not new enough?

---

### Post by EndersGame on 2005-04-12
Ahh...got it working now!  Thanks!

---

### Post by juice381 on 2005-07-04
Hello everyone, I am very New to linux but am an extremely fast learner. If anyone could help me that would be great and feel free to speack technically as I am a network engineer and speak the language fluently. I am having the sam problem game had I dlled the 2.6.10 from the link azz provided but have no idea on how to install it any help would greatly be appreciated.

---

