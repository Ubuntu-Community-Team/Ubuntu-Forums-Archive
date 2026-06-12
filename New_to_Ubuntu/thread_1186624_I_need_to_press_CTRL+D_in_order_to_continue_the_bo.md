---
title: "I need to press CTRL+D in order to continue the boot process, I have the log file..."
date: 2009-06-13
forum: New to Ubuntu
---

### Post by legolas_w on 2009-06-13
Hi
Thank you for reading my post
During the boot process, I receive a message about a log file located in /var/log/fsck/check and the boot process stops until I press the ctrl+d keys.
here is the content of the log file, can you please let me know what should I do?
I should include that I removed a hard disk and changed the partitioning of the remaining disk.

```

Log of fsck -C3 -R -A -a 
Sun Jun 14 00:07:27 2009

fsck 1.41.4 (27-Jan-2009)
fsck.ext3: No such file or directory while trying to open /dev/sdb1

/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

home: clean, 187314/3203072 files, 5561489/12799788 blocks
OPT: clean, 324649/4481024 files, 5653489/17918491 blocks
Torrent: clean, 7191/3203072 files, 6005016/12799780 blocks
Misc: clean, 2688/5130000 files, 5007543/20480000 blocks
fsck died with exit status 8

Sun Jun 14 00:07:29 2009
----------------

```

Thanks.

---

### Post by halitech on 2009-06-13
can you post the output of
```
cat /etc/fstab
```

I had the same message when I removed a drive and you just need to alter the fstab file

---

