---
title: "[SOLVED] mounting /home over NFS (feisty)"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by PointSource on 2007-07-14
Hi all,

I am having lots of trouble mounting a NFS /home share to a kubuntu 7.04 computer. I type in a username and password, and the computer appears to log in, but it hangs right after it changes the mouse cursor from black to white. The really interesting thing is that I have set another computer up the same way, only running edgy instead of feisty, and it works.

UIDs are the same on server/client
nfs share is set up in /etc/fstab
nfs-common is installed on client

If anyone has any ideas, or something I've forgotten to do, please let me know.
TIA

---

### Post by Mr. C. on 2007-07-14
One would presume that your NFS mount has failed, and that your home directory is unavailable.

What does /var/log/messages show?  Any errors?

Get the NFS mount working elsewhere (eg. no /home) before you mount it in /home.  This way, you can log in an d work out the problems with your mount.

Without actual data, all we can do is speculate.

MrC

---

### Post by PointSource on 2007-07-14
/var/log/syslog
/var/log/messages

Another note, after I log in as a user whose home is outside /home, /home is browseable.

---

### Post by Mr. C. on 2007-07-14
I see nothing problematic in your logs.  Can you show the following from the NFS client:

```
cat /etc/fstab
mount
nfsstat
```

and from the NFS server:
```
cat /etc/exports
nfsstat
```

MrC

---

### Post by PointSource on 2007-07-15
Server:
/etc/exports:
```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).

/home 192.168.183.1(rw,no_root_squash,sync)
/home 192.168.183.2(rw,no_root_squash,sync)
/home 192.168.183.3(rw,no_root_squash,sync)
/home 192.168.183.4(rw,no_root_squash,sync)
/home 192.168.183.5(rw,no_root_squash,sync)
/home 192.168.183.6(rw,no_root_squash,sync)
/home 192.168.183.7(rw,no_root_squash,sync)
/home 192.168.183.8(rw,no_root_squash,sync)
/home 192.168.183.9(rw,no_root_squash,sync)
/home 192.168.183.10(rw,no_root_squash,sync)
/home 192.168.183.11(rw,no_root_squash,sync)
/home 192.168.183.12(rw,no_root_squash,sync)

/usr/share/wallpapers 192.168.183.1(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.2(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.3(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.4(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.5(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.6(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.7(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.8(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.9(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.10(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.11(rw,no_root_squash,sync)
/usr/share/wallpapers 192.168.183.12(rw,no_root_squash,sync)
```

nfsstat:
```
Warning: No Client Stats (/proc/net/rpc/nfs: No such file or directory).
```

Client:
nfsstat:
```

Client rpc stats:
calls      retrans    authrefrsh
110        0          0

Client nfs v2:
null         getattr      setattr      root         lookup       readlink
0         0% 11       10% 0         0% 0         0% 13       11% 1         0%
read         wrcache      write        create       remove       rename
80       73% 0         0% 0         0% 0         0% 0         0% 0         0%
link         symlink      mkdir        rmdir        readdir      fsstat
0         0% 0         0% 0         0% 0         0% 0         0% 4         3%

Client nfs v4:
null         read         write        commit       open         open_conf
0         0% 0         0% 0         0% 0         0% 0         0% 0         0%
open_noat    open_dgrd    close        setattr      fsinfo       renew
0         0% 0         0% 0         0% 0         0% 0         0% 0         0%
setclntid    confirm      lock         lockt        locku        access
0         0% 0         0% 0         0% 0         0% 0         0% 0         0%
getattr      lookup       lookup_root  remove       rename       link
0         0% 0         0% 0         0% 0         0% 0         0% 0         0%
symlink      create       pathconf     statfs       readlink     readdir
0         0% 0         0% 0         0% 0         0% 0         0% 0         0%
server_caps  delegreturn
0         0% 0         0%
```

mount:
```

/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
192.168.183.2:/home on /home type nfs (rw,_netdev,rsize=32768,wsize=32768,soft,intr,addr=192.168.183.2)
192.168.183.2:/usr/share/wallpapers on /usr/share/wallpapers type nfs (rw,_netdev,rsize=32768,wsize=32768,soft,intr,addr=192.168.183.2)
/dev/hdc on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=nonet)
/dev/sda1 on /media/disk type vfat (rw,noexec,nosuid,nodev,noatime,uid=1009,utf8,shortname=lower)
/dev/sda2 on /media/disk-1 type vfat (rw,noexec,nosuid,nodev,noatime,uid=1009,utf8,shortname=lower)
```

/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4368e2f7-ec4b-4326-ae82-8e45ef004db7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3A4F-4280  /media/hda1     vfat    defaults,noauto,utf8,umask=007,gid=46 0       0
# /dev/hda10
UUID=b87ac459-d08a-4c0d-b983-e28e2727c5a9 /media/hda10    ext3    defaults,noauto        0       0
# /dev/hda12
UUID=f0b22414-b3a0-44e4-8f27-69705b0e776c /media/hda12    ext3    defaults,noauto        0       0
# /dev/hda5
UUID=613ac873-2f06-44df-88f8-7ca2c2f37fae /media/hda5     ext3    defaults,noauto        0       0
# /dev/hda6
UUID=00b9c72b-5033-44c5-a8dc-9bb18b9d0525 /media/hda6     ext3    defaults,noauto        0       0
# /dev/hda7
UUID=0eaaf38a-dfca-4a48-90db-bd2574100aa5 /media/hda7     ext3    defaults,noauto        0       0
# /dev/hda8
UUID=ed2e0082-0bb3-4873-8314-ef8f5fe50c69 /media/hda8     ext3    defaults,noauto        0       0
# /dev/hda9
UUID=c47d9d2d-667e-4136-9216-45b4eecc55c4 /media/hda9     ext3    defaults,noauto        0       0
# /dev/hda11
UUID=ec8b040a-7c26-4ce4-ab75-b70a86d31c37 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

192.168.183.2:/home /home nfs _netdev,rsize=32768,wsize=32768,rw,soft,intr 0   0
192.168.183.2:/usr/share/wallpapers /usr/share/wallpapers nfs _netdev,rsize=32768,wsize=32768,rw,soft,intr 0   0
```

---

### Post by Mr. C. on 2007-07-15
The only thing that I'm curious about in the output is why your NFS client is using NFS v2 vs. v3.  Can you check the version of NFS in use on the systems where things work correctly?

I don't know what the state of NFS v2 is in recent Linux kernels - it used to be that an 8k buffer size was all that was supported.  A standard debugging practice is to reduce the buffer size until you find a stable configuration.

Also see if you can force NFS v3, by setting the nfsd server options (see man nfsd and /etc/init.d/nfs*).

I don't see any RPC timeouts or retransmissions, so there seems to be no issue with the protocol.

MrC

---

### Post by PointSource on 2007-07-16
Fixed! I was using the package "nfs-user-server" on the server instead of "nfs-kernel-server", which I just installed. Now everything "Just Works".

Thank you for your help, Mr C. If you hadn't prompted me to check the versions I was running I would not have thought of upgrading/sidegrading.

This upgrade might also fix the problem I have with open office and file locking.

PointSource

---

### Post by Mr. C. on 2007-07-16
Excellent!

That explains the V2 protocol, which is ancient.

Often it is a series of minor clues and playing hunches that pays greater dividends than years of knowledge!

Nice work,
MrC

---

