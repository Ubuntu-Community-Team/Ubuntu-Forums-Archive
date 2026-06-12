---
title: "Query regarding 2 memtest entries in boot menu"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Oasis Vali on 2011-05-29
Hi all!!
 
I just dual booted my dell laptop which had windows 7 on it using ubuntu 11.04. As i understand, the grub bootloader is now being used (think version 2) and it lists ubuntu, ubuntu recovery mode, windows 7 at the end and in between it has 2 memory test entries:
 
memtest86+
memtest86+, serial console 115200
 
when i booted into both, they did pretty much the same thing ie checked iff my RAM was functioning properly.
 
So my question is, if they have the same functionality, can i remove one? (and how?) and if they dont, what is the difference?

---

### Post by yetiman64 on 2011-05-29
> **Oasis Vali said:**
> Hi all!!
 
I just dual booted my dell laptop which had windows 7 on it using ubuntu 11.04. As i understand, the grub bootloader is now being used (think version 2) and it lists ubuntu, ubuntu recovery mode, windows 7 at the end and in between it has 2 memory test entries:
 
memtest86+
memtest86+, serial console 115200
 
when i booted into both, they did pretty much the same thing ie checked iff my RAM was functioning properly.
 
So my question is, if they have the same functionality, can i remove one? (and how?) and if they dont, what is the difference?
The serial console entry is used for remote access according to this thread ; [http://ubuntuforums.org/showthread.php?t=1445275](http://ubuntuforums.org/showthread.php?t=1445275).

I am personally unsure how to remove only the serial console though I suspect it may be possible to edit the script /etc/grub.d/20_memtest86+ as root.

If you have already checked the RAM and it is OK you could consider removing both the entries with,

```
sudo chmod -x /etc/grub.d/20_memtest86+
```this removes the executable bit on the script that generates the entries.

To make the changes take, use,
```
sudo update-grub
```To reverse the changes at any time to use memtest run "sudo chmod +x /etc/grub.d/20_memtest86+" and re-run "sudo update-grub" (both without the quotes).

---

### Post by Oasis Vali on 2011-05-29
Thanks a lot yetiman64!! the procedure you described worked!! and thank you again for your prompt reply :)

---

