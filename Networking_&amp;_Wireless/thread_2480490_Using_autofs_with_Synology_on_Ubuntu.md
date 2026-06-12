---
title: "Using autofs with Synology on Ubuntu"
date: 2022-10-31
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2022-10-31
I am using autofs with Synology on my Ubuntu laptop and the issue I have is that I cannot manage the files on my NAS through Nautilus. I think that something is wrong with my setup as networks is not something I understand very well :-(

So my setup is as follows:

**autofs.master**
```
/home/foxy/NAS /etc/auto.nfs --timeout=600 --ghost
```

**auto.nfs **
```
Video 192.168.0.29:/volume1/video
```

**On the NAS**
User permission of the folder read/write

*NFS Rules*

Hostname or IP: 192.168.0.254/255.255.255.0
Privilege: Read/Write
Squash: No mapping
And all Enable Asyncronisation, Allow connections from non-privileged ports and Allow users to access mounted subfolders are ticked.

I am not even sure that NFS is the best option, given that my network consists of 2 NAS (Synology and QNap) and a couple of laptops. But I set it up this long ago and it worked OK.

Any advice will be really appreciated.

---

### Post by TheFu on 2022-10-31
A few other people in these forums have having problems with 22.10 and their Synology devices. While I've tried to help them, it seems they wouldn't answer questions  one of them found some extremely synology-specific answer. Neither seemed interested in security.  That makes it hard to help, since security is part of the setup for everything I do.

Anyway, I don't have a synology and haven't tested 22.10. I don't use non-LTS releases except for toy stuff. New is the enemy of stable.

Comments about the settings you've posted.

Mounting network storage under an individual's HOME directory is a bad idea for a number of reasons.  Better to mount it somewhere else, perhaps /data/ and create a symbolic link from the HOME to that other location.  This is good for local and network storage and helps when you need to deal with backups.  Keeping network storage separate makes backups cleaner.

I'd use:
autofs.master
```
/-       /etc/auto.nfs --timeout=60 --ghost 
```

auto.nfs
```
/data/Video    -fstype=nfs,nconnect=4,proto=tcp,rw,async     192.168.0.29:/volume1/video
```

It is very important to actually use the correct fields in those 2 files.  There were mistakes in what you posted, so it isn't any surprise it wasn't working.

On a proper NFS server, the settings for the shared storage are in /etc/exports.   The contents of that file is like this:
```
/volume1/video       regulus(rw,async) romulus(rw,async)
```
The NFS server can ping each host (regulus, romulus).  If not, you can use IP addresses.

When the exports file is modified, restart the nfs-server on the NFS server system.
When the /etc/auto-whatever files are modified, restart autofs on the client system(s).  It may be necessary to manually umount the storage, then restart the daemon. Just depends.

Anyway, give those changes a shot and please, please, pay attention to NOT mounting extra storage directly under any user's HOME - anywhere. Problems will happen doing that.

---

### Post by foxy123 on 2022-11-02
Thanks a lot for your help.

So what I've done so far:

1. I have changed the mounting directory to /mnt and amended the auto.master file:

```
/mnt/ /etc/auto.nfs --timeout=600 --ghost
```

2. Changed syntaxis in auto.nfs file:

```
Media -fstype=nfs,nconnect=4,proto=tcp,rw,async 192.168.0.29:/volume1/Media 
Backups -fstype=nfs,nconnect=4,proto=tcp,rw,async 192.168.0.29:/volume1/homes/foxy/Backups
Music -fstype=nfs,nconnect=4,proto=tcp,rw,async 192.168.0.29:/volume1/music
Video -fstype=nfs,nconnect=4,proto=tcp,rw,async 192.168.0.29:/volume1/video
Mydocs -fstype=nfs,nconnect=4,proto=tcp,rw,async 192.168.0.29:/volume1/Mydocs
```

So now I seem to be able to edit files in all directories but the one I have created recently. If I can just access dirs like Media, Backups, Music and Video just clicking on them, the Mydocs directory requires my user password for some reason. I can see that it has different permissions and I am not sure why:
```
/mnt$ ls -l
total 28
drwxrwxrwx  4 nobody users  4096 Oct 30 18:06 Backups
drwxrwxrwx 11 root   root   4096 May 17  2015 Media
drwxrwxrwx  3 root   root  12288 Oct 30 18:04 Music
d--------- 29 root   root   4096 Oct 11  2014 Mydocs
drwxrwxrwx  6 root   root   4096 Oct 30 18:05 Video

```

I wonder if it's possible to make it behave like a normal directory.

---

### Post by foxy123 on 2022-11-02
Oh, forgot to mention what I have in /etc/exports on the Synology NAS
```
/volume1/btsync 192.168.1.254/255.255.255.0(rw,async,no_wdelay,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
/volume1/Media  192.168.0.254/255.255.255.0(rw,async,no_wdelay,root_squash,insecure_locks,sec=sys,anonuid=1024,anongid=100)
/volume1/music  192.168.0.254/255.255.255.0(rw,async,no_wdelay,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
/volume1/Backups    192.168.0.254/255.255.255.0(rw,async,no_wdelay,crossmnt,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
/volume1/homes  192.168.0.254/255.255.255.0(rw,async,no_wdelay,crossmnt,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
/volume1/photo  192.168.0.254/255.255.255.0(rw,async,no_wdelay,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
/volume1/Mydocs 192.168.0.254/255.255.255.0(rw,async,no_wdelay,crossmnt,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
/volume1/video  192.168.0.254/255.255.255.0(rw,async,no_wdelay,crossmnt,insecure,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)

```

---

### Post by TheFu on 2022-11-02
> **foxy123 said:**
>  
I wonder if it's possible to make it behave like a normal directory.

NFS mounts use normal Unix file and directory permissions.  How to use those is something you'll need to learn.  Search for "ubuntu file permissions" to find the ubuntu tutorial for it, but Unix is Unix is Unix. They all work the same.

The only thing that NFS does different is that root/sudo don't work over remote links, so changing the owner of a file/directory needs to happen on the NFS server.  For my Ubuntu-based NFS server, I simply ssh into the system and make the top level directory that is in the NFS sharing (/etc/exports) have the owner uid I want each client to use.  I suspect the synology has some webgui to accomplish the same thing. 

The permissions I'm seeing on your mounts is scary.  root:root and 777?  That's a terrible idea.  Change the owner recursively to the owner you need on the client, then from the client systems, chmod and chgrp will work as expected.  Then you can have sane permissions of 644 or 640 for the files.

---

