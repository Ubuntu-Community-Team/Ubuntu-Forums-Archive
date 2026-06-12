---
title: "mount freenas"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by farscape on 2007-03-14
I want a file server that I can access with WIndows and Ubuntu. Well I can acces the freenas with windows after I set up CIF(Samba) on freenas. I enabled NFS in freenas so I could access the shares with Ubuntu but I'm not sure how to mount it from Ubuntu. Is anyone else doing this? Help.

---

### Post by pvalois on 2007-03-14
the usual way to mount an nfs export is to run the command

mount -t nfs <server_name>:<export_name> <mount_point>

where in your case,

server_name = freenas 
export_name = ???   ---> check your /etc/exports
mount_point = the directory where you want the nfs to be mounted

be careful, in nfs, the security is low, and the right are posix standard one. 
so the uid has to be the same on the server and on the client to be identified as the owner of a file.

you can also configure your ubuntu client to automatically mount the samba share configure /etc/fstab (follow the man pal)

---

### Post by farscape on 2007-03-15
> **pvalois said:**
> the usual way to mount an nfs export is to run the command

mount -t nfs <server_name>:<export_name> <mount_point>

where in your case,

server_name = freenas 
export_name = ???   ---> check your /etc/exports
mount_point = the directory where you want the nfs to be mounted

be careful, in nfs, the security is low, and the right are posix standard one. 
so the uid has to be the same on the server and on the client to be identified as the owner of a file.

you can also configure your ubuntu client to automatically mount the samba share configure /etc/fstab (follow the man pal)

Thanks, I'll give it a shot.

---

### Post by rkillcrazy on 2007-12-09
I'm messing around with this and can't get it working.  I could just create a launcher on the desktop and map it to my FreeNas box but what's the fun in that!?

I tried following the posts but couldn't find /etc/exports.

I've made changes to the fstab file before so i tried hacking away at that but to no avail.  I figured I'd just add the following line in there:

```

//freenas     /media/freenas     cifs     0     0

```

Any help would be appreciated.

12-09-07
0836 EST

---

