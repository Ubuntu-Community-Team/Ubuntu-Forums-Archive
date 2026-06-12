---
title: "Sidewinder X6 doesn't work in GNU GRUB.."
date: 2010-09-25
forum: New to Ubuntu
---

### Post by mfenix130 on 2010-09-25
Hi i just purchased the sidewinder x6 keyboard ,but the problem is it _does not work in GNU GRUB (version 1.98.1ubuntu6)_.i am dual booting ubuntu (10.04) and windows 7.i cant select the windows 7 loader option because the down arrow key does not work.so it automatically boots into ubuntu (first choice) after 10 seconds.

Details=
_When i start my pc,initially the keyboard works (i can see the backlighting),then when it reaches GNU GRUB loader it stops working._
i see 7 options in it which are:
Ubuntu with linux,2.6.32-22-generic
Ubuntu with linux,2.6.32-22-generic(recovery mode)
Ubuntu with linux,2.6.32-21-generic
Ubuntu with linux,2.6.32-21-generic(recovery mode)
Memory Test (memtest 86+)
Memory Test (memtest 86+,serial console 115200)
Windows 7(Loader (on/dev/sda1) 

but since the keyboard doesnt work it boots into ubuntu by itself.
I have to use an old PS/2 keyboard to select and choose the windows 7 options..

Oh and_ the sidewinder doesn't even work in the windows boot loader_ (i have two windows 7 installed on two separate hdds),so again i have to use the old PS/2 keyboard here..
After windows starts booting,then then keyboard works.And it works fine in Ubuntu as well.

**How to make it work in boot managers ??**

---

### Post by mfenix130 on 2010-09-29
> **mfenix130 said:**
> Hi i just purchased the sidewinder x6 keyboard ,but the problem is it _does not work in GNU GRUB (version 1.98.1ubuntu6)_.i am dual booting ubuntu (10.04) and windows 7.i cant select the windows 7 loader option because the down arrow key does not work.so it automatically boots into ubuntu (first choice) after 10 seconds.

Details=
_When i start my pc,initially the keyboard works (i can see the backlighting),then when it reaches GNU GRUB loader it stops working._
i see 7 options in it which are:
Ubuntu with linux,2.6.32-22-generic
Ubuntu with linux,2.6.32-22-generic(recovery mode)
Ubuntu with linux,2.6.32-21-generic
Ubuntu with linux,2.6.32-21-generic(recovery mode)
Memory Test (memtest 86+)
Memory Test (memtest 86+,serial console 115200)
Windows 7(Loader (on/dev/sda1) 

but since the keyboard doesnt work it boots into ubuntu by itself.
I have to use an old PS/2 keyboard to select and choose the windows 7 options..

Oh and_ the sidewinder doesn't even work in the windows boot loader_ (i have two windows 7 installed on two separate hdds),so again i have to use the old PS/2 keyboard here..
After windows starts booting,then then keyboard works.And it works fine in Ubuntu as well.

**How to make it work in boot managers ??**

Anyways Got it to work by enabling USB keyboard support in BIOS..:)

---

