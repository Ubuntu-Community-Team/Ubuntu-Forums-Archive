---
title: "What is the preferred way to share files between 2 Linux machines over LAN?"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by chick on 2008-10-13
I know I can set up SSH to do this but I'm wondering whether there is something simpler?

---

### Post by kevdog on 2008-10-13
Only ways Im aware of are ssh, ftp, samba, or more encrypted options such as sshfs.  It really depends what your needs are. Either of the options will work.

---

### Post by maciu on 2008-10-13
Well since you want to share files between two Linux boxes i would recommend the native way - NFS.

---

### Post by superprash2003 on 2008-10-13
yea.. NFS is pretty good for a linux only network..or as mentioned samba..

---

### Post by Iowan on 2008-10-13
SSHFS seems pretty painless - once SSH is set up.  I have it installed, but haven't really tried using it.

---

### Post by chick on 2008-10-13
Thanks all, looks like NFS is the native way I was looking for.

---

