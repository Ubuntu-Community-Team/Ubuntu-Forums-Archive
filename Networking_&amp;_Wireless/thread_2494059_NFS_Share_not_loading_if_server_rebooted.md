---
title: "NFS Share not loading if server rebooted"
date: 2024-01-04
forum: Networking &amp; Wireless
---

### Post by erlendoye on 2024-01-04
I've been using Ubuntu for a few months now having switched from Windows and by and large I'm enjoying the switch although I'm having a few niggles.

One issue I'm having is NFS shares. On Windows with samba I rarely had any issues on accessing my folders on my Raspberry Pi server but with Ubuntu this is less reliable. For example if I reboot the server my Ubuntu laptop can no longer connect to the NFS share (or have to wait a long time for it to restablish) and I have to reboot my laptop for to connect to it again. This problem is proabably due to a mistake I may have made with the fstab entry. I've pasted both my Ubuntu laptop fstab and the raspberry server experts file below:

Ubuntu laptop:
```
192.168.0.8:/mnt/media/ /mnt/nfs_clientshare nfs auto 0 0
```

Raspberry server:
```
[COLOR=#000000][FONT=Calibri]/mnt/media/Videos/Camera *(rw,insecure,no_subtree_check)[/FONT][/COLOR]
```

Any suggestions appreciated!

---

### Post by TheFu on 2024-01-04
**Update: **
What does the export look like?  Ah ... I see it now. Would have bit me if it wasn't any clearer.
```
/mnt/media/Videos/Camera *(rw,insecure,no_subtree_check)
```

BTW, I hope that's a typo in the fstab line posted above. It won't work at all as posted.

Ok, so on the Pi, the storage needs to be mounted without using an automatic, GUI-based, mount.  Basically, the real storage needs to be mounted using either the fstab or autofs.  

Personally, I'd never use a Pi as an NFS server, for a number of reasons (USB storage isn't the same as SATA/eSATA/SAS/SCSI. The USB storage command set is barely enough to transfer bits.

I'd never allow any storage to be mounted through gio/gvfs either.  This method of mounting i.e. putting mounts under /media/ and hoping the OS mounts them can have a number of silent failures.

Moving on to the NFS client .... 
For NFS or other sometimes-there mounts like USB storage, I avoid using the fstab and use autofs.  This way, the storage is only mounted to the client when actually in use.  There are lots of good reasons for this.

My config settings are like this on the server:
/etc/fstab:
```
/dev/istar-vg2/lv_media2           /d/D2   ext4 noatime,nodev,nosuid 0   1
```
/etc/exports:
```
/d/D2           hadar(rw,async,root_squash,no_subtree_check,fsid=1)
```
fsid is usually not needed, but when there are lots of NFS exports and clients, sometimes it is needed to prevent confusion.

On the client, I use autofs, the mounts all look like this:
/etc/auto.nfs
```
/d/D2 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D2
```

And once mounted, 
```
$ df -Th /d/D2
Filesystem                               Type  Size  Used Avail Use% Mounted on
istar:/d/D2                              nfs4  3.6T  3.6T   45G  99% /d/D2
```

Note how I mount to the same locations on the NFS server and clients?  I'm getting old and want to avoid being confused.  I mount /d/D2 and 6 other storage areas to a number of clients, so I don't want to worry that storage is mounted in different places on different systems.

On my Pi2/3/4 systems, they are each NFS clients and use autofs just like the others (i.e. hadar).

Also note that I don't mount storage under /media/ or under /mnt/ .   Those locations have specific purposes in the standards. You can look it up.  Having multiple tools trying to manage mounts in a single directory has always been a problem. Avoid those problems by not doing it.

---

### Post by SeijiSensei on 2024-01-04
Replace the word "auto" with "defaults" then run "sudo mount -t nfs -a". Is it now mounted?

---

### Post by erlendoye on 2024-01-06
Thanks - I will investigate autofs instead of fstab. What do you mean by "The USB storage command set is barely enough to transfer bits"? I have two external HDs plugged into the PI5 USB3 ports.


> **TheFu said:**
> **Update: **
What does the export look like?  Ah ... I see it now. Would have bit me if it wasn't any clearer.
```
/mnt/media/Videos/Camera *(rw,insecure,no_subtree_check)
```

BTW, I hope that's a typo in the fstab line posted above. It won't work at all as posted.

Ok, so on the Pi, the storage needs to be mounted without using an automatic, GUI-based, mount.  Basically, the real storage needs to be mounted using either the fstab or autofs.  

Personally, I'd never use a Pi as an NFS server, for a number of reasons (USB storage isn't the same as SATA/eSATA/SAS/SCSI. The USB storage command set is barely enough to transfer bits.

I'd never allow any storage to be mounted through gio/gvfs either.  This method of mounting i.e. putting mounts under /media/ and hoping the OS mounts them can have a number of silent failures.

Moving on to the NFS client .... 
For NFS or other sometimes-there mounts like USB storage, I avoid using the fstab and use autofs.  This way, the storage is only mounted to the client when actually in use.  There are lots of good reasons for this.

My config settings are like this on the server:
/etc/fstab:
```
/dev/istar-vg2/lv_media2           /d/D2   ext4 noatime,nodev,nosuid 0   1
```
/etc/exports:
```
/d/D2           hadar(rw,async,root_squash,no_subtree_check,fsid=1)
```
fsid is usually not needed, but when there are lots of NFS exports and clients, sometimes it is needed to prevent confusion.

On the client, I use autofs, the mounts all look like this:
/etc/auto.nfs
```
/d/D2 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D2
```

And once mounted, 
```
$ df -Th /d/D2
Filesystem                               Type  Size  Used Avail Use% Mounted on
istar:/d/D2                              nfs4  3.6T  3.6T   45G  99% /d/D2
```

Note how I mount to the same locations on the NFS server and clients?  I'm getting old and want to avoid being confused.  I mount /d/D2 and 6 other storage areas to a number of clients, so I don't want to worry that storage is mounted in different places on different systems.

On my Pi2/3/4 systems, they are each NFS clients and use autofs just like the others (i.e. hadar).

Also note that I don't mount storage under /media/ or under /mnt/ .   Those locations have specific purposes in the standards. You can look it up.  Having multiple tools trying to manage mounts in a single directory has always been a problem. Avoid those problems by not doing it.

---

### Post by erlendoye on 2024-01-06
Thanks. So I changed the auto to defaults and your command mounts the drive. Do you think this change in fstab wording will mean the mount is more reliable (eg when the server reboots etc)? What does changing auto to defaults actually do? Your help is appreciated. Thanks both!

> **SeijiSensei said:**
> Replace the word "auto" with "defaults" then run "sudo mount -t nfs -a". Is it now mounted?

---

### Post by SeijiSensei on 2024-01-06
[https://linux.die.net/man/5/nfs](https://linux.die.net/man/5/nfs) lists the array of options for NFS, of which auto is just one. Using defaults includes a range of standard options like rw access. Auto is one of the defaults.

The best way to know if the shares come back is to reboot. Running "sudo mount -t nfs -a" tells the mount command to look in /etc/fstab for all (-a) NFS mounts defined there. So it implies that the mount will survive a reboot.

Also the server can set options and override the settings in /etc/fstab.

---

