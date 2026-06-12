---
title: "Load ubuntu on an old iMac"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by dunklegend on 2010-03-12
I have an old iMac and I want to load Ubuntu on it, so it would get a new life.

The kind of iMac is the one where the CPU is inside the monitor.

Anyone knows how to do it?

Or maybe point me to a website that has these instructions, I searched in google but I couldn't find anything that works.

---

### Post by srs5694 on 2010-03-12
Is this iMac a PowerPC unit? If so, check [here](https://wiki.ubuntu.com/PowerPC) for some basic information on running Ubuntu on PowerPC systems. I've never run Ubuntu on a PowerPC Mac, but it looks as if it's an unofficial port rather than an official version. Personally, I do have a Debian PowerPC installation on an ancient (10-year-old) iMac. I wouldn't want to run a modern distribution with a modern desktop environment on a system that old -- the modern software is just too demanding of RAM, CPU time, and even disk space. Something a few years more recent (say, 2005-ish) should be OK, though.

For the most part, Linux (any Linux) on PowerPC works just like Linux on x86 or x86-64. The biggest differences are in disk partitioning and booting. PowerPC Macs use a partitioning scheme known as the Apple Partition Map (APM), vs. the Master Boot Record (MBR) system used on most x86 and x86-64 systems. This necessitates using different partitioning software, or at least different partitioning options. Assuming the PowerPC Ubuntu port is done well, chances are this won't be an obtrusive difference.

The boot loader handles the boot process. On x86 and x86-64 systems, this is usually handled by GRUB, which is installed automatically. PowerPC requires a different boot loader. It will also probably be installed automatically by the OS installer, but you should definitely pay careful attention to the documentation and/or online prompts and help concerning this step.

---

### Post by audiomick on 2010-03-12
you should perhaps post in the "apple users" part of the forum
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)
and read the second sticky at the top.

---

