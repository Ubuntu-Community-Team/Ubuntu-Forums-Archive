---
title: "GRUB fix"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by lengo on 2009-10-23
I dual boot XP and Ubuntu. Or at least I used to... I was trying to resize partitions with GParted (sound familiar yet... ?) and inadvertently deleted the Ubuntu partition. On boot I got Error 22. After searching I found that it might be possible to do 'fixmbr' from an XP install disk recovery console. XP recovery console reported that "Setup did not find any hard disk drives installed in your computer". Sigh... My next approach was to try to repair GRUB from a LiveCD. sudo grub, find /boot/grub/stage1 returned Error 15: File not found. I found some instructions [_here_]("http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-22-deleted-partition-377590/page2.html") that suggest to do: sudo lilo -M  /dev/sda mbr. Another suggestion was to reinstall Ubuntu and create a new GRUB. Any advice would be much appreciated (obviously).

---

### Post by Dark_Stang on 2009-10-24
You're getting that error because grub is looking for the menu.lst file, which was stored on your Ubuntu partition. So you have two choices...

1. Reinstall Ubuntu or...
2. Forget Ubuntu and just go with Windows. You may need to load in some sata drivers to get the Windows XP disc to recognize your hard drive before you run fixmbr.

---

### Post by Elfy on 2009-10-24
duplicate here [http://ubuntuforums.org/showthread.php?t=1299480](http://ubuntuforums.org/showthread.php?t=1299480)

---

