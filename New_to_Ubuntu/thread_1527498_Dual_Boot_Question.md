---
title: "Dual Boot Question"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Automag05 on 2010-07-09
Hi guys,
I am very new to Linux, running Ubuntu version 10.04, and have Grub2.
What I am wanting to do is install Fedora 13 (or another fun version of Linux, I am up for suggestions) on my Grub2 that is currently partitioning WinXP and my Ubuntu, does Grub2 support that? And if it does, how may I go about installing it? I downloaded the Fedora.iso, but I do not know how to boot from CD with Grub2, I'm too familiar with Windows.

Thanks!
Auto

---

### Post by Paqman on 2010-07-09
> **Automag05 said:**
> Hi guys,
does Grub2 support that?


Sure, but what Fedora will do is reinstall the bootloader when you install it anyway.

> And if it does, how may I go about installing it?

Just boot up into the Fedora disk and start the installation, same as Ubuntu

> 
I downloaded the Fedora.iso, but I do not know how to boot from CD with Grub2, I'm too familiar with Windows.


You need to set your BIOS to boot from CD, same as you did when you installed Ubuntu.

---

### Post by Automag05 on 2010-07-09
Maybe I am doing something wrong then, I do have my BIOS set up to boot from disk first, yet it is ignored. So there is nothing in Grub2 that can keep my disk from running?

---

### Post by Paqman on 2010-07-10
> **Automag05 said:**
> Maybe I am doing something wrong then, I do have my BIOS set up to boot from disk first, yet it is ignored. So there is nothing in Grub2 that can keep my disk from running?

No. As long as you BIOS says to boot from CD before hard drive, it should boot. Check the CD on another computer.

---

