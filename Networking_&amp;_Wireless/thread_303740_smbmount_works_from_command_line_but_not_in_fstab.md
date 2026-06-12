---
title: "smbmount works from command line but not in fstab"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by stashj on 2006-11-20
I am having a nightmare trying to figure out why my fstab isn't mounting my samba share properly. If anyone can help I'd be much obliged.
I am using Edgy Server and a samba share on a unix box.

smbmount //192.168.1.41/editest /mnt/editest dmask=777,fmask=777

from the command line works fine and creates the mount, there is no username and password on the share.

//192.168.1.41/editest /mnt/editest dmask=777,fmask=777 0 0

in my fstab results in the mount being unreadable and giving me the following error when i change to the directory and try to ls

ls: .: Input/output error

the same line in my fstab on my edgy desktop box mounts the share fine.

Can anyone help me? I have tried a few commands in the fstab but with the same result, I'm beginning to think it's something that's in the default desktop install that's not in the server but can't figure out why the command line will work and the fstab entry won't

---

### Post by Iowan on 2006-11-20
[http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html]("http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")
I suspect you've already seen this link - but in case you haven't...
[http://www.ubuntuforums.org/showthread.php?t=280473]("http://www.ubuntuforums.org/showthread.php?t=280473")
Here's another one.

---

### Post by stashj on 2006-11-21
Thanks for the reply. I'm afraid I have seen both of those and followed the troubleshooting.
I just can't understand how
mount -t smbfs //192.168.1.41/editest /mnt/editest
will work but putting
//192.168.1.41/editest /mnt/editest smbfs dmask=777,fmask=777 0 0
in the fstab gives a mount that I can't connect to.
Both of those links suggest that they are the same thing but there must be some difference.

---

### Post by stashj on 2006-11-21
I've fixed it now. Just in case anyone else is having this problem. I changed smbfs in my fstab entry to smb and it seems to work fine. I have no idea why this worked so I apologise that I can't elaborate.

---

