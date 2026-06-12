---
title: "[SOLVED] mount error 13: ubuntu to server 2003"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by flying_fish on 2008-09-05
Looking for help to get directly connected to a Server 2003 share.  Connecting directly to a share results in an error, "mount error 13".  However, I am able to mount to dirs below the share???

The following mount to the dir cnt works:
user-laptop:~/mnt$ sudo mount.cifs //server/cnt /home/user/cnt -ouser=user,pass=userpass

The following mount to a share e$ does not work:
user-laptop:~/mnt$ sudo mount.cifs //server/e$ /home/user/e -ouser=user,pass=userpass
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

The following is the result of running smbclient -L:
user-laptop:~/e$ smbclient -L  -U tsmith
Password: 
Domain=[userdomain] OS=[Windows Server 2003 R2 3790 Service Pack 2] Server=[Windows Server 2003 R2 5.2]

	Sharename       Type      Comment
	---------       ----      -------
	E$              Disk      Default share
	atoDB2-database files2 Disk      
	CNT             Disk      

Note that both E$ and CNT are listed by running smbclient -L.  It seems that permissions need to be reset on the 2003 server but I cannot find a difference between the permissions for E$ and CNT

---

### Post by flying_fish on 2008-09-18
Marked as solved as there is a known bug that Nautilus does not show volume shares such that smb://shareserver/ in the address bar will result in Nautilus reporting 0 items even if there are shares.

Also, I am told that one cannot mount a share volume with a name a share name that ends in $ such as E$.

---

