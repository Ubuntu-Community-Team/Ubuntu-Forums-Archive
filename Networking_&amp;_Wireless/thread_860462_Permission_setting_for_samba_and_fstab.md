---
title: "Permission setting for samba and fstab"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by newbie618 on 2008-07-15
Hi,

I am having trouble setting the permission with the line below

/etc/fstab >>

//192.168.0.1/share /home/user/share  smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0

It mounts to the linux server running samba, but I can only get modify right.  I cannot delete or create.  Can someone tell me what I need to change.  I am logging in from a Ubuntu 8.04 desktop to a Ubuntu 8.04 server with ebox samba.  If I use a window xp machine, there is no problem.

Thanks

---

### Post by newbie618 on 2008-07-15
Hi,

I have figure out part of the problem.  Dosemu will run the program when the dos program is installed on the local drive but not on the network share directory.  Dosbox will run the program with no problem and a bit easier to configure.  It is slow and I guess I have to figure how to get Dosemu going.

Thanks

---

