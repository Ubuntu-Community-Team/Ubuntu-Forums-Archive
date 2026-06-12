---
title: "Samba connections not closing"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by legatek on 2007-08-02
I have just been informed by my Sysadmin that I have over twenty open connections to our Samba server at work! I mount the Samba shares during boot with fstab. It seems that when I shut down the connections are not closed and the next time I boot up another connection is established, resulting in the server getting clogged with many useless open connections. I need to solve this problem as it affects other users as well. Let me know what other information/logs you need and I'll happily post them. Thanks for any help in this matter.

---

### Post by legatek on 2007-08-02
As an update, I have applied max.durden's fix from the following thread

[http://ubuntuforums.org/showthread.php?t=293513/]("http://ubuntuforums.org/showthread.php?t=293513/") and am now waiting to hear if this has fixed the problem.

*edit: it probably won't since the shares are mounted with smbfs, not cifs

---

### Post by legatek on 2007-08-06
It seems the problem is still occurring. This morning I have more than or equal to 14 open connections to each of the Samba servers I must access. I have unmounted them using umount -f and could manually mount them and unmount them whenever I need them but I would really like to solve this problem so they can always remain mounted. Here is my fstab:

```
proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=703ad9f3-8d37-4cae-9145-f20c42c7c373 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=40B88046B8803D02 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=ACC8E72FC8E6F70C /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=70FC-D7A1 /media/sda3 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda5 :
UUID=69248f5f-dc0a-4f03-b53b-b51fd3027800 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/data ntfs-3g defaults,locale=en_US.UTF-8 0 0
\\PCMM45\User	/media/PCMM45	cifs	credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
\\PCMM45\Pool	/media/Pool	cifs	credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
\\Samba\pool-dnaseq	/media/DNA-server	cifs	credentials=/root/.smbcredentials-remote,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
\\sandy02-pool\pool-faessler	/media/Sally-server	smbfs	credentials=/root/.smbcredentials-remote,iocharset=utf8,dmask=777,fmask=777 0 0
\\samba-home-legate\legate	/media/Samba-server	smbfs	credentials=/root/.smbcredentials-remote,iocharset=utf8,dmask=777,fmask=777 0 0
```

Both PCMM45 entries and the last three Samba servers mount multiple times.
Here is the output from "cat /proc/mounts":

```
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/703ad9f3-8d37-4cae-9145-f20c42c7c373 / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/703ad9f3-8d37-4cae-9145-f20c42c7c373 /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/disk/by-uuid/40B88046B8803D02 /media/sda1 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/disk/by-uuid/ACC8E72FC8E6F70C /media/sda2 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/disk/by-uuid/70FC-D7A1 /media/sda3 vfat rw,gid=46,fmask=0007,dmask=0007,codepage=cp437,iocharset=iso8859-1,utf8 0 0
/dev/sda1 /media/windows fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/sda2 /media/data fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
```

Somehow this doesn't look right but I don't know how to fix it. Any ideas would be appreciated.

---

