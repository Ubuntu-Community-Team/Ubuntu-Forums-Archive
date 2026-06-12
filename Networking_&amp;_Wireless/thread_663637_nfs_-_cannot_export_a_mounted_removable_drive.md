---
title: "nfs - cannot export a mounted removable drive"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by Vetto on 2008-01-10
I have an NFS server with an attached USB drive mounted as "/media/My Book"

I am trying to export this directory and when I refresh the exportfs (exportfs -ar)  I get the folowing:
```

vetto@adcap:~$ sudo exportfs -ra
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.100.0/24:/media/My Book".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x
exportfs: Warning: /media/My Book does not support NFS export.

```

Here is the details of the local mount:
```

/dev/sdb1 on /media/My Book type vfat rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower)

```

Here is the /etc/exports
```

"/media/My Book"   192.168.100.0/24(rw,no_root_squash,async)

```

Is the inability to export this directory related to the mount point, the filesystem (vfat), the fact that it is an automounted usb drive, or something else?

---

### Post by Vetto on 2008-01-11
Wait...

mounting the drive /dev/sda1 as /media/MyBook (without the space) and then exporting it as /media/MyBook worked fine.

Now I think that I can mount the nfs "/media/MyBook" as "/media/My Book" on the client will work fine...I will post results later.

---

### Post by Vetto on 2008-01-11
it worked... just gotta figure out the settings to get the best performance

---

