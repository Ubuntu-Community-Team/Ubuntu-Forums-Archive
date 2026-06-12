---
title: "NFS error"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by sDoky on 2008-05-20
Hi guys, I'm experiencing some errors with missing files (well not actually missing but just not visible). I've got a server (ubuntu 7.10 server edition) configued as a nfs samba and many other servers. From time to time if I try to open the directory (on my desktop) it shows there's no file or some files are missing. And remount fixes this. Does anyone know what to do?

my server's /etc/exports file
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/media/sda1	10.0.0.2(sync,no_subtree_check,no_root_squash,rw)
/media/sdb1	10.0.0.2(sync,no_subtree_check,no_root_squash,rw)
/home/ftp	10.0.0.2(sync,no_subtree_check,no_root_squash,rw)
/var/www	10.0.0.2(sync,no_subtree_check,no_root_squash,rw)
```

my desktop's /etc/fstab file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5da46b4e-4a03-4348-8e02-26720c5fdf26 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7C87-4E66  /media/XP       vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=7b301cec-c732-4f42-a155-6dbc4c96cf6c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
10.0.0.10:/media/sda1 	/media/sda1	nfs	rsize=8192,wsize=8192,timeo=14,intr
10.0.0.10:/media/sdb1	/media/sdb1	nfs	rsize=8192,wsize=8192,timeo=14,intr
10.0.0.10:/var/www	/media/www	nfs	rsize=8192,wsize=8192,timeo=14,intr
10.0.0.10:/home/ftp	/media/ftp	nfs	rsize=8192,wsize=8192,timeo=14,intr

```

Thanks for your help

---

### Post by nixscripter on 2008-05-21
The easiest thing I can think of is that the NFS server is timing out, and so it opens an empty directory. When you re-mount, it tries again, and works.

First, try extending the timeout with **timeo=60** or some larger value. Also, to speed up the response of the server, you may want to try async instead of sync in the server config, which will result in acknowledging when it has recieved the data, but before it has written it to disk.

---

### Post by nixscripter on 2008-05-21
The easiest thing I can think of is that the NFS server is timing out, and so it opens an empty directory. When you re-mount, it tries again, and works.

First, try extending the timeout with **timeo=60** or some larger value. Also, to speed up the response of the server, you may want to try **async** instead of **sync** in the server config, which will result in acknowledging when it has recieved the data, but before it has written it to disk.

---

### Post by sDoky on 2008-05-21
Thanks man, I've set these settings up. I'll try it. Thanks a lot
> **nixscripter said:**
> The easiest thing I can think of is that the NFS server is timing out, and so it opens an empty directory. When you re-mount, it tries again, and works.

First, try extending the timeout with **timeo=60** or some larger value. Also, to speed up the response of the server, you may want to try **async** instead of **sync** in the server config, which will result in acknowledging when it has recieved the data, but before it has written it to disk.

---

### Post by sDoky on 2008-05-22
Still doin' the damn thing again. Any other ideas?

Thanks

---

### Post by nixscripter on 2008-05-22
Is there a particular time it does this, like the first time you boot? What kinds of files does it do this for? How long does the remount fix it for?

I don't know about Samba, but I believe most implementation of NFS (including Linux's) use extensive host-side caching. If, for example, a file is created on the remote side, it might not appear locally for a while.

---

### Post by sDoky on 2008-05-24
Well I think it's random. And it sometimes hides just few files or directories. Like when I'm playing some playlist, suddenly it stops and says: 'the file does not exist!'. Any ideas? Does this happen to any of you guys?

Thanks

> **nixscripter said:**
> Is there a particular time it does this, like the first time you boot? What kinds of files does it do this for? How long does the remount fix it for?

I don't know about Samba, but I believe most implementation of NFS (including Linux's) use extensive host-side caching. If, for example, a file is created on the remote side, it might not appear locally for a while.
EDIT: It is not doing for samba, my brother is running WinXP and there are no problems with that connection over samba.

---

### Post by nixscripter on 2008-05-26
One more thing I can think of, which might be annoying: get rid of the **intr** flag in /etc/fstab.

This will make a wait for the server unkillable. Perhaps something is interrupting it when it is trying to open a file, making it abort early. Also, add **soft** to the same fstab file so as to avoid waiting forever. (If it still doesn't work, then you might try **hard** instead on a day when you don't have much to do.)

---

### Post by buntunub on 2008-06-26
I am also experiencing NFS issues now after the -19 kernel update to only my x64 machine. Checking cat /var/log/messages shows an NFS-kernel-server timeout, wait 90 seconds, etc. followed with a really nasty gvfs error:0 message. This issue causes some really NASTY side effects as well because if you try to access your still mounted NFS shares, it causes Nautilus to freeze, and then GDM cascades into total lockup. Resetting dbus helps a tad following this GDM cascaded failure. Resetting NFS-kernel-server does not. My portmap looks about the same as the OP's. Ive googled this, and it seems to be a persistent bug for all the more recent GNOME using distro's (IE. those using gvfs), so that makes me think that it has something to do with a combination of NFS and gvfs that just wont play nice with each other.

---

