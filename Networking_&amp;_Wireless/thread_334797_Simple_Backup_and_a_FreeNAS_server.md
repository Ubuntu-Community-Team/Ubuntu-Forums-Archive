---
title: "Simple Backup and a FreeNAS server"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by bobbob1016 on 2007-01-09
I have a FreeNAS server setup, which has been working flawlessly for storing files and things, but I have an issue getting Simple Backup to backup to it.  I have a drive mounted through SMB, but it is a drive on my desktop, and I can't backup to it.  Whenever I do backup to it, the backup goes to /var/backup/ not the network drive.  Someone suggested that it was a permissions issue, but I don't know how to mount it as root.  I am able to make a folder on the drive if I am root (I have the root-nautilus-here script installed).

To mount the drive, I use this command:
sudo mount //192.168.0.250/160gig /media/Backup/ -o username=**********,password=**********,dmask=777,fmask=777

---

### Post by Iowan on 2007-01-10
[http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html]("http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")
Any help here?

---

### Post by bobbob1016 on 2007-01-11
Sorry I didn't respond sooner, I just started classes this week.

I mount the SMB shares with commands similar to the ones from that guide.  I mount the drives as root, and make them R/W to every user.  I run Simple Backup as root as well, and I tell it to backup to the mounted SMB drive, but no luck.

The command I type to mount is:
sudo mount //192.168.0.1/linux /media/sharename/ -o username=myusername,password=mypassword,dmask=777,fmask=777

I'd prefer not to mount them on boot, since I don't use them as much, and I want the simple backup to backup when I tell it to, so I would mount the drive when I want a backup.

---

