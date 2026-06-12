---
title: "How do I get rId of that B&amp;W OS selection screen thing?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Shake 'n' Bake on 2009-12-27
I installed Ubuntu NBR on an SD card and got some updates a bit later.  Ever since then, on boot (after the "GRUB Loading" message) I've been presented with a few OS choices.  There's a few Ubuntu choices, some testing stuff, and both Windows Vista and 7.

Can I get rid of this or is it normal?  Thanks for the help.

---

### Post by drs305 on 2009-12-27
That is GRUB (Grand Unified BootLoader) and it's normal. It is either Grub (legacy) or Grub 2 - you can probably see the version at the top of the menu.

This menu allows you to set the default OS you want to boot. Normal options on a dual boot system include:

Linux/Ubuntu kernels will boot to Ubuntu. As newer kernels are introduced, the list will grow. (Think of them as updates to the main operating system). The latest/newest one is usually at the top of the menu.

Recovery mode: You will probably see some listed as "Recovery". These load the kernels without some of the things that can cause problems if they are loaded. You would use the "Recovery" mode if you tried booting into Ubuntu and had problems, such as with video drivers, etc.

Memtest86+ - These are menu items that run tests on your installed memory, looking for faults.

Windows

Windows Recovery - The recovery partition to help reinstall Windows if it becomes corrupted.

You can set which one of these options will boot at startup, and how long you will see the menu (even IF you want to see the menu options).

How you set them up depends on which version of Grub you have. For Grub 2, take a look at the 'G2-Basics' or "GRUB2" in my signature line for information including how to set it up.

If you are using Grub legacy, there is a great GUI app that can help you configure the settings. Refer to the "SUM" link.

---

### Post by Shake 'n' Bake on 2009-12-27
Thanks.  It's a bit annoying, is all.

---

### Post by drs305 on 2009-12-27
> **Shake 'n' Bake said:**
> Thanks.  It's a bit annoying, is all.

You can hide it and let the system boot automatically to one of the choices. If you do that you can display the menu by holding down the SHIFT key during boot if you want to make a different selection.

You can also shorten the time it's displayed before it boots the default selection.

And you can also make the GRUB2 menu very pretty with some eye candy by placing an image in the background. 

All of these are explained in the GRUB2 doc, linked below.

---

### Post by Shake 'n' Bake on 2009-12-27
Thanks.  I took a look and I'm a) too impatient to wait for the download and b) not skilled enough to do this.

This is only my third or fourth dabble with any form of Linux.  I'm an avid Mac user, but have no knowledge of the command line.

---

