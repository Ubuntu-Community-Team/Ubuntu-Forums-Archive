---
title: "I have 2 Windows Xp and one ubuntu?!"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by retskrad on 2008-12-29
when i start the computer, I see:

> Windows XP
Windows XP
Ubuntu

How can I remove on XP?

Offtopic:
Also, one other question. it looks like my internet is disconnecting eveytime I'm loggin into ubuntu 8.10. Maybe it works with ubuntu 8.04? 
I duscissed it here [http://ubuntuforums.org/showthread.php?t=1020106](http://ubuntuforums.org/showthread.php?t=1020106)

---

### Post by Michael.Godawski on 2008-12-29
hi, 

perhaps there are two different windows entries in the grub menu.lst ?
I guess you mean the two windows entries which are in the grub...
Please post the output of:
```

cat /boot/grub/menu.lst
```

---

### Post by sdowney717 on 2008-12-29
edit out the entry for the XP you never want to boot from menu.lst

type in 
gksudo gedit /boot/grub/menu.lst

take out the 5 lines associated with the xp boot 

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

will likely be either the root hd0.0 or hd1,0


```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d6269386-1a91-432d-9014-cce8e93eb891 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by handydan918 on 2008-12-29
> **retskrad said:**
> when i start the computer, I see:



How can I remove on XP?

Offtopic:
Also, one other question. it looks like my internet is disconnecting eveytime I'm loggin into ubuntu 8.10. Maybe it works with ubuntu 8.04? 
I duscissed it here [http://ubuntuforums.org/showthread.php?t=1020106](http://ubuntuforums.org/showthread.php?t=1020106)

I would advise caution here. One of those partitions is likely a restore partition, while the other is the actual O/S. Be careful.

---

### Post by retskrad on 2008-12-29
no you don't understand, when you can choose which OS you want to dual boot, it comes 2 windows xp, and below them you can choose to dualboot uubntu

---

