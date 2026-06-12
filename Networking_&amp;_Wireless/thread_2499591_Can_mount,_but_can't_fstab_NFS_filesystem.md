---
title: "Can mount, but can't fstab NFS filesystem"
date: 2024-08-01
forum: Networking &amp; Wireless
---

### Post by IRQsRFun on 2024-08-01
I am currently running Ubuntu 24.04 and I was able to setup a NFS share.  

I am able to mount this setup using the mount command, but I am unable to setup /etc/fstab such that the file system mounts.
I have already added the appropriate address in /etc/lhosts for the NAS address I am trying to attach to.

I am a trying to learn how to troubleshoot things like this.

Does anyone know in which script for /etc/fstab is processed?  My thought would be to add reporting (logging)  statements in this script that I can use to help me determine what is going on.  I am already looking at the log files and I am having difficulty finding the issue.  Also, please tell me the best way to print to the log files.

If I bork the script, I can still boot from a different version of linux and fix it.

If there is a better process for debugging this, please let me know.

---

### Post by TheFu on 2024-08-02
/etc/lhosts is the wrong file, if you are trying to make local hosts files used for lookups.
You say you can mount NFS. What is the working mount command?
You say your attempts to get that mount into your fstab isn't working.  What does your fstab file contain?
This stuff has been stable for 30 yrs, so it is unlikely NOT to work and follow normal settings.

Around 2016, systemd.mount started handling mount stuff.  There are multiple ways to address it.  The fstab is the easiest, assuming you know the format.  You can also use a systemd-Unit file. Yuck!   Or you can use **autofs**, which is how I mount all non-SATA, non-SCSI, non-Infiniband storage, but if you are certain your NFS server will always be there (I'm not), then using the fstab is fairly common.

---

### Post by Tadaen_Sylvermane on 2024-08-02
```
192.168.1.2:/path/to/share /local/mountpoint nfs defaults,noauto,x-systemd.automount,x-systemd.idle-timeout=30 0 0
```

This will mount it on demand when you enter or poll anything in the mountpoint. It will auto umount after 30 seconds assuming no activity.

If I had to guess it's not mounting because it's trying to mount before the network is up. There is a ```
netdev
``` flag for the fstab options but this is just a guess.

---

### Post by TheFu on 2024-08-03
x-systemd.automount doesn't work the same as **autofs**.  Just sayin'.
When I learned about sustemd.automount, I tested it and found some undesirable aspects, at least for my needs.

---

### Post by TheFu on 2024-08-05
Please don't use "soft" NFS mounts unless they are read-only.
Also, I don't see the "bg" option in the mount.nfs manpage. Is that valid?

poko21, would be helpful if you actually showed a systemd-mount 
Unit file, if that is what you are proposing.  I've never seen those used in the wild.
Also, what is "<your_fstab_entry>" - that can be confusing.

The **showmount -e {ip-of-NFS-server}** command will show which mounts the client can access.  But since the OP already said a manual mount command worked, it wasn't useful for THIS thread.

My auto.nfs from a client has entries like this:
```
 -fstype=nfs,nconnect=4,proto=tcp,rw,async  istar:/d/D1
```
istar is in my DNS, so I don't need to use the IP address, but that would be fine too.
The resulting mount looks like this:
```
$ dft /d/D1
Filesystem     Type  Size  Used Avail Use% Mounted on
istar:/d/D1    nfs4  3.5T  3.5T  2.5G 100% /d/D1
```

Another view of the mount results:
```
$ mount |grep /d/D1
/etc/auto.nfs on /d/D1 type autofs (rw,relatime,fd=6,pgrp=1486,timeout=300,minproto=5,maxproto=5,direct,pipe_ino=24915)
istar:/d/D1 on /d/D1 type nfs4 (rw,relatime,**vers=4.2,rsize=1048576,wsize=1048576**,namlen=255,hard,proto=tcp,nconnect=4,timeo=600,retrans=2,sec=sys,clientaddr=172.22.22.5,local_lock=none,addr=172.22.22.20)
```

Converting the autofs entry into an fstab line would look like this:
```
istar:/d/D1    /d/D1   nfs    nconnect=4,proto=tcp,rw,async   0   0  
```
I don't actually need "proto=tcp,rw" options. Those are defaults these days.  the others aid with performance for my specific NFS server, storage, and network.  You can also see from the **df** and **mount** output that nfs v4.2 and a hard mount, rsize, wsise, without file locking is negotiated automatically.  I'm not using NFS v4 w/ Kerberos tickets.  That would be more secure, but it is more hassle to setup.  In a business where clients and servers aren't on the same small, server-only, subnet, I'd demand Kerberos be used.

---

