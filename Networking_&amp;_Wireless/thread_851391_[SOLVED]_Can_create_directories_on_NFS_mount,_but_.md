---
title: "[SOLVED] Can create directories on NFS mount, but not regular files"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by jazzgossen on 2008-07-06
I have a FAT32 partition exported via NFS. On the NFS server, all users can create files in the exported tree. But on the clients, users can create directories, but not regular files.

Here are the contents of the config files on the server:
/etc/exports:
```
/mnt/shared [client_address](rw,no_subtree_check)
```

/etc/hosts.deny:
```
portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL
```

/etc/hosts.allow:
```
portmap: [client_address]
rquotad: [client_address]
mountd: [client_address]
statd: [client_address]
```

I mounted the share on a client with the following command:
```
sudo mount [server_address]:/mnt/shared /mnt/gemensamt/ -o rw,hard,intr
```

All files on the shared volume are owned by root and have rwxrwxrwx access. The volume is mounted on the server like this:
```
/dev/hda9       /mnt/shared     vfat    defaults,umask=0000   0       2
```


What am I doing wrong?

---

### Post by jazzgossen on 2008-07-09
It must be that NFS doesn't play nicely with FAT32. I don't have these kinds of problems with an EXT3 mount.

Now, if I could only have an EXT3 mount with write permissions for all users in all directories...

---

