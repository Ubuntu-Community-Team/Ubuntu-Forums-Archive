---
title: "SMB sharing entire drive/partition?"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by taseedorf on 2008-08-22
Is it possible to share an entire drive?  I have a USB external HD and would like to share the entire drive, since it has all video on it.  However, the sharing tab in the right click menu only allows to share folders.  Can I edit the shares in smb.conf to share an entire drive?  Also, are there any security risks in doing this?  
Thanks in advance

---

### Post by bab1 on 2008-08-22
Yes you can share the entire HD.  You need to:[LIST]
[*]Partition the HD (one partition is fine)
[*]Format the partition (use the ext3 FS)
[*]Create a mountpoint (I would use /<something_descriptive> ) 
[*]Mount the partition (using /etc/fstab)
[*]Create a folder (this will be the starting point of this share)
[/LIST]

Note: You can make multiple shares on this HD.

Then, as you say, edit the smb.conf file

There are only the normal Samba security risks. Nothing special.

---

### Post by taseedorf on 2008-11-28
ha found out I was being an idiot..trying to share the drive instead of the mount point.

---

