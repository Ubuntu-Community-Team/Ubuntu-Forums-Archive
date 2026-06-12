---
title: "Missing BootMGR"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Gotaro on 2009-09-14
"Press CTRL+ALT+DELETE to restart"

On one HD, I have a Windows 7 installation.  On the other, I have 3 partitions: Linux, Storage (FAT32), another Windows 7.

When I installed Win7 on the separate HD, it superseded GRUB (of course), so I ran GParted live and got things working again by repairing/reinstalling GRUB (I think).  But now I've installed Fedora 11 over Ubuntu and had a funky time getting the partition right (there were options I didn't really understand, and I wound up having to let it do its thing and just choose "Overwrite existing Linux partition."

I thought maybe I just had the wrong partition selected for the Win7 entry (currently set at hd1,0), but there appears to be only one partition on the entire drive (looking through GParted).
```

title Windows 7
	rootnoverify (hd1,0)
	chainloader +1
```

What should I do?

Thanks :)

Edit: Actually, there are not 3 partitions, but 6 (including a boot partition and two "unallocated" ones).

Edit: I've tried booting from the Win7 DVD and repairing, which tells me I have no OSes installed...

Edit: Solved.  The "bootmgr" file was located on the other Win7 partition.  I changed (hd1,0) to (hd0,2).

---

