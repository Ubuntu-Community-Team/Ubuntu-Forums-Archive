---
title: "Permission problems with NFS."
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by davemar on 2008-07-23
I'm trying to get NFS working between my two PCs. My server PC (32bit), running Ubuntu 7.10 has a hostname pc1. The client PC (64bit) running Ubuntu 8.04 has a hostname pc2. 

I've got the two ping-ing and ssh-ing quite happily to each other.

On the client PC I fixed the bug with nfs-common described here: [https://bugs.launchpad.net/ubuntu/+bug/213444/comments/23]("https://bugs.launchpad.net/ubuntu/+bug/213444/comments/23").

On pc1 (server) my /etc/export file looks like this:
```
/home 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check,no_root_squash)
/win1 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check,no_root_squash)

``` 

/home is ext2, and /win1 is fat32.

I kicked things into action (so I think!) with:
```
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -a
```

On the client PC, the relevant line (to mount /win1) of /etc/fstab looks like this:
```
pc1:/win1      /mnt/temp       nfs     rsize=8192,wsize=8192,timeo=14,intr              0       0

```

When I try a "sudo mount -a" I get this:
```
/usr/local/sbin/mount.nfs: not using string
mount.nfs: pc01:/win1 failed, reason given by server: Permission denied
```

Is there something obvious I'm missing out?

I've turned the firewall off on both machines as far as I know. Though I would like to know how to set the firewall correctly once I've got this working (ports, etc).

Cheers, Dave.

---

### Post by davemar on 2008-07-25
Still no ideas anyone?

---

### Post by Endwin on 2008-07-25
Looks like you have the addressing wrong for NFS. You are defining the netmask in the network. 

Should be something like this
```

/home 192.168.0.0/24(rw,sync,no_subtree_check,no_root_squash)
/win1 192.168.0.0/24(rw,sync,no_subtree_check,no_root_squash)

```

Run ```
sudo exportfs 
``` again and see if you can access it.

Also make sure connecting computers have a 192.168.0.XXX address.

---

### Post by Jose Catre-Vandis on 2008-07-25
Also, make sure you are using the full path both in your exports file and your fstab. for example

/win1 might look like /win1 on the server and to the NFS server, but it could actually be /media/win1 and you need to delcare this on both machines or it won't connect, and will give the Permissions error. Similarly /home as you see it when logged in is actually /home/username.

I had a few fights with this along the way to NFS heaven :)

---

### Post by davemar on 2008-07-25
Endwin, I tried the /etc/exports file change as you suggest, but it made no difference. I thought the /24 was effectively the same as 255.255.255.0? 

Jose, the directories are correct, I triple checked those too. Still no joy.

Could the /etc/fstab on the server have any effect on permissions?

---

### Post by davemar on 2008-07-25
Fixed it!! What a silly fool I am! I had the IP addresses as 192.168.0.x in the export files, where they should have been 192.168.1.x. I can't believe I should have made such a daft mistake and not spotted it. Ones look too much like zeros, binary will never catch on.... :)

---

### Post by Jose Catre-Vandis on 2008-07-25
:lolflag: Please mark as solved? :D

---

