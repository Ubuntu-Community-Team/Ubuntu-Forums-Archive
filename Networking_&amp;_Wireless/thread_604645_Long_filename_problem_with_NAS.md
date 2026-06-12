---
title: "Long filename problem with NAS"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by Thies on 2007-11-06
Hey!

I installed a NAS (LaCie Big Disk) in our network to store there files to me shared. Some of these files have very long file-names (with spaces, special characters, umlauts etc). The synchronisation is going quite OK, but files with long file names (I couldn't yet figure out the amount of chars that still copy fine) do get messed up and are saved with a something like ": x .." ending. Neither from Ubuntu nor from Windows (XP) can these files be assessed or deleted (error message is that the file does not exist).

The NAS uses XFS as file system, which should allow file names up to 255 Byte. I have no clue what this means in characters.

Maybe the problem is in my mounting of the NAS. I mount the NAS in "/etc/fstab" as follows:
```
//192.168.0.20/share  /media/NAS/share  smbfs  uid=thies,gid=thies,username=thies,credentials=/home/thies/.smbcredentials,dmask=0777,fmask=0777,iocharset=utf8,codepage=unicode,unicode 0  0
```

I hope that someone might have a clue? Also if all the mount options are needed ...

Many thanks and Happy Ubuntuing!
/Thies

---

### Post by Lambert on 2007-11-06
I'm not 100% sure so I'll give you an area to look into and a bump for your thread.

Shouldn't the file system listed in  fstab be xfs and not smbfs?

---

