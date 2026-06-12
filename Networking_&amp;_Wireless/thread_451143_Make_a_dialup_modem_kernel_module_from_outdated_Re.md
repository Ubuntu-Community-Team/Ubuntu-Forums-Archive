---
title: "Make a dialup modem kernel module from outdated Redhat source package"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by soliac on 2007-05-22
I'm trying to make a loadable kernel module for my dialup modem: a BCM V.92 winmodem. Broadcom released a Redhat driver a few years ago, but it was for the 2.4 Linux kernel.
[The (Redhat) source package is here]("http://support.us.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R47114&formatcnt=1&libid=0&fileid=55543"). Inside it there is, among other things, a file called "BCMSM_lib.o". How do I make a module called BCMSM.ko from that???
Attached is the contents of Broadcom's source package.

---

### Post by sdide on 2007-05-22
I can't help you there, but you might want to post this in the "Programming Talk" forum.

---

### Post by _duncan_ on 2007-05-23
If the source package was written for the 2.4 linux kernel, then compiling it will still result in a .ko module for 2.4, unless you plan to work on the source code yourself to adapt it to more recent kernel versions. Believe me, that is not an easy task even for programmers.

---

### Post by soliac on 2007-05-23
Yes, you're right. Running "make" would have resulted in a 2.4 *.o kernel module. But "make" fails. I tried looking through the Makefile, and I ran a few commands in there, but the bits of C code needed by the module won't compile, giving out huge lists of errors. I'm thinking this is a lost cause. Broadcom hasn't released any updates for a long time, I think they've just forgotten about this driver.

---

### Post by _duncan_ on 2007-05-24
The compilation errors are probably due to incompatibilities between the GCC version the driver was written in and the default GCC version of Ubuntu Edgy. I won't be surprised if you see a lot of "deprecated function" errors during "make".

I'm not familiar with your specific modem, but if you are desperate, you can try linmodems.org to see if they have updated open-source drivers for Broadcom. The link to their website is on my signature.

I had a similar problem 2 years ago when my modem came with a 2.4 kernel linux driver, but no updated drivers for recent kernels. After 2 months of searching, I went out and bought a PCI modem based on the smartlink chipset for 5 US$, downloaded the open-source driver from linmodems.org, and was on-line in less than 30 minutes of work.

---

