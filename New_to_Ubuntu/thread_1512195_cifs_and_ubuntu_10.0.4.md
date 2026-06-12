---
title: "cifs and ubuntu 10.0.4"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-06-17
i have ubuntu 10.0.4 have in my fstab

//10.0.0.3/documents /media/leanne cifs credentials=/root/.cred-mom,auto 0 0

lance@bermudezl:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //10.0.0.3/documents,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
lance@bermudezl:~$ dmesg | tail
[   68.662673]  CIFS VFS: No username specified
[   68.662681]  CIFS VFS: cifs_mount failed w/return code = -22
[  105.857070] CE: hpet increasing min_delta_ns to 15000 nsec
[  150.033544]  CIFS VFS: cifs_mount failed w/return code = -22
[  256.210360]  CIFS VFS: No username specified
[  256.210367]  CIFS VFS: cifs_mount failed w/return code = -22
[  353.230630]  CIFS VFS: No username specified
[  353.230643]  CIFS VFS: cifs_mount failed w/return code = -22
[  790.995768]  CIFS VFS: No username specified
[  790.995780]  CIFS VFS: cifs_mount failed w/return code = -22

if i take out the credentials=/root/.cred-mom and use the username and password in the file i can connect to the windows7 computer. Why is this not working if works just fin on my opensuse computer using the same info.

---

