---
title: "Mounting NFS"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-03-26
In an attempt to set up a NFS server between two local machines, I have come to a point where I think that I need to restart the nfs-common on the client machine.  When I attempt to mount the share, it says access is denied.  However, when I do, it says that that command is not found.  I have installed the nfs-common and portmap on the client and I believe that the /etc/exports is also set up properly.  

```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/media/data	192.168.2.1/24(rw,no_root_squash,async)
```

---

### Post by baddnady23 on 2010-03-26
I have also changed permissions to 777 for /media/data... but to no avail

---

### Post by terdon on 2010-03-26
Hi, 
   I realize this is really NOT the *nix way, but I got my nfs shares set up perfectly and very easily using webmin :[http://www.webmin.com/]("http://www.webmin.com/")

I spent ages trying to get verious network issues and exports sorted and webmin allowed me to fix all in minutes.

---

### Post by baddnady23 on 2010-03-26
hmmm...interesting but not real sure if its what I'm looking for... Thanks though!

---

### Post by baddnady23 on 2010-03-26
Ah got it.  Simple typo right here:

```
/media/data	192.168.[COLOR="Red"]2.1[/COLOR]/24(rw,no_root_squash,async)
```

should have been:

```
/media/data	192.168.[COLOR="Blue"]1.0[/COLOR]/24(rw,no_root_squash,async)
```

Just goes to show the need to double check ones own work :D

---

### Post by terdon on 2010-03-26
Too true... :)

---

