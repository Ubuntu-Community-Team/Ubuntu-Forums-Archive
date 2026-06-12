---
title: "Fstab entry to mount network share isn't working?"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2006-11-09
I would like some help here, I have followed this guide ([http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)) word for word and this mount point just won't mount upon boot but if I do sudo mount -a it works but with the following error: [mntent]: warning: no final newline at the end of /etc/fstab. 

this is my fstab 
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda5       /windows        vfat    defaults,utf8,umask=007,gid=46 0   1
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//UBUNTU/lptp-backups   /home/daniel/SMB-laptop-backups smbfs   uid=1000,gid=1000,credentials=/home/daniel/.smbpasswd        0       0
the guide states this about my fstab entry: //servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,uid=mylinuxusername,gid=mylinuxgroupname 0 0
which is what mine follows.

can anyone help me troubleshoot this?

---

### Post by FrodoB on 2006-11-09
Maybe add a new blank line to the end of fstab and auto to the options?

---

### Post by featherking on 2006-11-09
This guy had a similar problem and fixed it, perhaps you can benefit from it as well? [http://www.ubuntuforums.org/showthread.php?t=282008]("http://www.ubuntuforums.org/showthread.php?t=282008")

---

### Post by dannyboy79 on 2006-11-09
SOLVED, the solution to this error: [mntent]: warning: no final newline at the end of /etc/fstab
was the fact that you need to hit enter after the last line.
and then the main solution is to use /etc/rc.local by adding your mount point in the file. I don't know how it works but it does. the solution is documented here ([https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/comments/48](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/comments/48)) but the noauto option isn't vaild for smbfs so you can exclude that.

---

### Post by FrodoB on 2006-11-09
Congrats

---

