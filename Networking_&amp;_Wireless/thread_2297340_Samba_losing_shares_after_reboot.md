---
title: "Samba losing shares after reboot"
date: 2015-10-02
forum: Networking &amp; Wireless
---

### Post by boz_1812 on 2015-10-02
Hi,

I'm new to Ubuntu and so have many mysteries to solve.  I have several PCs networked with my main PC running Ubuntu 14.04 and another WIN7.  The Ubuntu PC has a secondary HDD to act as my "file sever" and is formatted NTFS so WIN7 can access it.  I've setup the workgroup (WIN workgroup name) in Samba, have a common user account across all PCs and have designated directories to share through Samba.  Fine, all PCs can read and write to the shared directories.
When I reboot the Ubuntu PC the shares are lost and although WIN7 can see the directories they can't be opened.  I have the same issue if I share the directories using the "Local Network Share" method.  All works fine until I reboot the Ubuntu PC, when I then have to re-share the directories via "Local Network Share".
The primary HDD doesn't have this problem, but then it's formatted ext4.
I'm not sure if the problem arises from the NTFS formatting, the fact that it's a secondary HDD, or there is a problem with Samba.
Any thoughts would be appreciated.
Thanks.

---

### Post by TheFu on 2015-10-02
The formating of the samba storage as NTFS isn't needed. Any Linux file system would be preferred, actually.

Have you looked at the logs for samba and on the client machines? The samba logs are pretty helpful, BTW.

---

### Post by boz_1812 on 2015-10-04
Thanks.  I've reformatted the second HDD (label = YPC6) to ext4 and everything is fine with one exception.
When I reboot the Ubuntu PC WIN7 lists the shared directories, but can't open them.  I checked /media/bob and the secondary HDD was not listed.  The samba log shows numerous entries like,

[2015/10/05 10:21:36.198207,  0] ../source3/smbd/service.c:792(make_connection_snum)
  canonicalize_connect_path failed for service shared-files, path /media/bob/YPC6/shared-files

I opened Nautilus and browsed the secondary drive.  The individual directories didn't have the icon flag indicating they were shared, but I don't know if that has any significance.
I tried the WIN7 PC again and now it can read/write to the shared drive.  It seems like the secondary HDD is not mounting automatically on boot, but opening Nautilus mounts the drive?
Thanks.

---

### Post by TheFu on 2015-10-04
A new partition won't be automatically mounted until you tell it that you want it mounted, how to mount it and where to mount it. This is a security consideration.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by boz_1812 on 2015-10-10
OK.  Thanks for your help.

---

