---
title: "Nautilus hangs after forgetting to unmount NFS"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by jamesshuang on 2007-02-04
I have a very irritating problem with NFS mounts. When I forget to unmount them before disconnecting from the network, Nautilus freezes. ls, cd, and umount all freeze when I'm trying to access the mounted nfs share, which means the computer is effectively locked until a reboot, or a reconnection with the network. Is there a way to make the NFS share just disconnect instead of locking the entire computer?

---

### Post by etienne.navarro on 2007-02-07
Perhaps using one of the options mentioned in the manpage of exports
```
man exports
```
Try using the **intr** option, which could solve the problem.

---

### Post by dmizer on 2008-02-25
i also have this problem.

my fstab line looks like this:
```
server.mydomain.com:/files /mountpoint nfs rsize=8192,wsize=8192,timeo=14,intr
```

as you can see, this DOES have the intr option.  i have not found any options which solve this.  this has been causing me difficulty since dapper.

---

### Post by dmizer on 2008-02-27
okay ... for a bump:

here's /etc/exports:
```
/files 192.168.1.0/24(rw,no_root_squash,async)
```

is there an fstab or exports variable i'm missing?

---

### Post by dave-5B on 2008-06-14
same problem on hardy, anyone have any ideas?

fyi fstab looks like dmizer's:
```

server:/some/dir /home/me/dir nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

```

Edit:
is this possibly a completely different problem since gnome changed to gvfs

---

