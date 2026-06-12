---
title: "Samba share mount - garbled characters and recursive directories"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by bipco on 2007-12-27
Hello

Trying to mount a Samba share in the filesystem and I get garbled characters (like it's the wrong character set or something), and within the mounted directory is the same one again  (and apparently again within that, but I can't change into that one).

Mounting using:

bipco@thinkBok:~$ sudo smbmount //192.168.1.100/W /mnt/network/W

The mount in the Terminal looks like this:

bipco@thinkBok:/mnt/network/W$ ls
total 2675750160
?--------- ? ?                     ?                ? 
?--------- ? ?                     ?                ? 
?--------- ? ?                     ?                ? 
?--------- ? ?                     ?                ? 
?--------- ? ?                     ?                ? 
---------- 1 root 128412437720000000 1940-10-24 03:26 6??
---------- 1 root 128412437720000000 1940-10-24 03:26 #8??
---------- 1 root 128413595100000000 1940-10-24 03:26 gese
---------- 1 root 128414316000000000 1940-10-24 03:26 Z?:?8??

Have tried some variations on the mount command, including cifs (which gives an error 20 = not a directory, and doesn't mount anything).

The share shows up OK in Nautilus on the desktop when using Connect to server, but I want to be able to use rsync for copying for speed, rather that have to tar everything so as to get round permission problems for root owned files, etc.

Any thoughts appreciated.

Thanks

Warren

---

