---
title: "How to make ubuntu's menu.lst the default?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by suitedaces on 2009-10-11
Hi, apologies for what is probably a duplicate thread, but i can't find the correct search terms.

I recently installed crunchbang in a third partition of my os, and all's going well, except that the /boot/grub/menu.lst in my crunchbang is now the default one.

How can I either A) make sure upgraded kernels for ubuntu appear in my new grub menu as they did in my old one, or B) restore my ubuntu menu.lst as the "dominant" one, and add crunchbang to it?

---

### Post by oldfred on 2009-10-11
Which ever Grub is in the MBR will be the one in control. When you installed Crunchbag did it offer an advance setting for installing Grub like Ubuntu does?

You can reinstall Grub choosing the Ubuntu partition's stage1, You should get multiple stage1:

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)

When I have multiple OS I like to chainboot which requires the grub to be installed to the partition setup(hdx,y) and then use a chainboot entry in the first menu.lst that comes up. That way every update to the kernel is still updating its menu.lst and you do not have to edit a menu.lst. The only disadvantage is layered menus.
boot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
You can even go one more level and just have a partition for Grub and a menu.lst that is chainboot entries:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by suitedaces on 2009-10-11
Thanks, I get as far as
```
grub> find /boot/grub/stage1
 (hd0,4)
 (hd0,6)

```

All i know is ubuntu is on dev/sda5 and crunchbang is dev/sda7

---

### Post by lidex on 2009-10-11
suitedaces:
Find instructions here
[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub")
hd0,4 would be your ubuntu install

---

### Post by suitedaces on 2009-10-12
Thanks, not sure why I didn't come across that in my searches. In uni at the minute, but will use that tonight.

---

### Post by mikechant on 2009-10-12
Just to simplify things a bit (as the referenced post is quite extensive)

sda5=(hd0,4)
sda7=(hd0,6)

so to switch back to the Ubuntu grub setup you just need
```
root (hd0,4)
setup (hd0)
```
at the grub prompt

---

