---
title: "Ubuntu 16.04 - Unable to mount NFS shares"
date: 2018-01-11
forum: Networking &amp; Wireless
---

### Post by rodride on 2018-01-11
Hi all,

my exports file on NFS server : 

```

/home/filip/Documents/ 192.168.2.5(rw,sync,no_subtree_check)
/home/filip/Images/ 192.168.2.5(rw,sync,no_subtree_check)
/home/filip/Vidéos/ 192.168.2.5(rw,sync,no_subtree_check)
/media/filip/USB-LINUX-1.2To/ 192.168.2.5(rw,sync,no_subtree_check)
/media/filip/USB-DISK640/ 192.168.2.5(rw,sync,no_subtree_check)

```

my fstab file on NFS client ;
```

192.168.1.85:/home/filip/Documents /mnt/nfs_Documents  nfs  user,auto  0 0
192.168.1.85:/home/filip/Images /mnt/nfs_Images  nfs  user,auto  0 0
192.168.1.85:/home/filip/Vidéos /mnt/nfs_Vidéos  nfs  user,auto  0 0
192.168.1.85:/media/filip/USB-DISK640  /mnt/nfs_USB-DISK640  nfs  auto,user,nfsvers=3  0 0
192.168.1.85:/media/filip/USB-LINUX-1.2To  /mnt/nfs_USB-LINUX-1.2To  nfs  auto,user,nfsvers=3  0 0

```

I can mount Documents, Images and Videos shares but when i try with the USB shares, i have this message :
```

sudo mount -a
mount.nfs: access denied by server while mounting 192.168.1.85:/media/filip/USB-DISK640
mount.nfs: access denied by server while mounting 192.168.1.85:/media/filip/USB-LINUX-1.2To

```

Any ideas to fix that ?

---

### Post by TheFu on 2018-01-11
Are the USB file systems Linux?  I wouldn't expect NTFS or FAT-whatever to work.

---

### Post by rodride on 2018-01-11
USB-DISK640 is fat
USB-LINUX-1.2To is ext4

---

### Post by TheFu on 2018-01-12
Check the system logs.

Try manually mounting the ext4 storage somewhere else, not under /media/, update the NFS exports, restart the nfs-server daemon to force a config file re-read, and see how that works.

I don't think the FAT storage will ever be shared over NFS. [http://nfs.sourceforge.net/](http://nfs.sourceforge.net/) answer C4 says it might work, but will cause grief. Something to do with not having inodes.

[https://ubuntuforums.org/showthread.php?t=2106939](https://ubuntuforums.org/showthread.php?t=2106939) is sorta similar, but not.  It shows using verbose mount commands to get more data.

---

### Post by rodride on 2018-01-21
I simply modify shared usb drives permissions on the server and that's work so fine now.

I can mount my shares on the client.

---

