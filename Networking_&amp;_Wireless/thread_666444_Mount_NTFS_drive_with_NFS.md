---
title: "Mount NTFS drive with NFS:"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by kmatthews812 on 2008-01-13
I am trying to mount an NTFS drive with NFS, and I keep getting the following error when I run 'sudo exportfs -a'

/media/sda1/Backup does not support NFS export.

Here is what I have in my /etc/exports file:

/media/sda1/Backup      172.168.1.100(ro,async,no_subtree_check)

And here is what I have in my /etc/fstab file:

/dev/sda1       /media/sda1     ntfs defaults                0       0

I can access the drive through its mount point with no problem.  I just cannot successfully export it via NFS.  I can export other directories on the ext3 partition via NFS without any problems, but the NTFS drives fail.  

Looking through the system logs does not give me any more debugging information about what the drive does not support NFS export.  Has anybody seen this before?  What can I change to fix this?  


Thanks,

Kev

---

### Post by HermanAB on 2008-01-13
Hmm, I think this line in the client fstab should be 'nfs' not 'ntfs':
/dev/sda1 /media/sda1 ntfs defaults 0 0

The export file tells the server what file system is used on the physical drive.

The fstab file tells the client how to mount the distant drive and by that time, the distant drive has been abstracted already to nfs by the server.

Cheers,

Herman

---

### Post by kmatthews812 on 2008-01-13
Well, I'm trying to do this in 2 steps.  The first step is to mount the physical drive to a directory.  That's what I'm doing with the fstab file.  Since the drive is NTFS formatted, the fstab entry must specify NTFS instead of NFS.  

After that, I'm trying to export the directory via NFS, which is where the error is occurring.

---

### Post by Servechilled on 2008-02-27
> **kmatthews812 said:**
> Well, I'm trying to do this in 2 steps.  The first step is to mount the physical drive to a directory.  That's what I'm doing with the fstab file.  Since the drive is NTFS formatted, the fstab entry must specify NTFS instead of NFS.  

After that, I'm trying to export the directory via NFS, which is where the error is occurring.

I figured it out. Uninstall nfs-kernel-server from Synaptic and install nfs-user-server. It appears that exportfs no longer is installed, so to update your exports, as far as I know you'll have to run ```
sudo /etc/init.d/nfs-user-server restart
```

All this on my 2nd day of running Ubuntu :D (been using RedHat for years, but I've found Ubuntu works much better for me.)

---

### Post by Vladimir Hidalgo on 2008-06-02
I did a little guide to solve this problem in Feisty (I guess it work for Hardy too), it's in Spanish, but most can be understood even if you don't know the language.

[http://www.svcommunity.org/forum/index.php?topic=55193.0](http://www.svcommunity.org/forum/index.php?topic=55193.0)

Vlad.

---

