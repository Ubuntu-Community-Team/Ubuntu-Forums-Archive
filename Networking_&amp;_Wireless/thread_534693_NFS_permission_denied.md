---
title: "NFS permission denied"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by tilapia on 2007-08-25
I've installed nfs-kernel-server on a Feisty box and set up /etc/exports as follows:

```

/home 192.168.0.*(rw,no_root_squash,no_subtree_check)
/var/www 192.168.0.*(rw,insecure,no_subtree_check)
/nas 192.168.0.*(rw,insecure,no_subtree_check)

```

I've created mount points on another Feisty box and I'm trying to mount the NFS shares as follows:

```

192.168.0.101:/nas /media/movies nfs defaults 0 0
192.168.0.101:/var/www /media/webserver nfs defaults 0 0
192.168.0.101:/nas/storage /media/itunes nfs defaults 0 0

```

I've got a Debian Etch server which is configured virtually identically (as far as I can tell) and the mounts mount correctly. However, when I run sudo mount -a I get the following errors: 

```

mount: 192.168.0.101:/nas failed, reason given by server: Permission denied
mount: 192.168.0.101:/var/www failed, reason given by server: Permission denied
mount: 192.168.0.101:/nas/storage failed, reason given by server: Permission denied

```

I'm not really sure how to troubleshoot this problem. Please can someone give me some pointers? A previous Dapper machine I had also used the same config (as far as I can tell) and that seemed to work correctly.

Many thanks, 
Matt

---

### Post by WMG_Perth on 2007-08-26
Hi,

Try changing you exports file on the server to

/home 192.168.0.0/255.255.255.0(rw,no_root_squash,no_subtree_check)
/var/www 192.168.0.0/255.255.255.0(rw,insecure,no_subtree_check)
/nas 192.168.0.0/255.255.255.0(rw,insecure,no_subtree_check)

then sudo exportfs -ra

and restart nfs.
Hopefully that will help

---

### Post by tilapia on 2007-08-26
Awesome. That worked a treat. Thanks a lot for your help.

---

