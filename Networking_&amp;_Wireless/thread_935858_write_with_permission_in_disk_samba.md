---
title: "write with permission in disk samba"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by alasarr on 2008-10-02
Hi!I've a server samba with pass. I mount a disk in my file system, adding a file in fstab:

//10.30.102.110/things/intercambio      /mnt/auintercambio      smbfs   username=alasarr,password=pppp,uid=alasarr,gid=smbaurora,rw      0 0

I'd always like me to write files and directories into this folder with specified permissions. By example: I've a file whit permission 744 and when I copy its to /mnt/auintercambio I'd want to have 775 in /mnt/auintercambio

I know it's not usual but I need it for setting permissions in the server

Thanks !!

---

### Post by jones139 on 2008-10-02
I don't think that what you want to do is possible using samba - I have a feeling that Windows doesn't do permissions the same way (no such thing as groups etc.?).  When I used it I had to just set everything to rw permissions.  I gave up eventually and changed to NFS, which does what you want.

---

