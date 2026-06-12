---
title: "reading/writing to a FAT32 hd"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by nosman240 on 2009-01-24
Hey all, I looked through the forums and couldn't find the exact answer to my question:

I have WinXP currently installed on my hd in an NTFS partition. i also have an external hd that contains things like schoolwork, music, movies, etc. but it has a FAT32 partition. I'm planning a dual boot of XP/Ubuntu so would i be able to access the files on my FAT32 external as well as save files, copy, paste, etc. on Ubuntu like i would in XP? I was unsure about this because I've read Linux isn't very nice with FAT32 and i'd like to avoid formatting my external if possible

---

### Post by SunnyRabbiera on 2009-01-24
No it should work fine, as long as the drive is plugged in and the os sees it the drive should work.
I think anything you might have read might relate to people installing linux as a fat system...
Really linux can use any FS as long as its in the kernel, this includes NTFS but as an installed system its best to use the default system:
ext3

---

### Post by binbash on 2009-01-24
you can write and read, it should work fine

---

### Post by nosman240 on 2009-01-25
Thanks, i appreciate the input. so though ext3 is the preferred file system of ubuntu, what file system should i use when i install it on my internal HD partition? i'd like to be able to access stuff on the windows partition as well as my external, so would making it a NTFS partition be fine still? or should i make the ubuntu partition ext3?

---

### Post by drs305 on 2009-01-25
The ubuntu system will be installed as ext3. That would include the / (root) and /home partitions (if installed on a separate partition). The swap partition will be formatted as "swap" or "linux-swap" automatically by the system during install. Your non-system data partitions can be other file systems as you have previously discussed.

---

