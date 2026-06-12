---
title: "Synology NAS NFS Mounting Issues"
date: 2016-01-04
forum: Networking &amp; Wireless
---

### Post by scambro on 2016-01-04
I just rebooted my server for the first time in a few months and my NAS isn't mounted.  I checked out my fstab entry and realized I had a typo.  I seem to recall last time it rebooted, manually mounting the NAS, so I must have forgotten to update the fstab entry after doing that.  But now, for the life of me, I cannot get the nas to mount properly.

NAS:
```

nas> showmount -e 
Export list for nas:
/volume1/media <serverIP>,192.168.1.0/24
nas> ls -all /volume1/media/
d---------   10 root             root          4096 Dec 10 15:28 .
drwxr-xr-x   10 root             root          4096 Jan  4 10:45 ..
-rwxrwx---    1 guest            users        12292 Jan  4 11:05 .DS_Store
drwxrwxrwx    3 root             users         4096 Jan  4 10:45 @eaDir
drwxrwxrwx  160 1001             1000         49152 Jan  4 10:22 movies
drwxrwxrwx   13 1001             65534         4096 Oct 21 13:28 music
drwxrwx---    2 frontEndUser     users         4096 Jul  6 14:13 volume_reports
-rwxrwx---    1 guest            users         1277 Jul 10 12:41 wrapper.pl
nas> nano /etc/exports

/volume1/media  192.168.1.0/24(rw,async,no_wdelay,crossmnt,insecure,all_squash,insecure_locks,sec=sys,anonuid=1024,anongid=100) <serverIP> (rw,async,no_wdelay,crossm$

```
(the <serverIP> and 192.168 entries are the same for now while I'm trying to figure this out).

lubuntu server:
```

user@server:/media/nas$ sudo mount -t nfs nas:/volume1/media /media/nas
user@server:/media/nas$ ls -all
total 8
drwxr-xr-x  2 root root 4096 Jul  1  2015 .
drwxr-xr-x 12 root root 4096 Jul  1  2015 ..
user@server:/media/nas$

```

I can browse the nas just fine from a mac on the network using the SMB service.  I'm particularly confused because I thought the way I had the NFS service setup right now on the nas is very open (that's my intent).  Thoughts on at least manually mounting the nas?  I'm not getting an error message, which makes me feel like it's working, but then nothing shows when I list the contents.

Thanks!

---

### Post by scambro on 2016-01-04
Found another guide online that suggested using the following options in fstab:  rw,hard,intr,nolock.  This seems to have made the share read/writable from the server.  But I'm not sure why.

---

