---
title: "GRUB (legacy) with changing device names"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by edwardLS on 2010-03-03
How do you deal with the GRUB.CONF or GRUB/MENU.LST when each time the system is booted, the Hard drives (/dev/sd[a,b,c] may likely be named differently with respect to the "a", "b", or "c"?

I do not have the opinion of changing the order of connections on the Hot-Swappable devices.  When the removable device(s) are not present the system boots properly from /dev/sda1.  With either of the two, or both, removable devices installed the boot device is no longer identified as /dev/sda; but rather as either /dev/sdb or /dev/sdc.  And the attempt to boot results in a kernel panic and boot failure.

I "believe" the problem is in the 'kernel' line of the grub configuration where "root=/dev/sda1".  However, I do not have a clue how to get around this.  I have tried:
- root=(hd0,0) in the kernel line
- root=UUID={long string of the boot device} in the kernel line

So far, all my attempts have resulted in kernel panics.

Any help, suggestions, pointers, or solutions would be greatly appreciated.

---

### Post by coffeecat on 2010-03-03
> **edwardLS said:**
> root=(hd0,0) in the kernel line

That's where your problem is. It's not the kernel line by the way; it's the line that defines the root partition for grub. Not only do you really need an UUID here, you've got the syntax wrong for a (hdx,y) type line. See below.

The kernel line....

> **edwardLS said:**
> root=UUID={long string of the boot device} in the kernel line

.... is OK - so long as you have the UUID correct.

To give you an idea of the form it all needs to take, here is the first stanza from my Jaunty menu.lst:

```
title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        38f351f2-6ed5-4253-8320-8dcd3fce3ef5
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=38f351f2-6ed5-4253-8320-8dcd3fce3ef5 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet
```In my case, my root is sda6. Were I not using UUIDs, the form of lines 2 and 3 would be:

```
root     (hd0,5)
kernel     /boot/vmlinuz-2.6.28-18-generic root=/dev/sda6 ro quiet splash
```(hdx,y) for the line for grub and /dev/sda6 for the kernel's use, you see. But that's just for interest. You need the UUID in both if you're going to be swapping drives around.

**Edit:** You mention menu.lst, which is the legacy grub configuration file, but your profile says you are running Karmic which comes with grub2. Unless you do an upgrade from Jaunty, that is. The rest of your post certainly looks like you're dealing with legacy grub, but can you confirm this?

---

### Post by edwardLS on 2010-03-04
I should have mentioned that I am dealing with both a "Home" and a "Work" situation.  They are different.  I am addressing the "Work" system which is running Hardy Heron LTS.  My profile indicates my "Home" preferences.  I was using Ubuntu at home long before I convinced my work to give it a try.  

Thanks for you help.  That has cleared up some things for me.

---

### Post by psusi on 2010-03-04
The root= kernel parameter should be the UUID and the installer should have set it up that way for you.  The root (hdx,y) line is telling grub where to find the kernel, and grub only understands (hdx,y).  If you were more specific about the exact errors you get and under what circumstances I could offer more.

---

