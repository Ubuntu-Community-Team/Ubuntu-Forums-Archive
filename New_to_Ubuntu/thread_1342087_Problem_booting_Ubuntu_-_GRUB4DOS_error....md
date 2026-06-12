---
title: "Problem booting Ubuntu - GRUB4DOS error...?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by lotuscarsltd52 on 2009-11-30
I am a new user of Ubuntu (about 3-4 months) and I am unfortunately not a computer person, but I nonetheless downloaded Wubi and installed Ubuntu as an alternative to Windows.

Occasionally Ubuntu freezes upon booting and I am forced to do the old "hold the power button until the computer shuts off" routine, which has worked for Ubuntu every time until now. Ubuntu now refuses to boot which is a problem since I need to access my files for class.

I get the following message when I load Ubuntu:

"GRUB4DOS 0.4.4 2009-04-21, Memory: 639 K/1012 M, MenuEnd: 0x43516 [Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits. ]

grub>"

I don't know enough about code to actually go into the command lines and do something, and I don't know what to do to fix this problem.

In case it helps I am using an Acer Aspire One AOD-250 netbook with 1 GB RAM and a 1.6 GHz Intel Atom processor. I also recently upgraded to Ubuntu 9.10. Since my computer is a netbook there is no CD drive, so I can't use an install CD unless I borrow an external drive. Plus wouldn't this erase all the stuff on my hard drive?

I hope someone can help!

[EDIT] When I type "reboot" the computer does so without a problem, but when I type "boot" it says "Kernel must be loaded before booting".

---

### Post by stoogiebuncho on 2009-12-05
Wubi installs are installed on a NTFS filesystem (since they are installed within Windows), which doesn't handle improper shutdowns as well as EXT filesystems do.  It's one of the disadvantages of a Wubi install.  

I don't know what the chances are of getting your Ubuntu boot-able again - perhaps someone here knows more than I do.  

I know this doesn't help much.  One of the reasons I'm replying is simply to bump this back to the front page where maybe someone more knowledgeable will see it.

---

