---
title: "nfs problem with mounting"
date: 2005-06-07
forum: Networking &amp; Wireless
---

### Post by fahad on 2005-06-07
Hi,

i have i problem with NFS,
i setup every things between 2 machines to share files,
but when i try to mount the other machine folders i got :
 mount: RPC: Program not registered


what should i do with it ?

---

### Post by dataw0lf on 2005-06-08
Do you have the package 'autofs' installed?

---

### Post by fahad on 2005-06-08
yes

---

### Post by fahad on 2005-06-08
i restarted the machines,

it now works :)

thanks,

---

### Post by matthias_k on 2005-10-17
I am having the same issue here, but a restart did not work for me. This autofs package is installed. Any ideas?

I noticed that when you first start the shares-admin tool, it will ask you if you want to install samba and/or NFS. On my breezy installation, I selected both and everything worked out of the box.
On my Hoary installation, I remember I only checked SMB back when I started it the first time, and now it doesn't give me the option anymore to install NFS. Maybe it's installing something I missed when manually installing NFS thereafter? What packages do I need for NFS to work? At least, I can share my files with NFS, but I can't mount another NFS network share. Very odd.

---

### Post by cubeice24 on 2006-04-26
I'm running Hoary and here's the list of things I did on my **server** machine in order to get a succesful mount:
1)apt-get-installed portmapper, nfs-common and nfs-kernel-server
2)edited /etc/exports : /home/ez/Shared 139.8.8.25(rw)
3)restarted the following services:
   /etc/init.d/portmap restart
   /etc/init.d/nfs-common restart
   /etc/init.d/nfs-kernel-server restart

---

