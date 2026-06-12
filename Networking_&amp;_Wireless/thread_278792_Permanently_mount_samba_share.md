---
title: "Permanently mount samba share"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by Eladon on 2006-10-16
I would like to permanently mount a samba share on my file system.  I found some instructions here:

[http://ubuntuguide.org/wiki/Dapper#How_to_permanently_mount_a_samba_share](http://ubuntuguide.org/wiki/Dapper#How_to_permanently_mount_a_samba_share)

But when I try to do the mount I get this message: 

cli_negprot: SMB signing is mandatory and we have disabled it.
13534: protocol negotiation failed
SMB connection failed

So I try the manual mount of the fashion: 

```
mount -t smbfs -o username=myusername,password=mypassword //serverip/share /media/share
```

...same error message...

After 2 hours googling and searching Ubuntu's website, I'm thinking to myself, geez, this CAN'T be this difficult.

Please help!

---

### Post by Eladon on 2006-10-16
Found the solution.  Apparently this is a problem when trying to access a Windows 2003 share (may also be related to Active Directory).

I found the answer here:
[http://www.techiesabode.com/forum/posts_w.php?forum_id=1](http://www.techiesabode.com/forum/posts_w.php?forum_id=1)

The solution is to use the CIFS file system:

mount -t cifs -o user=yourusername //server/share /mountpoint

(basically, change smbfs to cifs)

More info on the CIFS mount options are here:
[http://www.kernel.org/git/gitweb.cgi?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;h=7b4ac096cd114d34e623bafaed91b85ba4a95e62](http://www.kernel.org/git/gitweb.cgi?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;h=7b4ac096cd114d34e623bafaed91b85ba4a95e62)

---

### Post by Eladon on 2006-10-18
Oh, also keep in mind, you will have to install samba and smbfs for this to work:
```
sudo apt-get install samba smbfs
```

---

