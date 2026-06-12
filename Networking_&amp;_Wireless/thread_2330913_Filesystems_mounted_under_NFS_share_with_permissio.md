---
title: "Filesystems mounted under NFS share with permission denied despite crossmnt"
date: 2016-07-16
forum: Networking &amp; Wireless
---

### Post by rsevero on 2016-07-16
Hi. I recently upgraded my home network to 16.04. I use nfs mounts and one of the mounts uses cross mounting, i.e., I have one share on my nfs server but on the server, under this share, on several subdirectories I have several other filesystems mounted. I want all these filesystems accessible on my nfs clients. This worked just fine up to version 15.10. Now my 16.04 clients return a 


*Impossible to access /multimidia/musicas: Operation not permited*


error when I try to acess one of these extra filesystems through the nfs share.


I've tested on last client that is still running version 15.10 and the mount is working as expected on it so I believe the problem isn't on the server which has already been upgraded do 16.04.


Here is my share line on the server's /etc/exportfs file:


*/multimidia     192.168.13.0/24(rw,sync,no_subtree_check,crossmnt,root_squash)*


And here is my fstab entry on one of my clients:


*192.168.13.254:/multimidia /multimidia nfs wsize=8192,rsize=8192 0 0*


Any ideas on how to make this work again as expected on 16.04 clients?

---

### Post by jules98 on 2016-08-06
Hi,

Just got the same problem on a Linux Mint 18 (16.04 based) box.
I haven't a solution, but a workaround: check once the mount point as "root" user and it will work for normal users...

> jdp@amroth:~$ ls -l /mnt/ftp/public
ls: cannot access '/mnt/ftp/public': Operation not permitted
jdp@amroth:~$ sudo ls -l /mnt/ftp/public
total 40
drwxrwxr-x   2 rtkit users  4096 Apr 24 22:00 android
drwxr-xr-x 116 jdp   users  4096 Aug  1 08:48 downloads
drwxr-xr-x   3 jdp   users  4096 Feb  9  2007 espagnol
drwxr-xr-x   3 rtkit saned  4096 Oct  4  2015 incoming
drwxr-xr-x   6 jdp   users  4096 Jul 16  2014 iso
drwxr-xr-x   2 saned uuidd 20480 Jul 18 07:40 scanner
jdp@amroth:~$ ls -l /mnt/ftp/public
total 40
drwxrwxr-x   2 rtkit users  4096 Apr 24 22:00 android
drwxr-xr-x 116 jdp   users  4096 Aug  1 08:48 downloads
drwxr-xr-x   3 jdp   users  4096 Feb  9  2007 espagnol
drwxr-xr-x   3 rtkit saned  4096 Oct  4  2015 incoming
drwxr-xr-x   6 jdp   users  4096 Jul 16  2014 iso
drwxr-xr-x   2 saned uuidd 20480 Jul 18 07:40 scanner
jdp@amroth:~$ 


Regards, Jacques-D.

---

