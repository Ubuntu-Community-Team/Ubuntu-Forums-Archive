---
title: "Changing drive format?"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-07-29
I tried using Vobcopy and aparently my drive is formatted as FAT32 and it needs to be NTFS.  Is there anyway of changing this without having to reinstall Ubuntu or anything?

---

### Post by S.R on 2010-07-29
If you still have windows installed you can use the convert command.

```
C:\> CONVERT  C:  /fs:ntfs

```

---

### Post by 3rdalbum on 2010-07-30
Your Ubuntu drive is formatted as Extended (ext3 or ext4), not as fat32 or NTFS. Extended can handle big files.

---

### Post by TriBlox6432 on 2010-07-30
But I get an error message when trying to use vobcopy...


michael@mCarey-Laptop:~$ vobcopy -l
Vobcopy 1.1.0 - GPL Copyright (c) 2001 - 2007 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

[Info] Path to dvd: /dev/sr0
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
[Info] Name of the dvd: JUNO
[Info] There are 32 titles on this DVD.
[Info] There are 104 chapters on the dvd.
[Info] Most chapters has title 1 with 29 chapters.

[Info] There are 32 angles on this dvd.
[Info] Using Title: 1
[Info] Title has 29 chapters and 1 angles
[Info] Using Chapter: 1
[Info] Using Angle: 1

[Info] DVD-name: JUNO

[Info] Outputting to /home/michael/JUNO1.vob
[Error] File '/home/michael/JUNO1.vob.partial' already exists, [o]verwrite, [a]ppend, [q]uit? 
o


[Error] Write() error
[Error] It's possible that you try to write files
[Error] greater than 2GB to filesystem which
[Error] doesn't support it? (try without -l)
[Error] Error: Bad file descriptor
michael@mCarey-Laptop:~$

---

### Post by oldos2er on 2010-07-30
Can you please post the output of **df -T** run in a terminal?

---

### Post by TriBlox6432 on 2010-07-30
michael@mCarey-Laptop:~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext4   234623848   3662908 219042708   2% /
none      devtmpfs      991400       284    991116   1% /dev
none         tmpfs      995620       208    995412   1% /dev/shm
none         tmpfs      995620       100    995520   1% /var/run
none         tmpfs      995620         0    995620   0% /var/lock
none         tmpfs      995620         0    995620   0% /lib/init/rw
michael@mCarey-Laptop:~$

---

### Post by TriBlox6432 on 2010-07-31
Bump

---

### Post by TriBlox6432 on 2010-08-01
Bump.

---

