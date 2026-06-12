---
title: "[SOLVED] Anyone tired the new GRUB version (grub-1.96.tar.gz)?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by looi76 on 2008-12-18
Hi everyone,
I just wanted to know if anyone has tired the new grub version ([grub-1.96.tar.gz]("ftp://alpha.gnu.org/gnu/grub/grub-1.96.tar.gz")). 
What is the difference between GRUB and GRUB2?

---

### Post by logos34 on 2008-12-18
> **looi76 said:**
> . 
What is the difference between GRUB and GRUB2?

Here's some stuff that might interest you:

> But GRUB has been showing its age: It can't handle RAID and LVM volumes; it's stuck in ASCII; it can't boot to a CD or DVD; and the underlying code is messy. So the fine folks at GNU spent the past few years writing a totally new GRUB. This new GRUB is called GRUB2, and it is based on the old PUPA project. GRUB Legacy is version 0.9x, and GRUB2 is version 1.9x.

[http://www.serverwatch.com/tutorials/article.php/3733046](http://www.serverwatch.com/tutorials/article.php/3733046)


> 
GRUB 2 targets at the following goals:

    * Scripting support, such as conditionals, loops, variables and functions.
    * Graphical interface.
    * Dynamic loading of modules in order to extend itself at the run time rather than at the build time.
    * Portability for various architectures.
    * Internationalization. This includes support for non-ASCII character code, message catalogs like gettext, fonts, graphics console, and so on.
    * Real memory management, to make GNU GRUB more extensible.
    * Modular, hierarchical, object-oriented framework for file systems, files, devices, drives, terminals, commands, partition tables and OS loaders.
    * Cross-platform installation which allows for installing GRUB from a different architecture.
    * Rescue mode saves unbootable cases. Stage 1.5 was eliminated.
    * Fix design mistakes in GRUB Legacy, which could not be solved for backward-compatibility, such as the way of numbering partitions. 

[http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)


> grub2 is critical, because its finally multi-platform, supports scripting (so we could even make it auto-configure itself), and it fixes serious design issues in Grub1 which cause errors (many of which Microsofts boot loader suffers from too).

Grub2 I believe is good enough to encourage motherboard manufacturers to build in a 256mb flash memory module into their motherboards to store Grub2 it on safely so it doesn't conflict with anything). If they did that, we wouldn't have to worry about overwriting other operating systems MBR's all the time, and we would have something as reliable as the EFI bootloader.

I don't think many people realise exactly how much safer Grub2 would make booting linux, whilst also improving reliability. Since its cross platform too and designed to be more extendible, it means we won't need to have programmers maintaining a different bootloader for each architecture, instead allowing them all to focus on just grub2.

[http://brainstorm.ubuntu.com/idea/10842/](http://brainstorm.ubuntu.com/idea/10842/)




---

