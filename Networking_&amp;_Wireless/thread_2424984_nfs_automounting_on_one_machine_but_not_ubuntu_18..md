---
title: "nfs automounting on one machine but not ubuntu 18.04"
date: 2019-08-19
forum: Networking &amp; Wireless
---

### Post by nyktovus on 2019-08-19
i have a machine in my garage running lubuntu 16.04
its fstab is as follows


192.168.2.5:/data/trunk 	/home/userguy/Trunk	 nfs 	rw,hard,intr,rsize=8192,wsize=8192,timeo=14 	0	 0
192.168.2.5:/data/trunk/video         /home/userguy/Trunk/video      nfs    rw,hard,intr,rsize=8192,wsize=8192,timeo=14     0        0       

works great out there. just installed ubuntu 18.04 in the house on a system.. installed the needed nfs-common
and used the same fstab contents.. 
and no dice. no automount.
but sudo mount-a works from terminal.
but mount -a (non sudo) or trying to mount from the file manager spits out a "root only bro" error 
help?

---

### Post by TheFu on 2019-08-19
Did you modify the export on the server to allow the new machine access?  Prove it.
Simplify and retest.

Are all connections wired ethernet?

mounting requires root/sudo.  And NFS access by root from a different machine is usually converted to nobody access.

---

