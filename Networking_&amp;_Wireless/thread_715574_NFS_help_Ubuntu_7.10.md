---
title: "NFS help Ubuntu 7.10"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by zuidema on 2008-03-05
I have tried several different approaches posted on the internet with no luck.
My network on both machines is DHCP.
At this point the Server side has nfs-common, nfs-kernel-server, and portmap installed. Below are the contents of /etc/exports and /etc/fstab

# /etc/exports: the access control list for filesystems which may be exported
# to NFS clients. See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4 gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes gss/krb5i(rw,sync)
#
/media/downloads/iso *(rw,sync,no_root_squash)


# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
#/dev/hda1
UUID=4bd7c18b-deb4-467c-9a3e-e3bce2c1e0a1 / ext3 defaults,errors=remount-ro 0 1
#/dev/sda1
UUID=6e88e2c2-8a17-4ff1-afcb-a05c9d2bec8c /home ext3 defaults 0 2
#/dev/sda2
UUID=524b7e71-fced-4d89-9ac5-1eb8713b0469 none swap sw 0 0

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/fd1 /media/floppy1 auto rw,user,noauto,exec 0 0

/media/download/iso 192.168.1.1/24(rw,no_root_squash,async)

On on the client side I have nfs-common and portmap installed and the line below in /etc/fstab

192.168.1.0/24:/media/download/iso /media/nfs/download/iso nfs rw,sync 0 0

Also made sure directory was exported with exportfs -av What else do I need to do?

---

### Post by Eiríkr on 2008-03-05
Well, we've got a description of your setup, but we are left with still no idea what your specific symptoms are.  What happens, exactly, when you try to mount the NFS share?  

Cheers,

Eiríkr

---

### Post by Loosewheel on 2008-03-05
Hi zuidema,
I would try to replace the host wild card, (*), in your exports file with the IP address of the machine you want to share the file with. I'm not sure,but I think you would need to include '.local.domain' with a wild card(*). Or '@SomeNetGroup'.
So it would look like: /media/downloads/iso 192.168.x.x(rw,sync,no_root_squash)

The fstab entry should have  <host>:<dir>, then the mount point, like /mnt/somefile. Mine looks like this: 
pcl3:/home/tech/Shared /home/tech/Shared3 nfs rsize=8192,wsize=8192,users 	0	0
This only needs to be on the client machine. And, I had to create 'Shared3' before trying to mount 'Shared'. (Probably not very graceful, but it works).

Take a look at the man pages for exports and fstab. (Type 'man exports' in a terminal).

Good luck.   Oh. You have to run 'exportfs -ra' in a terminal after changes to /etc/exports.

---

### Post by Eiríkr on 2008-03-05
Thanks to Loosewheel --

Refamiliarizing myself with /etc/exports file syntax, the man page notes:
> **wildcards**
Machine names may contain the wildcard characters _*_ and _?_.  This  can  be  used  to make the exports file more compact; for instance, _*.cs.foo.edu_ matches all hosts in the domain _cs.foo.edu_. However, **these wildcard characters do not match the dots  in a  domain name**, so the above pattern does not include hosts such as _a.b.cs.foo.edu_.

Likewise, I suspect the wildcard _*_ will not match the dots in an IP address either.  To serve up an NFS share to everyone, simply leave off any specification at all.  So that line in your exports file would look like this:
```
/media/downloads/iso (rw,sync,no_root_squash)
```

If this doesn't work, please let us know as specifically as you can what's happening.  

Cheers,

Eiríkr

---

### Post by zuidema on 2008-03-06
i have got it to work somewhat. Changed my network to static IP addresses then chose directory under /home/jgz/. I am able to mount manually but no luck with auto mount.

---

### Post by Eiríkr on 2008-03-06
I've read elsewhere that there are some issues with automounting SMB shares on boot due to the order in which things happen in Ubuntu during bootup.  Have a look at [post=2470296]this post[/post] and see if adding the indicated "sleep" and then "mount" lines in your /etc/rc.local file works for you (replacing "smbfs" with "nfs", naturally :)).

Cheers,

Eiríkr

---

