---
title: "*** sharing ntfs partition via samba"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by josh on 2006-09-26
hello!

i was able to setup samba in a way that its not going to ask for passwords and will let any users in my lan to access my shared folders.

the problem i have is that my ntfs partition is not viewable by me or by any other pcs on the lan. 

here is my smb.conf:

```
[global]
server string = johnny
workgroup = BAHAY
restrict anonymous = no
security = share


[movies]
path = /media/windrive
public = yes
writable = no
create mask = 0777
directory mask = 0777

[home]
path = /home/josh
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[public]
comment = Public Folder
path = /home/public
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

hosts allow 127.0.0.1 192.168.0.2 192.168.0.3 192.168.0.5 192.168.0.6

```

im able to see my public folder and home folder using other pcs and my ubuntu box but not the movies folder.

i have disabled my firewall. i also am a member of the plugdev group.

help please...

---

### Post by lukanium on 2006-09-26
Please show your /etc/fstab ....:-k

---

### Post by josh on 2006-09-26
here is my /etc/fstab

```
josh@johnny:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda8       /media/tunnel   vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       /media/winbank  ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda1       /media/windrive ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
josh@johnny:~$

```

---

### Post by josh on 2006-09-26
got it! thanks for the idea lukanium! i forgot to check the permission! set my permission to umask=0222. thanks

---

