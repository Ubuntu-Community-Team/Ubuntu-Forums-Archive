---
title: "NFS share not accessable with automount on /net: file or folder not found"
date: 2015-11-04
forum: Networking &amp; Wireless
---

### Post by bbruecker on 2015-11-04
Hi,

I have on Ubuntu Server 14.04 two NFS share, which I want to access by typing **/net/server/share**. The server has two shares, but only one is accessible.

Here is the content of the servers export file:
```
/data2/owncloud/bbruecker  192.168.88.0/255.255.255.0(rw,sync,all_squash,anonuid=33,anongid=33)
/data2/aufnahmen  192.168.88.0/255.255.255.0(rw,sync,all_squash,anonuid=116,anongid=10
```

I also tried it with "no_subtree_check" in both decelerations. No difference.

For accessing the nfs servers I use usually autofs by accessing the /net folder ([https://wiki.archlinux.org/index.php/Autofs](https://wiki.archlinux.org/index.php/Autofs)). It works in most cases, but not now.

The server is in the hosts file of the client (server name is 'sithonia'). I can only access the second share by typing ls /data2/aufnahmen. The second share works on the client by **ls /net/sithonia/data2/aufnahmen/** and I can cd into subfolders. The first share displays after **ls /net/sithonia/data2/owncloud/bbruecker** "folder or file not found". Seemed to me for permission trouble. So I checked them on the server: On the server www-data is the owner of bbruecker and all sub folders with read and write permissions. It's the same for the group www-data:

Here are the permissions on the folder I cannot access from the client:
```
drwxrwxr-x 8 www-data www-data 4,0K Nov  4 13:29 bbruecker
```

What's wrong?

---

### Post by TheFu on 2015-11-05
Please post the /etc/auto.master and /etc/auto.*  <--- whatever file is referenced in auto.master.
I've posted mine here previously.

---

