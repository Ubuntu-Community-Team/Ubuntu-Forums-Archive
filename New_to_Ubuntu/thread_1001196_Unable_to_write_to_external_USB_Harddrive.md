---
title: "Unable to write to external USB Harddrive"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by jseiser on 2008-12-03
I have been able to write to this drive from all my distros except this Fedora one.  I normally would launch the file manager as root, change the permissions on the drive to allow everyone read/write access.  Then everything worked fine.  When I launch nautilus as root, I can not change the permissions of the drive.

```

#
# /etc/fstab
# Created by anaconda on Thu Nov 27 15:16:34 2008
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
UUID=2d5728c1-80a7-4edc-ac15-51fc9c9f6111 /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0

```

```


[root@beast justin]# mount

/dev/mapper/VolGroup00-LogVol00 on / type ext3 (rw)
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdb1 on /boot type ext3 (rw)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
gvfs-fuse-daemon on /home/justin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=justin)
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

```

```

[root@beast justin]# blkid
/dev/sda1: UUID="C81886E81886D53A" TYPE="ntfs" 
/dev/sdb1: LABEL="/boot" UUID="2d5728c1-80a7-4edc-ac15-51fc9c9f6111" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb2: UUID="zdgdmc-W89n-4Tqx-HwdX-iBk3-z0gY-0zaBAQ" TYPE="lvm2pv" 
/dev/mapper/VolGroup00-LogVol00: UUID="1382b57b-8450-4184-931b-c27ad853a3f0" TYPE="ext3" 
/dev/mapper/VolGroup00-LogVol01: TYPE="swap" UUID="66245f4a-8099-4339-a0e3-981de00625f2" 
/dev/VolGroup00/LogVol00: UUID="1382b57b-8450-4184-931b-c27ad853a3f0" TYPE="ext3" 
/dev/VolGroup00/LogVol01: TYPE="swap" UUID="66245f4a-8099-4339-a0e3-981de00625f2" 
/dev/sdc1: UUID="196c625c-f949-4889-b1e1-fec7d9f5da22" TYPE="ext3" 

```

any ideas?

---

### Post by jbrown96 on 2008-12-04
You should be doing something like that from the command line. *Cringes at the thought of running a graphical app with root permissions*
A couple of commands that you may want to do: chown and chmod

Chown CHanges OWNership and chmod Changes MODification bits
If the owner has r/w/x access already, then just use chown. If not, then use chmod first, followed by chown.

```
sudo chown -R USERNAME:USERNAME /MOUNT/POINT
``` Change the username and mountpoint. If you are just mounting the drive with a desktop icon, then it will be mounted in the following order: /meida/disk, /media/disk-1, /media/disk-2, etc. Find out when is the one you need to change.

```
sudo chmod -R 777 /MOUNT/POINT
```

---

### Post by utnubuuser on 2008-12-04
yeah, or you can run nautilus as root

terminal >> gksu

---

