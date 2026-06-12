---
title: "Samba: can access one disk but not the other"
date: 2016-05-21
forum: Networking &amp; Wireless
---

### Post by Napseis on 2016-05-21
EDIT: typo....aaargh! Can someone delete this please?

hello,
I switched my server from Fedora to Ubuntu LTS, and i have a problem with samba.
I have two hard drives, i can access them ok, herethe fstab:

```
/dev/disk/by-uuid/9488e90e-ebe1-47c1-97c9-cf236d5ccaaf /mnt/Feydakin auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Feydakin 0 0
/dev/disk/by-uuid/fd702aca-4767-43c7-94f0-f4dfac14a5a9 /mnt/Sardaukar auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Sardaukar 0 0

```
I have several shares defined, all the one in Sardaukar are visible and accessible from windows. The ones from Feydakin are visible but not accessible, with error in the log: 
```
[2016/05/21 11:42:29.496004,  0] ../source3/smbd/service.c:800(make_connection_snum)
   canonicalize_connect_path failed for service Mist, path /mnt/Fedaykin/Mist

```


Here is an extract of the smb.conf. As you can see, exactly the same (and the share descrition parts has been copied from my old fedora, not the whole smb.conf).

```


[Mist]
        comment = Nuage de sauvegarde

        path = /mnt/Fedaykin/Mist
        read only = no
        browseable = yes
        valid users = napseis


[SystemGholas]
        comment = Images Diques des systemes
        path = /mnt/Fedaykin/SystemGholas
        read only = no
;       browseable = yes
        valid users = napseis


[Downloads]
        comment = downloads
        path = /mnt/Sardaukar/Downloads
        read only = no
;       browseable = yes
        valid users = napseis


[Temp]
        comment = Temp transfer fodler
        path = /mnt/Sardaukar/Temp
        read only = no
;       browseable = yes
        valid users = napseis

```



And finally the permissions:

in /mnt :
drwxrwx--x  9 napseis serverusers 4,0K mai   20 19:47 Feydakin
drwxrwx--x 13 napseis serverusers 4,0K mai   20 22:47 Sardaukar

in Feydakin:
drwxrwx--x  22 napseis serverusers 4,0K mars  19  2015 Mist
drwxr-x---.  5 napseis serverusers 4,0K mai   20 21:05 SystemGholas

in Sardaukar:
drwxrwxr-- 16 napseis serverusers  16K mai   19 20:01 Downloads
drwxrwx---  3 napseis serverusers 4,0K mai   21 00:09 Temp

I have absolutely no idea what is going wrong, as to me, everything is the same.

edit: finally [COLOR=#000000]fdisk -l is the only difference i see, but i didn't touch anything since Fedora :
[/COLOR]```

Disk /dev/sdc: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: BC3FEFC4-0565-4BDF-B200-4702AEE4CFD9
Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 3907028991 3907026944  1,8T Microsoft basic data


Disk /dev/sdb: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000a3c4c
Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1        2048 3907028991 3907026944  1,8T 83 Linux

```




Thanks!

---

