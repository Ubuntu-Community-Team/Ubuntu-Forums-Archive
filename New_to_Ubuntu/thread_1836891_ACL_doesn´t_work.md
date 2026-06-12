---
title: "ACL doesn´t work"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by greenhat2012 on 2011-08-31
Hello all!
I have ubuntu 10.09 on a Dell poweredge 1850 server.
I need that a normal account could execute "chown" and "chgrp" commands.
I installed the ACL utility ( I modified /etc/fstab file, remounted the filesystem , etc ). However it doesn´t work.
Here are the messages and the error messages when I try to test chown command :
------------------------------------------------
 COMMANDS TO CREATE AND SET THE ACL  :

  setfacl -m u:mortal1:rx /bin/chown
  chacl u::rwx,g::r-x,o::r--,u:mortal1:r-x,m::r-x chown
  
GETFACL OUTPUT :

root@portalito:/bin# getfacl chown
# file: chown
# owner: root
# group: root
user::rwx
user:mortal1:r-x
group::r-x
mask::r-x
other::r--

TEST WITH THE USERNAME "mortal1"

root@portalito:/tmp# su - mortal1
No directory, logging in with HOME=/
$ 
$ 
$ 
$ cd /tmp
$ 
$ 
$ touch test
$ ls -la test
-rw-r--r-- 1 mortal1 mortales 0 2011-08-31 13:39 test
$ 
$ chown mortal2  test
chown: changing ownership of `test': Operation not permitted
$ 


FSTAB OUTPUT :

root@portalito:/etc# cat fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    acl,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3c264868-3304-4f32-9bcb-43e17f10784f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

------------------------------------------------
What is wrong ?

I don´t want add the normal account to the sudo environment!

What can I do to solve this issue ?

Thanks in advance.
Regards.

---

### Post by wt8008 on 2011-09-02
You can allow users to have sudo access to only chown commands. chgrp may not require superuser access.

You can also apply ACL to the files you want to share if owner, group, other permissions is not good enough for your application.

---

