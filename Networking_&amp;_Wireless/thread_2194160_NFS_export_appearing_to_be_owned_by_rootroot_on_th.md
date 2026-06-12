---
title: "NFS export appearing to be owned by root:root on the client"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by kripz on 2013-12-16
On the client i have the same username and same uid/gid but when it mounts, the child directories of the top directory appear to be owned by root:root (0:0) when on the server it's owned by user:user (1000:1000).

The permissions seem whack as well...

Client fstab:
```
192.168.1.13:/storage/public	/storage	nfs	_netdev,vers=3,defaults,user,auto,noatime,intr   0 0
```
ls -la
```
drwxr-xr-x  7 user user    7 Dec 16 22:58 .
drwxr-xr-x 23 root     root     4096 Dec 16 22:17 ..
drwxr-xr-x  2 root     root        2 Dec 16 20:20 Anime
drwxr-xr-x  2 root     root        2 Dec 16 20:20 Downloads
drwxr-xr-x  2 root     root        2 Dec 16 20:20 Files
drwxr-xr-x  2 root     root        2 Dec 16 20:20 HD Movies
drwxr-xr-x  2 root     root        2 Dec 16 20:20 Random

```
Server:
```
/storage/public 192.168.1.0/255.255.255.0(rw,sync,no_subtree_check,root_squash)
```
ls -la
```
drwxr-xr-x  7 user user  7 Dec 16 22:58 .
drwxr-xr-x  4 user user  4 Dec 16 20:20 ..
drwxr-xr-x  2 user user  2 Dec 16 20:20 Anime
drwxrwxrwx 17 user user 36 Dec 16 22:40 Downloads
drwxrwxrwx  2 user user  2 Dec 16 20:20 Files
drwxr-xr-x  2 user user  2 Dec 16 20:20 HD Movies
drwxrwxrwx  2 user user  2 Dec 16 20:20 Random

```
Ubuntu server 13.10 and Ubuntu 13.10 desktop.

---

### Post by papibe on 2013-12-16
Hi kripz.

Could you post the results of these commands on the server?
```
cat /etc/idmapd.conf

id user

ls -n /storage/public
```
Please replace 'user' with the actual username ('user' in your current examples).

and also these ones on the client?
```
cat /etc/idmapd.conf

id user

ls -n /storage
```
Regards.

---

### Post by kripz on 2013-12-16
server
```
id user
uid=1000(user) gid=1000(user) groups=1000(user),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),111(lpadmin),112(sambashare),1001(public)

ls  -n /storage/public/
total 24
drwxr-xr-x  2 1000 1000  2 Dec 16 20:20 Anime
drwxrwxrwx 17 1000 1000 36 Dec 16 22:40 Downloads
drwxrwxrwx  2 1000 1000  2 Dec 16 20:20 Files
drwxr-xr-x  2 1000 1000  2 Dec 16 20:20 HD Movies
drwxrwxrwx  2 1000 1000  2 Dec 16 20:20 Random

cat /etc/idmapd.conf
[General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup
```

client

```
cat /etc/idmapd.conf
[General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup

id user
uid=1000(user) gid=1000(user) groups=1000(user),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),111(lpadmin),112(sambashare),1001(rtorrent-www)

ls -n /storage/
total 10
drwxr-xr-x 2 0 0 2 Dec 16 20:20 Anime
drwxr-xr-x 2 0 0 2 Dec 16 20:20 Downloads
drwxr-xr-x 2 0 0 2 Dec 16 20:20 Files
drwxr-xr-x 2 0 0 2 Dec 16 20:20 HD Movies
drwxr-xr-x 2 0 0 2 Dec 16 20:20 Random

```

---

### Post by papibe on 2013-12-16
Thanks.

I'm a little puzzled :confused:

Are you sure it is mounted? There's a difference in the creation time on the Download directory:

Server says 22:40, and client's 20:20.

It makes me think you are seeing a local directory on the client. You should see the mounts by running any of these 2 commands:
```
mount -l

df -h
```
Regards.

---

### Post by kripz on 2013-12-16
> **papibe said:**
> Thanks.

I'm a little puzzled :confused:

Are you sure it is mounted? There's a difference in the creation time on the Download directory:

Server says 22:40, and client's 20:20.

It makes me think you are seeing a local directory on the client. You should see the mounts by running any of these 2 commands:
```
mount -l

df -h
```
Regards.


Yes it's mounted, could just be wrong time/timezone or something. Those folders do not exist on the client, only the mount point directory named storage.

```
sudo mount
/dev/vda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
192.168.1.13:/storage/public on /storage type nfs (rw,noexec,nosuid,nodev,noatime,vers=3,intr,addr=192.168.1.13,_netdev)


df -h
Filesystem                    Size  Used Avail Use% Mounted on
/dev/vda1                      54G  3.0G   48G   6% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          488M  4.0K  488M   1% /dev
tmpfs                         100M  360K  100M   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          498M     0  498M   0% /run/shm
none                          100M     0  100M   0% /run/user
192.168.1.13:/storage/public  8.3T     0  8.3T   0% /storage
```

time difference just in case it's related:

server
> date +%s
1387246750

client
> date +%s
1387246776

---

### Post by kripz on 2013-12-16
I think i've found the problem, i'm using ZFS and sub pools so it's trying to "cross mount" or somthing like that. See here: [http://zfsguru.com/forum/zfsgurudevelopment/516](http://zfsguru.com/forum/zfsgurudevelopment/516)

Until i get nfs4 working i wont know if that's the problem or not. I might try that nfs3 recursive mounting script first to see what happens.

EDIT:

Fixed. Problem was related to cross filesystem mounting (ZFS pools/subpools are exposed as individual filesystems). Mounting each folder individually works.

I had to modify the script in the link to get it work for bash/ubuntu.

```
#!/bin/bash

# target NFS dataset
TARGET="storage/public"
# server
SERVER="192.168.1.13"
# local mountpoint
MOUNTPOINT="/storage"
# mount options
MOUNTOPTIONS="_netdev,vers=3,defaults,user,auto,noatime,intr"

# start mounting main filesystem
mount.nfs ${SERVER}:/${TARGET} ${MOUNTPOINT} -o ${MOUNTOPTIONS}
RV=${?}
if [ "${RV}" -eq "0" ]
then
 echo "* dataset mounted: ${TARGET}"
fi

# retrieve children based on directories in TARGET path
CHILDREN=($(find ${MOUNTPOINT}/ -maxdepth 1 -type d))

for CHILD in ${CHILDREN[@]:1}
do
 # mount child filesystem/directory
 CHILDBASE=`basename ${CHILD}`
 mount.nfs ${SERVER}:/${TARGET}/${CHILDBASE} ${MOUNTPOINT}/${CHILDBASE}  -o ${MOUNTOPTIONS}
 RV=${?}
 if [ "${RV}" -eq "0" ]
 then
  echo "* dataset mounted: ${TARGET}/${CHILDBASE}"
 else
  echo "* dataset FAILED: ${TARGET}/${CHILDBASE}"
  exit 1
 fi
done

echo "* done"

```

---

