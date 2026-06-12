---
title: "NFS Group Permissions"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by spauldingsmails on 2008-07-11
I have a couple of NFS exports where I would like to set the default permissions when a file is written from a client to the server.

There are two types of exports; a home export which is a directory where users can store files that only they can access (i.e. their remote home directory) and a shared directory where users of the same group can share files and documents.

When a user writes to their remote $HOME directory, the permissions are correctly set to rwx------ (or rw------- for files), but for the shared directory I would like the default permissions to be rwxrwx--- (or rw-rw---- for files) where owner and group can read and write sub directories and files. However, the shared directory just defaults to rwxr-xr-x and I cannot see a way of changing this. Changing the umask on the /home/shared directory seems to do nothing and so far I have not been able to find any documentation on how to accomplish this.

Any help much appreciated.

---

### Post by df6269 on 2008-07-11
Example:
bryan userid:100 groupid:100
/home/bryan   192.168.1.0/24(rw,all_squash,anonuid=100,anongid=100)

---

