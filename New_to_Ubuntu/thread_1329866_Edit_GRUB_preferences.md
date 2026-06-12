---
title: "Edit GRUB preferences"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by FelixS on 2009-11-17
I have installed Ubuntu 9.10 64 bit and Windows XP Home in the same hard drive. When I turn on the computer the GRUB have selected the Ubuntu 9.10 as default and starts it after a few seconds, but I want to set it to Windows XP as default. Is this possible?

PS: I'm doing this because I installed Ubuntu as a test, but now I use Windows because I used to use this. Thanks.

---

### Post by laffinet on 2009-11-17
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

You need to edit this file: /etc/default/grub 

Look for GRUB_DEFAULT=0

> GRUB_DEFAULT=0 Sets the default menu entry by menu position. As in GRUB, the first "menuentry" in grub.cfg is 0, the second is 1, etc. 

Change this to whatever the entry for windows is and you should be fine.

---

### Post by FelixS on 2009-11-18
> **laffinet said:**
> [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You need to edit this file: /etc/default/grub 

Look for GRUB_DEFAULT=0

 

Change this to whatever the entry for windows is and you should be fine.

Thank you very much. =D>

---

### Post by Cheesemill on 2009-11-18
Or you could install Startup Manager from the Software Centre and use that if you want point and click.

---

