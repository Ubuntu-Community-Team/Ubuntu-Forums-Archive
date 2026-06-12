---
title: "How do I see files created in Ubuntu 10.4 when I boot Windows XP"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by technmom on 2010-06-14
I installed 10.4 dual boot with Win XP two weeks ago and am enjoying it, but still need to go to Windows. Can I see the files I created under Ubuntu when I boot up in Windows?

---

### Post by Chesamo on 2010-06-14
That depends if Ubuntu is installed onto an extX file system or not. Ubuntu natively uses the ext4 file system, which can't be read by Windows. If you transfer those files into a Flash drive, or onto your Windows partition, then Windows will be able to read them, yes.

---

### Post by 67GTA on 2010-06-14
Short answer is no. Windows doesn't natively read filesystems other than it's own. There are kernel drivers that will let you do this with ext3, but they haven't been updated for ext4 yet. Some are read only, others are read and write capable. If it is very important, reinstall use ext3. Just google "read write linux from windows". Here a couple of examples. 

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by NCLI on 2010-06-14
[It is possible]("http://www.linuxjournal.com/article/9449"), but a little bothersome.

---

### Post by kgr132 on 2010-06-14
Ext2read 2.2 released. Now with LVM2 and EXT4 support
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)
It's read only support, but you can access the files on your ext2/3/4 partitions.


For just ext2/3 access, this works quite well and supports read/write. Also supports the larger iNode setting used for ext3 by recent ubuntu versions.
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

Both programs are open source and support WinXP.

---

