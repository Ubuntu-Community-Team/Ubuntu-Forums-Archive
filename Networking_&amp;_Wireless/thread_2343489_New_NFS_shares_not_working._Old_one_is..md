---
title: "New NFS shares not working. Old one is."
date: 2016-11-16
forum: Networking &amp; Wireless
---

### Post by HittingSmoke on 2016-11-16
I have my NAS shared with my servers that need mount point using NFS. I had one set up previously for the network. I'm trying to set up more fine-grained control. I've set up a new share with the exact same config as the first (working) share but I can't get the client to connect. I get No such file or directory error from the client when trying to connect.

My NAS is running Server 16.04. The client is running OpenFLIXR, a pre-prepared image that uses 16.04 as well.

This is my export folder:
```

    /srv/nfs4$ ls -lh
    total 4.0K
    drwxrwxrwx+ 1 root  root     0 Nov 16 07:53 comics
    lrwxrwxrwx  1 root  root    17 Nov 16 08:32 comics2 -> /mnt/store/comics
    lrwxrwxrwx  1 root  root    11 Oct 23 14:22 nextcloud -> /mnt/store/
    drwxrwxrwx  3 root  root  4.0K Nov 15 23:58 openflixr
```

Nextcloud is a symlink directly to my storage pool. Ignore the "nextcloud" name. I changed it to the root of my storage pool but never got around to changing the export name. What I don't know is why I set this up as a symlink instead of a bind mount. I thought it was a bind mount until I got in trying to troubleshoot my new share.

comics is a bind mount to /mnt/store/comics. comics2 is a symlink to the same directory I used to make sure the bind mount wasn't the issue.

When I try to connect to the symlink share: 

```
    sudo mount -v 10.0.10.3:/srv/nfs4/comics2 /mnt/comics
    mount.nfs: timeout set for Wed Nov 16 08:34:48 2016
    mount.nfs: trying text-based options 'vers=4,addr=10.0.10.3,clientaddr=10.0.200.59'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=10.0.10.3'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 10.0.10.3 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 10.0.10.3 prog 100005 vers 3 prot UDP port 59583
    mount.nfs: mount(2): No such file or directory
    mount.nfs: mounting 10.0.10.3:/srv/nfs4/comics2 failed, reason given by server: No such file or directory
```

When I try to connect to the bind mount share:
```

    sudo mount -v 10.0.10.3:/srv/nfs4/comics /mnt/comics
    mount.nfs: timeout set for Wed Nov 16 09:25:36 2016
    mount.nfs: trying text-based options 'vers=4,addr=10.0.10.3,clientaddr=10.0.200.59'
```

This just hangs here until I kill it.

I initially thought it was the client because this is a custom KVM image however I can still mount my root share (nextcloud) just fine from the same client:

```
    sudo mount -v 10.0.10.3:/srv/nfs4/nextcloud /mnt/comics
    mount.nfs: timeout set for Wed Nov 16 09:27:15 2016
    mount.nfs: trying text-based options 'vers=4,addr=10.0.10.3,clientaddr=10.0.200.59'
    mount.nfs: mount(2): No such file or directory
    mount.nfs: trying text-based options 'addr=10.0.10.3'
    mount.nfs: prog 100003, trying vers=3, prot=6
    mount.nfs: trying 10.0.10.3 prog 100003 vers 3 prot TCP port 2049
    mount.nfs: prog 100005, trying vers=3, prot=17
    mount.nfs: trying 10.0.10.3 prog 100005 vers 3 prot UDP port 40289
```

In case it's not obvious, these are not different subnets. This is /16.

This is what my exports currently looks like:
```

    /srv/nfs4/nextcloud 10.0.11.2(rw,nohide,no_root_squash,mp=/mnt/store) 10.0.200.59(rw,nohide,no_root_squash,mp=/mnt/store)
    /srv/nfs4/comics2 10.0.200.59(rw,nohide,no_root_squash,mp=/mnt/store/comics)
    /srv/nfs4/comics 10.0.200.59(rw,nohide,no_root_squash,mp=/mnt/store/comics)
```

The client reports the exports correctly:

```
    showmount -e 10.0.10.3
    Export list for 10.0.10.3:
    /srv/nfs4/comics  10.0.200.59
    /mnt/store/comics 10.0.200.59
    /mnt/store        10.0.200.59,10.0.11.2
```

I need to fix my root NAS mount to use a bind mount but I don't want to touch that until I figure out what's wrong with the comics mount.

Logs don't show anything at all related to NFS except the usual stuff on the server-side: 

```
    [8805340.841225] nfsd: last server has exited, flushing export cache
    [8805340.899321] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
    [8805340.899349] NFSD: starting 90-second grace period (net ffffffff81ef3e80)
    [8807141.024241] nfsd: last server has exited, flushing export cache
    [8807141.105738] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
    [8807141.105768] NFSD: starting 90-second grace period (net ffffffff81ef3e80)
```

Any ideas what to check next?

---

### Post by SeijiSensei on 2016-11-16
Just to make sure, 10.0.200.59 is the client?

I've never seen the "mp" option to NFS before.  I've read its description in "man exports" and don't really have a good sense when it would be needed.  Can you mount the share without that option in place?

---

### Post by HittingSmoke on 2016-11-17
> **SeijiSensei said:**
> Just to make sure, 10.0.200.59 is the client?

I've never seen the "mp" option to NFS before.  I've read its description in "man exports" and don't really have a good sense when it would be needed.  Can you mount the share without that option in place?

Yes. 10.0.0.0/16 is my CIDR. 10.0.200.0/24 is my DHCP range.

mp is the "mount point" option. From the export docs:

> mountpoint=path
mp
This option makes it possible to only export a directory if it has successfully been mounted. If no path is given (e.g. mountpoint or mp) then the export point must also be a mount point. If it isn't then the export point is not exported. This allows you to be sure that the directory underneath a mountpoint will never be exported by accident if, for example, the filesystem failed to mount due to a disc error.

If a path is given (e.g. mountpoint=/path or mp=/path) then the nominated path must be a mountpoint for the exportpoint to be exported.

I'll try it without mp when I get back to my desk, but it shouldn't be causing any issues.

---

### Post by HittingSmoke on 2016-11-17
> **SeijiSensei said:**
> Just to make sure, 10.0.200.59 is the client?

I've never seen the "mp" option to NFS before.  I've read its description in "man exports" and don't really have a good sense when it would be needed.  Can you mount the share without that option in place?

Nope. Removing the mountpoint option doesn't help.

---

