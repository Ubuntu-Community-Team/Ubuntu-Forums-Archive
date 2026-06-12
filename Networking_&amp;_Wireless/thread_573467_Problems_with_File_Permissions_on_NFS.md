---
title: "Problems with File Permissions on NFS"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by uris on 2007-10-11
I have an NFS server, but I have found the following problem and can't find a solution yet. The server is accessed by 12 users. However, I have to constantly be going there to change the file permissions whenever they create a new file. All the users belong to the same group, and I configured all the folders to group rw.
 
My exports file looks like this:
 
/dir/to/share 192.168.1.0/255.255.255.0(rw,sync,subtree_check,root_squash)
 
Any ideas on what might solve this issue?

---

### Post by mpokrywka on 2007-10-12
Try setting "set-group-id" permission on directories:
```
chgrp -R users_group /dir/to/share
find /dir/to/share -type d -exec chmod g+s {} \;
```
This forces all new files to inherit group from directory and new subdirs to inherit group and sticky bit (to force group inheritance down the path).

This works on my machine when users log in using ssh, I'm not entirely sure if it will work with NFS. Give a message, if it works.

---

