---
title: "how to mount NFS share directory from freeNAS at boot up"
date: 2020-01-30
forum: Networking &amp; Wireless
---

### Post by raymondvillain on 2020-01-30
Ubuntu 18.04
64 bit desktop machine
freeNAS successfully installed on old desktop box, NFS dataset created

I can mount the NFS dataset after boot, with this command (in a script file):

```
mount 192.168.1.174:/mnt/filebucket1/fenikan_warehouse /var/fenikan_warehouse
```

After mounting I can read and write to the NFS drive. 

I would like to somehow edit the fstab file and have this done sort of automatically at every startup, but cannot figure out how to do that.

If I edit fstab add a mount command on a separate lin nothing happens.

Any and all suggestions greatly appreciated.

---

### Post by guiverc on 2020-01-30
Try

```
192.168.1.174:/[COLOR=#000000][FONT=&amp]/mnt/filebucket1/fenikan_warehouse /var/fenikan_warehouse nfs rw,auto 0 2
```

All options in /your file-system-table (fstab) are separated by white-space (space/tabs) so options like the 'rw,auto' in my example are separated by comma, I use others too eg. I have ,rsize=8192,wsize=8192,timeo=14,intr,user..[/FONT][/COLOR]

---

### Post by TheFu on 2020-01-31
Best not to add rsize/wsize options. Let the NFS client and server negotiate the proper sizes.  Besides that, the fstab line seems ok.

I would point out that using /var/fenikan_warehouse might not be the best mount location. With snap packages, that storage cannot be accessed due to storage access constraints.  I mount storage outside "approved -by- snap" areas and have for 25 yrs.  If you don't have to use snaps, then it won't matter.  OTOH, following the **Linux File System Hierarchy Standards** does make sense, if possible.   [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) has a table.

---

