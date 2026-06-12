---
title: "network sharing between ubuntu systems."
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by tmasboa on 2005-08-09
How do you share folders and files between Ubuntu systems? I know you can use Samba with Windows, but what do you use between Linux? NFS? and how do you configure it?

---

### Post by jamesrw on 2005-08-09
I believe you can use samba between linux machines as well  :)

---

### Post by PeP on 2005-08-09
if you just copy something from time to time use scp 
konqueror provides a nice gui for it with fish urls:
fish://login@myothercomputeradress:~/

its quite a nice feature when you use public key authentication for ssh

else you should use either  samba or nfs 

for nfs 
1. install nfs-kernel-server for the server, nfs-common for the client

2. then you configure the server:
sudo gedit /etc/exports
mine looks like this:
```

#/etc/exports
/home/pep/share myothercomputer(rw,sync)

```
meaning that I share the folder ~/share with myothercomputer, with read and write allowed.

3. on the other side I add a line to /etc/fstab:
```

#/etc/fstab
[...]
myfisrtcomputer:/home/pep/share /media/share nfs defaults,users,noauto 0 0

```
replace noauto by auto to mount it automatically.


4. i start the server like this
```
 
sudo /etc/init.d/nfs-kernel-server start

```
(first time only after that it is don autmatically at boot)

5. then you can mount the share like this:
```

sudo mount /media/share 

```


6. Do not forget  to open your firewall on the server for the nfs port.


->>> the man pages are very helpfull

---

