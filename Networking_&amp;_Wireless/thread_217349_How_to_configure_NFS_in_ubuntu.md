---
title: "How to configure NFS in ubuntu?"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by nishant on 2006-07-17
hello guys

     i want to configure NFS. how to configure it as there is no export file in /etc/export. and also some commands like nmapr not working.please help me out. i want to form a network of say 7 to 8 machines, so please give me details.

tnx

---

### Post by joft on 2006-07-17
Hi,

so you want to setup a NFS server, right? You have to install the packages "nfs-common", "nfs-kernel-server" and "portmap". Then there should be an almost empty /etc/exports file, which you have to fill with life (see "man exports"). After changing the exports file, call

```

sudo exports -ra

```

or restart the NFS server by

```

sudo /etc/init.d/nfs-common restart
sudo /etc/init.d/nfs-kernel-server restart

```

---

