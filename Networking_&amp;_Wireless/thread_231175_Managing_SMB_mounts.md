---
title: "Managing SMB mounts"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by ltmon on 2006-08-07
Hi All,

I have several Samba shares I connect to whilst at work.  I use smbfs entries to mount them from my fstab.

I find this better and **_much_** faster than any gui samba browser (such as Konquerors smb:/ protocol), so would prefer to keep using it this way.

The only problem is that whenever I change network (move from wireless to wired), or just go home with my laptop suspended everything kind of freezes up with those mounted directories.  Sometimes I can force them to umount, but often I just give up and reboot.

Currently I have to manually unmount every directory before changing networks or disconnecting.

I would love them to automatically unmount whenever I disconnect from one network.

Even better would be to remount when the network changes, but it's not as essential as the top one.

Any ideas how to achieve this?

L.

---

### Post by fourchannel on 2006-08-07
what about running this script before you disconnect from a network.

```
sudo /etc/init.d/umountnfs.sh start
``` 
it umounts all network filesystems and non critical susbsystems. I ran it and then remounted my SMB shares with the system up and running with no problems. So you don't have to restart the system after running.

---

