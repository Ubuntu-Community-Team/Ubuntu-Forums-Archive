---
title: "Thumb Drive Mounting Error"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Koobelakahn on 2010-02-18
Hello all.
Im getting an error message, and google isnt yeilding results. I also used the thead search tool, to no avail.
Im currently running 9.10 Ubuntu Netbook Remix. The other day, i decided that i wanted to make a Ubuntu Startup disk. So I reformatted a 2gb thumb drive, and attempted to make a startup disk using an Ubuntu Live! CD. Unfortunately, I kinda messed it up when i messed with the partitions. So after making a few partitions in some obscure file formats, i now cannot mount the thumbdrive on any computer. I also tried it on Windows xp, and windows 7. Windows XP doesnt even try to validate its existance. Windows 7 says "This disk needs to be formatted" but when i try to format it, it does no such thing. Here is the error message I'm getting:

```
Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error in some cases useful info is found in syslog - try dmesg | tail  or so 
```

Can I repair my thumbdrive? Or should i abandon hope?

---

### Post by Koobelakahn on 2010-02-18
So, i ran
steven@steven-laptop:~$ sudo dd if=/dev/zero of=/dev/sdb

This is the resulting code
dd: writing to `/dev/sdb': No space left on device
4013961+0 records in
4013960+0 records out
2055147520 bytes (2.1 GB) copied, 753.93 s, 2.7 MB/s

And now the thumbdrive isnt being registered by Ubuntu at all.

---

### Post by Koobelakahn on 2010-02-19
After i ran the previous command, I put the thumbdrive into my Windows machine, and it asked me to Format it. I did, and now im currently using it as an Ubuntu Live USB.

---

