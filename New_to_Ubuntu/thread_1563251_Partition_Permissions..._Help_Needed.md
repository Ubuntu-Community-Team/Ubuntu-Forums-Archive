---
title: "Partition Permissions... Help Needed"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-08-28
Hello. I'm running Ubuntu 10.04, 64 bit and I have a slight problem. Upon install, I designated a 20 gig partition on my system for the root directory, and mounted a much larger data partition with music, videos, pictures etc. as /data. Not a smart move on my part, or so I've found out.
My problem is there are a lot of things it won't let me do on this partition, unless I'm sudo. It will let me delete most files, but there are some folders and things it won't let me touch. It won't let me make folders unless I make them using sudo in the terminal or via "gksudo nautilus". Also, many programs cannot create directories on this partition unless I launch them with sudo privileges.

Does anyone know how I would go about adding permissions to this folder? Or even changing its mount location so the /data folder it's mounted as isn't located in the root directory, and instead my home folder?

Thanks

---

### Post by minigeek on 2010-08-28
> **Stigmata13 said:**
> Hello. I'm running Ubuntu 10.04, 64 bit and I have a slight problem. Upon install, I designated a 20 gig partition on my system for the root directory, and mounted a much larger data partition with music, videos, pictures etc. as /data. Not a smart move on my part, or so I've found out.
My problem is there are a lot of things it won't let me do on this partition, unless I'm sudo. It will let me delete most files, but there are some folders and things it won't let me touch. It won't let me make folders unless I make them using sudo in the terminal or via "gksudo nautilus". Also, many programs cannot create directories on this partition unless I launch them with sudo privileges.

Does anyone know how I would go about adding permissions to this folder? Or even changing its mount location so the /data folder it's mounted as isn't located in the root directory, and instead my home folder?

Thanks

Hi 

Change the permissions on the partition to make you the owner

from the command line run the following command

```
chown -R yourname:yourgroup directory/
```

The -R option will change all the files and folders in that directory also.
:)

---

### Post by Miljet on 2010-08-29
If you use sudo to create a directory, that directory will belong to root, even if it is created in your home directory. Same thing for creating files or mount points. You can use the command "chown" to change ownership from root to yourself. Look at "man chown" for usage.

I would start with the mount point where the partition is mounted. Make sure that you are the owner of that mount point. Then work your way through the directories on the partitions or use the -R option and wildcards to change all at once.

---

### Post by zeroseven0183 on 2010-08-29
Part of the folder security feature in Ubuntu (and some Linux distros) is the use of *sudo* to execute stuffs that a normal user (account/permission) can't do alone. Which means, to do administrative tasks, you must prefix your commands with sudo else you can't do it.

I would suggest minimizing the use of *gksu nautilus* to manage your files and folders as you might mess up some things on the system. Having a separate partition for your data/music/video/document files, as you already did, is good enough.

No need to change permissions since most of the applications you'll install (and their configurations) will be written inside your /home/<username> directory.

---

### Post by QLee on 2010-08-29
[QUOTE=Stigmata13]...
Does anyone know how I would go about adding permissions to this folder? Or even changing its mount location so the /data folder it's mounted as isn't located in the root directory, and instead my home folder?[/QUOTE]

The information in these links can help you:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Ownership and permissions of vfat / ntfs are set at the time of mounting.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by oldfred on 2010-08-29
I mount in /use per this blog and then link into /home so home looks just like it did after the install but I deleted all the standard data folders and linked in my data folders.

Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I originally made sure I had ownership and permissions on the /data and the mounts via fstab.

sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/data
#I own everything and I am very permissive.
sudo chown -R fred:fred /usr/local/fred
sudo chmod -R 766 /usr/local/fred/data

Then mount in fstab

Then I link into /home by running these in ~.
#ln -s /usr/local/fred/data/Music
#ln -s /usr/local/fred/data/Documents
#ln -s /usr/local/fred/data/Downloads
etc for every folder in /data
I used to run each of above but this does it all  folders:
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

---

### Post by Riffer on 2010-08-30
I think WHAT you should have done is make your /data folder your /home folder.  This what I have done and there are many HOWTO's out there that can show you how to do so.

Off the top of my head a work around for you is to is to use your "gksudo nautilus" command and navigate to you /data folder.  Right click on it and on the context menu at the bottom is "properties", click on that and then go to the "Permissions" tab.  In there change the "owner" to your login name, change the "folder access" to create and delete.  Change your "group" section to the same as the "owner" section.  Also click on the box at the bottom marked "apply permissions to enclosed files".

That should do it.

---

### Post by bsalem on 2010-09-14
Are you mounting a different partition, such as an NTFS partition into a Linux partition? If so, be aware that Ubuntu can read and write to NTFS but cannot repair a corrupted NTFS filesystem and that the way Ubuntu protects you from looking at or changing sub-directories that have been damaged is to deny you access to them.

If you are mounting an EXT filesystem and permissions are set so you can't read parts of it, you may not be the owner, for example, files written by root, or it is possible that corruption has locked those parts of the partition away. You will need to make sure that the filesystem is seen at startup and checked or unmount it and check  and remount it yourself. Never check a mounted device.

I have a 1.5 TB Western Digital My Book that came shipped with NTFS and so far as I know EXT is not supported on this drive. The device has problems. It is slow to become visible when you first use it even though Ubuntu says it is mounted, and there must be some contention problems if multiple processes try to write on it, for I have had cases where the whole drive or subdirs in it go read-only and Ubuntu is unwilling to repair that. What I have had to do is to at least boot once into Windows Vista to do its equivalent of fsck, or run the disk check utility to clean up the NTFS filesystem. Then Ubuntu will set the permissions so I can write to it. You may have to do this, have Windows mount it and render it clean.

The same thing occurs if you try to read a DVD or CD with a corrupt or unsupported format, and in that case you really can't fix that.

---

