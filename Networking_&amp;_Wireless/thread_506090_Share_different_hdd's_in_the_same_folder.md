---
title: "Share different hdd's in the same folder"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by riaal on 2007-07-21
Hi, 

I have a problem. I want to share about 10 folders located on different hard disks. (Like /sda1/download and /sdb1/music and so on)

I want this folders to be mounted on the remote machines in one single folder so I just have to mount ones! At the moment I have all the folders shared (NFS) and then mount them in on single folder on the remote machines. As you can understand this is much work.

Whats the best way to do this?

I have tried out ln -s (symlinks) and to mount them twice whit --bound command on the server. Whit out luck.

Thanks.
Have a great day!

/Richard

---

### Post by bernied on 2007-07-21
The option is bind, not bound. (was that a typo?)

I would try an /etc/fstab something like this:
```
/dev/sda1 /mnt/disk1 ext3 defaults 0 0
/dev/sdb2 /mnt/disk2 ext3 defaults 0 0
/mnt/disk1 /mnt/shares/1 none bind 0 0 
/mnt/disk2 /mnt/shares/2 none bind 0 0
```
And then export /mnt/shares

... but maybe you are already doing this. If so the problem is maybe a limitation of NFS. Can you share NFS shares across multiple file-systems? Maybe not - or not without some tweaking.

---

### Post by bernied on 2007-07-21
This is from the [exports man page](http://linux.die.net/man/5/exports):
> nohide 
This option is based on the option of the same name provided in IRIX NFS. Normally, if a server exports two filesystems one of which is mounted on the other, then the client will have to mount both filesystems explicitly to get access to them. If it just mounts the parent, it will see an empty directory at the place where the other filesystem is mounted. That filesystem is "hidden". 
Setting the nohide option on a filesystem causes it not to be hidden, and an appropriately authorised client will be able to move from the parent to that filesystem without noticing the change. 
However, some NFS clients do not cope well with this situation as, for instance, it is then possible for two files in the one apparent filesystem to have the same inode number. 
The nohide option is currently only effective on single host exports. It does not work reliably with netgroup, subnet, or wildcard exports. 
This option can be very useful in some situations, but it should be used with due care, and only after confirming that the client system copes with the situation effectively. 
The option can be explicitly disabled with hide.
Good luck.

---

### Post by bernied on 2007-07-21
It's maybe not what you want, but you can do this without so much pain with samba shares.

---

### Post by riaal on 2007-07-21
Well, the first thing works, Mounting them on the server. When I share it whit NFS (even whit the nohide option) they do not apear on the remote computer. =( 

Thanks for helping!

---

