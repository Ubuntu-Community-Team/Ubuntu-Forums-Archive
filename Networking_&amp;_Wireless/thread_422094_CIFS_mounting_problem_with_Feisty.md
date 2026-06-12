---
title: "CIFS mounting problem with Feisty"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by abovett on 2007-04-24
I've got several Feisty installs (some physical, some VMware VMs). Some were upgraded fom Edgy, and some were clean installs. The upgraded boxes are fine, but on the two clean installs, an attemt to mount a CIFS share fails like this:

```
andrew@t-ubuntu-3:~$ sudo mount -t cifs //SOL/testdir /home/andrew/mnt/SOL/testdir -o username=andrew,workgroup=ajblan
mount: wrong fs type, bad option, bad superblock on //SOL/testdir,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmsg says:
```

[20235.230158]  CIFS VFS: cifs_mount failed w/return code = -22

```

The share is accessible through gnome VFS, so I know it's reachable in principle.

Anyone got any suggestions?

Andy

---

### Post by abovett on 2007-04-24
Found the answer - though I don't understand it!

I have to install smbfs.

I thought smbfs and cifs were distinct, and smbfs was depricated, whilst cifs was in the kernel. So why do I need smbfs installed?

Andy

---

### Post by LookUpSeeBlu on 2007-11-26
Thank you very much for this post and answer!  I have been fumbling with this for days!  I just recently switched from Gentoo to Ubuntu and the mount script I wrote worked fine in Gentoo, but not in Ubuntu.  Once I installed smbfs it worked.

Thanks very much!

---

