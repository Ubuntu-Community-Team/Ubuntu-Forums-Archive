---
title: "Access to NFS export does not work"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by Cascade49 on 2008-11-01
Hello,

I'm not sure if I'm in the right support category for this one. I've got a problem accessing to one of my NFS exports with one of my clients. The network consist of a Debian Etch server, two Ubuntu 8.04 and two Kubuntu 8.04 clients.

Following the entries in **/etc/exports** of the server:

```
/srv/music         192.168.1.0/24(rw,no_root_squash)
/srv/data          192.168.1.0/24(rw,no_root_squash)
/home              192.168.1.0/24(rw,no_root_squash)
```

Following permissions are set on the exported directories:

```
drwxrws---  13 root users  4096 2008-11-01 09:59 data
drwxrws--- 286 root musik 24576 2008-09-26 13:14 music
drwxrws---   9 root users  4096 2008-04-05 20:35 home
```

The entries in **/etc/group** on all computers are as follows:

```
users:x:100:myuser
music:x:1100:myuser
```

On all four clients **/etc/fstab** looks like this:

```
server:/srv/music        /mnt/music        nfs   user,auto    0    0
server:/srv/data         /mnt/data         nfs   user,auto    0    0
server:/home             /mnt/home         nfs   user,auto    0    0
```

On all clients the imported directories look like this:

```
mxuser@clientx:~$ ls -l /mnt
drwxrws---  13 root users  4096 2008-11-01 09:59 data
drwxrws---   9 root users  4096 2008-04-05 20:35 home
drwxrws--- 286 root musik 24576 2008-09-26 13:14 music
myuser@clientx:~$ mount | grep server
server:/srv/music on /mnt/music type nfs (rw,user=root,noexec,nosuid,nodev,addr=192.168.1.x)
server:/srv/data on /mnt/data type nfs (rw,user=root,noexec,nosuid,nodev,addr=192.168.1.x)
server:/home on /mnt/home type nfs (rw,user=root,noexec,nosuid,nodev,addr=192.168.1.x)
```

However, on one of the Kubuntu clients I am not able to access the **music** folder. Following error message is given:

```
myuser@client4:~$ cd /mnt/musik
bash: cd: musik: Permission denied
```

Creating a folder with the same permissions locally on the very same client, I'm able to access this folder without any problem. Changing the group for **/srv/music** on the server and re-importing it to the client enables me to change into the folder as well. On the remaining three clients it's working well in the original configuration.

I can't see any differences in the configuration of those four clients, neither did I find a log file showing more detailled information on this problem.

I would very much appreciate if somebody had got a clue on this problem. Thanks a lot...

Regards,
Cascade

---

### Post by Cascade49 on 2008-11-07
Push ;-)

Nobody any idea??

---

