---
title: "Very high iowait over mount.cifs"
date: 2016-06-15
forum: Networking &amp; Wireless
---

### Post by toni6 on 2016-06-15
Hi,

We have 2 servers which pull backups from our NetApp over CIFS.
The first server (Ubuntu 14.04.4) is on the same subnet as the NetApp while the second server (Ubuntu 14.04.3) is on another subnet (but has full access).

Both servers use the same mount options for the CIFS share mount on the NetApp:
//xxx.xxx.xxx.xxx/public   /mnt/FileSrv/Public   cifs   noauto,username=backup,password=secret,workgroup=domain.local,iocharset=utf8   0       0

When I run an rsync on the second server, it runs as it should: fast and with very little iowait.
When I run the same rsync on the first server, the transfer goes at +/- 200kbps and throws the rsync process on iowait for 99%.

Both servers have no hardware issues as other backups (rsync over SSH) run perfect.
The NetApp serves all files fast (no complaints from the business).
Also when I run the rsync on the first server against a share on a Windows server, it goes like it should without iowait.

So it seems that the first server has an issue with mount.cifs towards the NetApp.

Any clues where to look?

Thanks.

---

### Post by toni6 on 2016-06-15
Update: I upgraded all the packages on the second server. Result: also slow!

I guess the problem is Samba which is upgraded from version 4.1.6+dfsg-1ubuntu2.14.04.13 to version :4.3.9+dfsg-0ubuntu0.14.04.3

Will try to revert the upgrade of samba and see what it does.

---

### Post by toni6 on 2016-06-15
Reverting helped on the second server, but not on the first server ...

---

