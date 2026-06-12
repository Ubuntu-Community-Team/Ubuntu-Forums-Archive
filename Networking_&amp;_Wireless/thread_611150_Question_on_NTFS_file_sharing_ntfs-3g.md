---
title: "Question on NTFS file sharing ntfs-3g"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by Matchless on 2007-11-12
Hi,
    I need some clarity on the following issue:
With the NTFS-3g driver the files in the NTFS partition on a dual boot PC can be safely read and written to from Ubuntu. The NTFS partition is thus mounted in Ubuntu and can be used as if it is part of the Ubuntu file system.
Files on an NTFS partition on a remote Windows PC can be mounted  on the Ubuntu PC.
Question Can these files be read and written to safely if on a NTFS partition?
              Can NTFS-3g be used to mount such remote files?
I found al ot on mounting a Windows share, but no-one really spelling this out. If it was unsafe to write to a NTFS file on a dual boot PC then it should also be unsafe to write to the same file on a remote Windows PC?? Maybe I have missed the boat somewhere.
Thanks

---

### Post by kidders on 2007-11-14
Hi there,

Just like Ext or FAT ones, NTFS drivers are for interpreting the raw data stored on a device. Although it *can* be done (eg using ATA over Ethernet), it is not common practice to share files by exposing raw filesystem data over a network. Conventional sharing protocols (eg AFP, Windows filesharing, NFS) all have their own filesystem models, so the way shared files are stored server-side is always irrelevant. Basically, sharing files that happen to be stored on a ReiserFS filesystem differently than files stored on an NTFS filesystem would be silly.

> **Matchless said:**
> If it was unsafe to write to a NTFS file on a dual boot PC then it should also be unsafe to write to the same file on a remote Windows PC?That's not true ... Naturally, a Windows PC's NTFS drivers didn't have to be reverse-engineered, so they work perfectly. Network *clients* don't even need to know what NTFS is. As long as the client PC can understand the file sharing protocol the Windows PC is using, it can safely access the shared files.

Consider FTP, for example. Windows PC users regularly make use of FTP to access things stored on remote servers, despite the fact that Microsoft operating systems are completely incompatible with the filesystems used to store the data shared by most FTP servers. The Windows file sharing protocol works the same way ... it's little more than glorified FTP.

I hope that helps.

---

### Post by Matchless on 2007-11-15
Thanks,
          Although a lot of what you state is way above my head but I think I understand that what you are saying is that the usual file sharing protocols makes sharing between different machines running different OS's transparent. Obviously then this is not the same for a shared partition on the same PC as only in such cases should these special drives used for NTFS and EXT3 access from linux and Windows.
Thanks again

---

