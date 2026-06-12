---
title: "Sharing content between local users"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by bit_jammer on 2009-12-07
Hello. I have installed ubuntu 9.10 in my home laptop and we're a couple os us using it and I would like to have a partition where we are able to share contents and also modify it. So thatm I've created a new ext4 partition but how do I mount it so it belongs to root (or other user) and users group? Is it possible to make that any content we place on the shared folder has the same properties, I mean, belongs to one user but the users in group are able to modify it?

Thanks.

---

### Post by bodhi.zazen on 2009-12-07
You mount it by adding an entry in /etc/fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

In terms of sharing, you can use shared group, such as users, and set the sticky bit or use ACL.

[http://www.cyberciti.biz/faq/linux-setup-shared-directory/](http://www.cyberciti.biz/faq/linux-setup-shared-directory/)

Or use ACL. ACL take a bit longer to learn, but give a finer grain of control.

See :

[http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)
        The second link is a nice discussion, see pot #9 for ACL.


And eiciel is a gui tool

[http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html](http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html)

Eiciel is in the Ubuntu repositories, so easy to install.

---

### Post by sandyd on 2009-12-07
just chmod the directory to 777

---

### Post by bit_jammer on 2009-12-07
That was great (and fast). Thanks a lot. I'll give a try.

---

### Post by bit_jammer on 2009-12-08
Well. I must be doing something because this [http://ubuntuforums.org/showpost.php?p=832721&postcount=9]("http://ubuntuforums.org/showpost.php?p=832721&postcount=9") is not working.
This is what I've done:
[LIST]
[*]Create a new directory: sudo mkdir /shared
[*]Change permissions to the directory:sudo chgrp -R users /shared
[*]Added this line to the fstab
```
UUID=a8fce815-8891-4a81-9b40-6ec3d5747a4f  /shared   ext3         rw,suid,exec,users,acl           0  0
```
[*]mount /shared
[*]sudo setfacl -dm g:users:rwx /shared
[*]getfacl /shared (this produces a good output with the information about the groups)
[*]**[COLOR="Red"]Here comes the problem:[/COLOR]**
[*]cd / && ls -l
```
drwxr-xr-x+  3 root       **[COLOR="Red"]root[/COLOR]**      4,0K 2009-12-08 00:32 shared
```
[*]So that, none of the group users can create,delete under shared
[/LIST]
To be clear, every time I mount the partition it becomes owned by root:root. No matter if the folder is previously owned by  root:users, once I mount it, it becomes root:root.

So, I keep on doing some research, but this is not working. I've to say that I'm running 9.10.

---

### Post by bit_jammer on 2009-12-08
> **carlee said:**
> just chmod the directory to 777

Well that's the easy way, but not the way I wanna do. Linux/Ubuntu is supposed to be configurable in that way. 
What I would like (maybe it's not possible) is to have a shared unit where everything belongs to a particular group and any new content has rights for the group.

---

### Post by bodhi.zazen on 2009-12-08
Mount the partition.

then 

```
sudo chown root:group_you_want_for_share /shared
```

---

### Post by bit_jammer on 2009-12-08
Well. I managed to do it. Finally I decided to mount the file system on ntfs. It's not what I wanted, but ....
This is how my fstab looks like:
```
/dev/sda8  /home/shared ntfs-3g user,uid=root,gid=shared,fmask=0117,dmask=0007 0 0
```
And this is the result:
```
drwxrwx---  1 root       shared    4,0K 2009-12-08 21:43 shared
```
```

bitjammer@bitjammer-hdx-ubuntu:/home/shared$ mkdir foo
bitjammer@bitjammer-hdx-ubuntu:/home/shared$ ll
total 0
drwxrwx--- 1 root shared 0 2009-12-08 21:50 foo
bitjammer@bitjammer-hdx-ubuntu:/home/shared$ touch file
bitjammer@bitjammer-hdx-ubuntu:/home/shared$ ll
total 0
-rwxrwx--- 1 root shared 0 2009-12-08 21:51 file
drwxrwx--- 1 root shared 0 2009-12-08 21:50 foo

```

```

bitjammer@bitjammer-hdx-ubuntu:/home$ getfacl shared/
# file: shared/
# owner: root
# group: shared
user::rwx
group::rwx
other::---

```

If someone manages to make this work with ext3/4, please, let me know

---

