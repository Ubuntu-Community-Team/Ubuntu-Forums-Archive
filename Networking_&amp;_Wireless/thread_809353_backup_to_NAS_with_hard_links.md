---
title: "backup to NAS with hard links?"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Marco_Polo on 2008-05-27
I'm attempting to backup my laptop with Backuppc ([http://backuppc.sourceforge.net/faq/BackupPC.html](http://backuppc.sourceforge.net/faq/BackupPC.html)).  I'd like to store the data on a Lacie Mini ([http://www.lacie.com/products/product.htm?pid=10843](http://www.lacie.com/products/product.htm?pid=10843)).  The drive supports FTP and SMB and can be formatted as either FAT32 or ext3.  I've currently got it formatted to ext3.

I've followed a guide to mount the drive as a samba share and now I've got this in my fstab:
//EDmini.local/ED_mini /media/EDmini cifs username=backuppc,password=backuppc,rw,noexec  0 0

The backup server runs as user backuppc and the data is going to '/var/lib/backuppc'.

Now when I take the step of mounting my NAS at that location, the backup server fails to connect.  I've learned that backuppc, like Time Machine and rsnapshot, uses hard links and that this is not supported by CIFS.

I've read that NFS does support them.  So, is it possible to mount the drive's filesystem as NFS?  Do I need to get a different drive?  Lastly - how do most Ubuntu user backup to an external drive?  I've seen people using rsync, but I believe that requires ssh support - do other NAS drives support ssh?

Any help would be much appreciated.

---

