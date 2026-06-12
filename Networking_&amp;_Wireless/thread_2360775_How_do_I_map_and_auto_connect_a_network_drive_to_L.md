---
title: "How do I map and auto connect a network drive to Lubuntu?"
date: 2017-05-08
forum: Networking &amp; Wireless
---

### Post by finchy505 on 2017-05-08
Hi guys

I have a shared network folder on my Qnap NAS that I need to be mapped to my Lubuntu PC, and for it to auto connect to it on start up (regardless of whether a user is logged in). What is the best way to do it? 

I tried using RPCBind, which seemed to work initially but after a reboot it no longer seems to be mapped to that network share. 

This was how I did it.....

$ mkdir NAS
$ sudo apt-get install nfs-kernel-server rpcbind nfs-common
$ sudo update-rc.d rpcbind enable 
$ sudo cp /etc/fstab /etc/fstab.backup
$ sudo leafpad /etc/fstab


This will open up fstab in Leafpad. Add this to the bottom with NAS IP address at x.x.x.x, NAS share at yyyy, zzz is the name of the network share (NAS) and wwww is either nfs or cifs;
//x.x.x.x/yyyy /home/<username>/zzz wwww guest,uid=<username>,gid.<username>,nobrl,noauto,x-systemd.automount  0 0


//192.168.0.10/network-share /home/finchy/NAS nfs guest,uid=finchy,gid.finchy,nobrl,noauto,x-systemd.automount  0 0

Is there a better way to do it so it connects and stays connected as a mapped drive? 

Thanks

---

### Post by TheFu on 2017-05-08
NFS and the fstab is a way, but don't use the UID/GID or guest stuff. Actually, with NFS, you shouldn't need many options at all. Those are for CIFS style mounts, not NFS.
Don't mount system storage under a personal HOME either. Lots of reasons this shouldn't be done.  Create a directory somewhere else, perhaps /Net and mount it there.

BTW, using sudo with a GUI editor can have dangerous side effects.  Best to use **sudoedit /path/to/file**. This is always safe.

I use autofs, so I can't just give you the NFS options I use.  I use NFS for about 10 different mounts across all the systems here and have been using NFS for about 25 yrs.  Chances are your storage device has an NFS how-to that should be followed.  The main thing is to have the uid/gid numbers as returned by the 'id' command correct for the files and directories.  There is an Ubuntu nfs how-to - google will find it. 

When you don't have things working, just do it from a shell to nail things down. Start with:
```
sudo mount -t nfs 192.168.0.10:/network-share /Net
```
Then use **sudo chown** to fix the ownership as needed.  Normally, root doesn't have any privileges on NFS storage. This is a security thing, but I suspect on a NAS device they allow external root accounts to do things.

Hope this helps.

---

