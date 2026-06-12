---
title: "Unable to mount NFS share on client using autofs"
date: 2015-02-06
forum: Networking &amp; Wireless
---

### Post by djibdjib on 2015-02-06
Hi,
I have a debian wheezy distribution running on a pocket server ([cubox-i]("http://www.solid-run.com/")) on my home network.
I export the NFS shares in /etc/exports on the server:
```
/media/myShare   192.168.1.*(rw,all_squash,sync,no_subtree_check)
```
I can mount it on my ubuntu laptop (client side) and I can access the files:
```
mount 192.168.1.2:/media/myShare /mnt/
```
However, I try to automount it using autofs but it doesn't work (I don't see any information in /var/log/syslog)
Here is the content of my /etc/auto.master file :
```
# Mount Cubox NFS shares
/mnt/nfs    /etc/auto.nfs    --timeout=30

```
Here is the content of my /etc/auto.nfs file :
```
# NFS shares rules
myShare   -fstype=auto     192.168.1.2:/media/myShare
```
Do you have any idea about why it doesn't work?
Or any help to debug it? Where should I look?
Thanks!
Djib'

---

### Post by djibdjib on 2015-02-06
I finally found the solution [here]("http://serverfault.com/questions/608332/automount-autofs-mount-issue-on-centos-6-5").
Autofs do his job very well and is working in fact.
```
$ ls -la /mnt/nfs/
total 4
drwxr-xr-x 2 root root    0 febr.  6 13:05 .
drwxr-xr-x 3 root root 4096 febr.  6 12:55 ..

```
You see that /mnt/nfs is 0 byte size while it should be 4096, which is weird.
If I type :
```
$ ls -la /mnt/nfs/myShare
total 40
drwxrwxrwx  8 root root  4096 febr.  3 15:16 .
drwxr-xr-x  3 root root     0 febr.  6 13:12 ..
drwxrwxrwx 10 myUser myUser  4096 febr.  3 18:27 myFile0
drwxrwxrwx  5 myUser myUser  4096 febr.  3 15:09 myFile1
drwxrwxrwx  2 root root 16384 febr.  3 14:06 lost+found
drwxrwxrwx  3 myUser myUser  4096 febr.  3 15:15 myFile2
drwxrwxrwx  2 myUser myUser  4096 febr.  3 14:43 myFile3
drwxrwxrwx  4 myUser myUser  4096 febr.  3 15:16 .Trash-1000
```
The NFS share is accessed and the content is made available.
The NFS share was then available since the beginning but was invisible while I wasn't accessing it...
Hope this will help!

---

