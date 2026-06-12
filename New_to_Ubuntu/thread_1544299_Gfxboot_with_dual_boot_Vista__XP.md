---
title: "Gfxboot with dual boot Vista / XP"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Azureum on 2010-08-02
Hello!

As this is my first post I'd like to say hi!

I am wishing to set up a dual boot configuration with Windows Vista (highly tweaked) and Windows XP (stripped and highly tweaked). I have been looking around and I am getting more confused the more I look.

I would like to use gfxboot version of GRUB to load XP & Vista.

If someone could provide me with a step by step of the Linux side (commands, and partitioning, order of install etc) then I can manage the Windows side myself.

My original thought was that I'd have to run a live cd of a linux distro with gfxboot on it, install it with the commands to the MBR. I also believe there needs to be a small partition for the bootloader files themselves.

Would I arrange 2 x primary partitions & one partition for the grub files? Does that partition need to be of the Ext type?

I found this tutorial dealing with putting grub on the drive:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=gfxboot+vista+xp](http://ubuntuforums.org/showthread.php?t=224351&highlight=gfxboot+vista+xp)

I do not know if this is gfxboot or not ...

I also wish when booting to hide the other operating system so it does not take a drive letter other than C:

I'm just not sure of how to configure my partitions, and the order of install, and the specific commands to install and then configure the bootloader to the hard disk.

I would appreciate any help you can provide, thanks!

---

### Post by SpockVulcan on 2010-08-02
I hope this answers your question.

The easiest way to have a dual boot of Windows and Ubuntu is to Install windows completely (sorry this means backup and format:()then use a live CD and use the installer to resize the two partitions

---

