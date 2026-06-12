---
title: "Partitioning for a XP dual boot."
date: 2009-01-17
forum: New to Ubuntu
---

### Post by leonhart83 on 2009-01-17
Hey guys,

I have only ubuntu installed on my laptop and my gf hates it. I have a license of xp to use, but I don't want to reformat the ubuntu install. Is there a command I can run to create a partition so that when I run the setup it will be visable to xp and I can dual boot.

Hopefully that isn't too confusing.

---

### Post by cdtech on 2009-01-17
You can use the Live CD and open the program "gparted". Set up a partition and format it to fat so Windows will recognize it.

---

### Post by ajmorris on 2009-01-17
hi there,
formatting as fat (as cdtech suggested) is a very good way of sharing between windows and ubuntu, however fat can be annoying at times, mainly because of it's limitations, such as being unable to create a file larger than (2^32)-1 bytes (approximately one byte less than 4 GB), you can alternatively leave your ubuntu partition as the default ext3, and download tools for windows xp, to allow xp to read and write to the partition.

[Ext2IFS]("http://www.fs-driver.org/") has had the most success stories

both methods are good either way, it is just up to your preference :)


AJ

---

### Post by muteXe on 2009-01-17
He;ll have to reconfigure his grub won't he?

---

### Post by theozzlives on 2009-01-17
If XP is put on AFTER Ubuntu the GRUB will need to be reinstalled.

---

### Post by muteXe on 2009-01-17
going on the first post it sounds like that might be the case.

---

### Post by minsf on 2009-01-17
yes i think he'll have to reconfigure his grub
you may be interested in this: 
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

one more thing: the mentioned gparted program is under System>Administration (when running a live cd) and appears as "Partition Editor".

---

