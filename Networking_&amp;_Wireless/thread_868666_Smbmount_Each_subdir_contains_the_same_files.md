---
title: "Smbmount: Each subdir contains the same files"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by JochenJung on 2008-07-24
Hi folks,

Im trying to mount an nfs share, which works. However I'm not able to change into subdirectories.


Here is what I did:

root@itjungj-pc:~# mount //172.29.129.240/I_company$ /mnt/ -o username=itjungj,password=pw,lfs


It works:

root@itjungj-pc:~# l /mnt/
total 257K
drwxrwxrwx  1 root root    0 2008-07-21 16:10 .
drwxr-xr-x 21 root root 4.0K 2008-06-18 08:27 ..
drwxrwxrwx  1 root root    0 2006-11-13 09:54 Hosting
-rwxrwSrwx  1 root root 249K 2008-07-21 16:10 treeinfo.wc
[...]


But:

root@itjungj-pc:~# l /mnt/Hosting/
total 253K
drwxrwxrwx 1 root root    0 2008-07-21 16:10 .
drwxrwxrwx 1 root root    0 2008-07-21 16:10 ..
drwxrwxrwx  1 root root    0 2006-11-13 09:54 Hosting
-rwxrwSrwx  1 root root 249K 2008-07-21 16:10 treeinfo.wc
[...]

root@itjungj-pc:~# l /mnt/Hosting/Hosting/
total 253K
drwxrwxrwx 1 root root    0 2008-07-21 16:10 .
drwxrwxrwx 1 root root    0 2008-07-21 16:10 ..
drwxrwxrwx  1 root root    0 2006-11-13 09:54 Hosting
-rwxrwSrwx  1 root root 249K 2008-07-21 16:10 treeinfo.wc
[...]

As you can see, each subdirectory seams to contain the very same content, which is not true.

If I connect to the same share using a windows client, everything works fine.

I would be glad, if one of you has an idea, what I am doing wrong..
I'm running Ubuntu 8.04.

Regards, Jochen.

---

