---
title: "How to set individual NTFS partitions permissions behaviour for each user account?"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by ryniek on 2011-01-30
I've already asked for help @ AskUbuntu, two days ago (here's source: [http://askubuntu.com/questions/23759/how-to-set-individual-ntfs-partitions-permissions-behaviour-for-each-user-account]("http://askubuntu.com/questions/23759/how-to-set-individual-ntfs-partitions-permissions-behaviour-for-each-user-account") ), but no one replied. Maybe here on forum someone knows the answer?

Thank you

---

### Post by HermanAB on 2011-01-30
You can't.  NTFS is a Windows file system.  Use Ext3, Ext4, XFS or JFS.

---

### Post by ryniek on 2011-01-31
> **HermanAB said:**
> You can't. NTFS is a Windows file system.

Even using NTFS-3G driver? There must be some way to do it. I can't now reformat those two partitions, because i have important data on them, plus i don't have any external hard drives :f

---

### Post by Morbius1 on 2011-01-31
The title of your topic and what you wrote in askubuntu are two different things if I read your post correctly. 

This is your fstab entry for the VM partition:
> UUID=60FF39EB72B72264 /media/VM ntfs noauto,uid=1000,gid=1000,umask=0077,nodev,locale=pl_PL.utf8 0 0What you wrote in askubuntu:
> VM for my VirtualBox .vdi file) for which i must have full permissions for my allday use accountThe second "0" in umask=0077 combined with uid=gid=1000 will do that.
> For Guest account, i want make VM partition fully disabled and invisible (and thus it mustn't automount)Automounting has nothing to do with something being disabled or invisible. The last 2 "7" in umask=0077 will do what you want. Everyone will see that there is a /media/VM mountpount but only you will be able to open the folder.
> ..but VM can be only set to limited and have disabled automounting - so guest can't mount it but it still can be seen in Nautilus, plus I must always mount it manually when i login to allday account.Get rid of the "noauto" option. Your fstab entry should look look this:
```
UUID=60FF39EB72B72264 /media/VM ntfs uid=1000,gid=1000,umask=0077,nodev,locale=pl_PL.utf8 0 0
```

---

### Post by vanadium on 2011-01-31
> **ryniek said:**
> Even using NTFS-3G driver? There must be some way to do it. I can't now reformat those two partitions, because i have important data on them, plus i don't have any external hard drives :f
Your data cannot be important. Otherwise, you would have a backup copy.

---

### Post by ryniek on 2011-01-31
> **vanadium said:**
> Your data cannot be important. Otherwise, you would have a backup copy.

> [...]plus i don't have any external hard drives :f

and my upload is too slow to make online backup.

But this topic is about NTFS partitions not backups.

---

### Post by vanadium on 2011-01-31
I just wanted to point you gently to the importance of having a backup. Not only because it is the only way to preserve data, but also because it would have allowed you to eventually change the file system. Your internal disk can break anytime. Then your data is lost. You can simply not permit that if your data are important. If you think you can, then your data are probably not that important to you.

Independent of ntfs partitions, it is impossible with the standard linux system to set permissions that change dependent on the user. You can assign rights to owners, groups and others, and you can assign an owner and group. These are static, though.

In your scenario, you could disable all rights for "others" (which includes "guest") and enable read only for others on the Downloads permission. You set the owner to your "allday use" and provide that all rights. This would probably do what you want.

There is no reason not to mount your VM partition: permissions will make sure that it cannot be accessed or read by guest.

For ntfs partitions in particular, you cannot set permissions and ownerships on each individual directory or file, because ntfs does not support unix permissions. You can only set permissions for the whole volume at once. You need to do this through mounting options, as Morbius1 showed in detail.

---

### Post by ryniek on 2011-01-31
> **Morbius1 said:**
> The title of your topic and what you wrote in askubuntu are two different things if I read your post correctly. 

This is your fstab entry for the VM partition:
What you wrote in askubuntu:
The second "0" in umask=0077 combined with uid=gid=1000 will do that.
Automounting has nothing to do with something being disabled or invisible. The last 2 "7" in umask=0077 will do what you want. Everyone will see that there is a /media/VM mountpount but only you will be able to open the folder.
Get rid of the "noauto" option. Your fstab entry should look look this:
```
UUID=60FF39EB72B72264 /media/VM ntfs uid=1000,gid=1000,umask=0077,nodev,locale=pl_PL.utf8 0 0
```

Hey, thanks, it worked. Now when i log in to guest account, VM partition isn't mounted and can't be seen in Places tab (system bar on desktop) or in Nautilus.

Here's my *fstab* config:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda1 :
UUID=35e66658-5ee9-40cf-bf56-8204959e3df0	/	xfs	defaults	0	1
#Entry for /dev/sda2 :
UUID=26c714cf-4236-45e7-9c46-cfcf91a215ae	/home	xfs	defaults	0	2
#Entry for /dev/sda5 :
UUID=1315BCB027C44639	/media/DOWNLOADS	ntfs-3g auto,uid=1000,gid=1000,umask=0022,nodev,locale=pl_PL.utf8	0	0
#Entry for /dev/sda6 :
UUID=60FF39EB72B72264	/media/VM	ntfs-3g auto,uid=1000,gid=1000,umask=0077,nodev,locale=pl_PL.utf8	0	0
#Entry for /dev/sda7 :
UUID=c52411f5-105c-45d1-971f-412f962c350e	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0

```

So far everything is working, so topic is **SOLVED**.

---

