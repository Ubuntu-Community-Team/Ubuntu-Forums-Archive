---
title: "Problem with mount windows shared folder"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by yudigadget on 2007-09-19
Hi ubuntu lovers,
I have problem with mount windows shared folder on ubuntu
My /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=29a692f0-53c9-4634-99dd-61045ab593dc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fe1b4a98-7ed5-4c8c-82c5-20206d52a4e8 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
//172.168.100.200/Tour /mnt/Tour cifs auto,user,username=operation02,workgroup=WORKGROUP,password=product,uid=500,gid=500,file_mode=0777,dir_mode=0777,rw 0 0

the username, password, workgroup, etc are correct!

well, everytime i save or create file into windows shared folder, i always got read only permission, something like this:
[IMG]http://img206.imageshack.us/img206/6043/screenshot1ip9.png[/IMG]

the permission of that file is:
[IMG]http://img211.imageshack.us/img211/1792/screenshot3nz4.png[/IMG]

then i must do this from terminal:
sudo -i (with password)
umount -a
mount -a

it really bothering me.. that i always must do that ritual to make the read-only gone.

then i hit F5 to refresh that shared folder and the lock key is gone
[IMG]http://img187.imageshack.us/img187/6313/screenshot2ts6.png[/IMG]

and the permission of that file changed to
[IMG]http://img124.imageshack.us/img124/6097/screenshot4mc7.png[/IMG]

so how to fix this problem?

i really need your help :(
thanks for help!

---

### Post by yudigadget on 2007-09-19
any help? please.... i need it so much

---

