---
title: "NFS issue with 7.01 - rpc error program not registered"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by thompsw on 2008-03-21
Hi -- I'm having a problem getting NFS setup.  I've defined the shares (both Samba and NFS) with the Gnome utility; I've even run exportfs, I've installed the required packages -- Gnome does that for you, I've rebooted several times trying different things. The shared folders are setup in /etc/exports (the Gnome utility does that for you) and they look correct.  I have tried different approaches with validating users -- through the Gnome utility, through use of hosts.allow etc. (hosts.allow and hosts.deny are currently empty).  I've also turned off all firewalls on the machines in question, thinking that perhaps that was the issue.

I'm getting "rpc error program not registered" from the client when I try to mount the folder.

Both the client and the server are identical setups, side by side behind a router.  

ps Samba works sharing the folders with XP running on parallels on the client machine, but NFS on the underlying 7.01 does not.

any ideas ?  I've read so many how-to's over and over but still cannot solve this problem.  I'm not exactly a newbie, having setup NFS before on 2.4 Caldera kernels ... but I'm missing something very obvious here.

Thanks in advance ...

---

### Post by thompsw on 2008-03-21
has anyone got any ideas ?  I'm completely stuck at this point.

Thanks.

---

### Post by tjapko on 2008-03-23
I had the same problem and found the solution at :

[http://nfs.sourceforge.net/nfs-howto/ar01s07.html#unable_to_mount_fs](http://nfs.sourceforge.net/nfs-howto/ar01s07.html#unable_to_mount_fs)

Use as root /etc/init.d/nfs-kernel-server restart.

Good luck

---

