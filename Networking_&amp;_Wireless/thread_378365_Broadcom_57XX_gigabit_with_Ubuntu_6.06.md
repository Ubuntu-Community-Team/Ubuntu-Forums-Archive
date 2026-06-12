---
title: "Broadcom 57XX gigabit with Ubuntu 6.06"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by tullio.barbieri on 2007-03-07
I'd installed Ubuntu 6.06 on Dell SC440 server and no Ethernet adapter has been recognised.
The NIC present on the main board of the server is NetExtreme Broadcom 57xx Gigabit.

I need help to find drivers for UBuntu and fro installing them without re-compiling the kernel (if possible).
Thanks

Tullio

---

### Post by chili555 on 2007-03-07
It seems there are two modules present now that are supposed to work with this adapter. To find out which one, if any, is loaded, open a terminal and do: lsmod | grep tg3 and then do: lsmod | grep bnx2.

I understand that bnx2 is to be preferred. I understand it was to be included in 6.06, so first, lets' see if you have it. After doing sudo updatedb (this will take a few moments), do locate bnx2.

Let us know and we'll go from there.

> without re-compiling the kernelGosh, that would be fun, but there are better ways.

---

### Post by TeamMoto7543 on 2007-03-16
Try looking at:
http://ubuntuforums.org/showthread.php?t=323667&highlight=sc440

---

