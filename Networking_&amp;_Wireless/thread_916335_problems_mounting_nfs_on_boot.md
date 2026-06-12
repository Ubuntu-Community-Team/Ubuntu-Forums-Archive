---
title: "problems mounting nfs on boot"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by CalZing on 2008-09-10
I have recently installed NFS on my server. Unfortunately, my desktop computer behaves really strange. I'm using a wired network connection with static IP.

The thing is, when the computer has booted, I can mount the NFS share with the mount option. The problem is that i can't automount it in /etc/fstab... I post my /etc/fstab here so you could check. Of course does the mount points exists and are in right case whatsoever

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=91e74452-5231-4f93-9c51-e751240013bc / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdc5
UUID=f044eafd-d927-4550-a506-3d1e712f30d8 /home/andreas ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdc1
UUID=2248814A48811E23 /windows ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
UUID=c01424c3-4183-4c95-b36a-78a6c2a65878 /ubuntu-studio ext3 nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
84.55.119.92:/var/ftp /home/andreas/robert nfs nouser,_netdev,atime,auto,rw,dev,exec,suid 0 0


---

