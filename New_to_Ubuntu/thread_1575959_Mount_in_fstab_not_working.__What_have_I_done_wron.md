---
title: "Mount in fstab not working.  What have I done wrong?"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by necronom on 2010-09-16
I've searched for answers on this, and tried what was suggested, but it doesn't work for me.  This is what I want and what I've tried:

I have my email on an NTFS partition, and I'm using the Opera email client to use the same email directory, so when I boot in either Linux or XP I have everything there.

I had it working, but I had to manually mount the "Software" drive every time, which was annoying, so I entered a command (I can't remember what it was at the moment), and it listed this:

```
/dev/sdb2 /media/Software fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0
```I read that I just need to paste that into my /etc/fstab file.  I did that, but when I rebooted I got this:

```
An error occured while mounting /media/Software
Press S to skip mounting or M for manual recovery
```Then, when I got to my desktop, I tried the manual way to mount it (through the "Places" menu), but that now says:

```
Unable to mount Software

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb2 on /media/Software
```I then used chown to make me the owner of the /media/Software directory that must have been made when I manually mounted it through the menu:

```
drwxr-xr-x 2 paul paul 4096 2010-09-15 22:10 Software
```but that didn't make any difference from when it said "root root".

I'm now at a loss.

Any ideas?

---

### Post by Mark Phelps on 2010-09-16
Don't have an immediate answer, but in general, it's a bad idea to automount an MS Windows NTFS partition read/write if it is also an OS boot partition.  One unclean shutdown and you won't be able to boot into your MS Windows OS in order to run chkdsk to repair the partition.

A better approach is to mount it using Places, only when needed, and then use the Clean Shutdown option (in Places) to dismount it.  That avoids the problem of unclean shutdowns.

---

### Post by necronom on 2010-09-16
It's not my OS partition, but it does have all my XP software on it.  Would one of these "unclean shutdowns" cause a problem to my software?  What do they do?  Do they destroy partitions, and how often do they happen?  That sounds quite worrying!

I need my email every time I switch my computer on, so that's why I want to automount it.

I can't see a "clean shutdown" option in Places.  If there is such a thing somewhere, why would it choose to do an unclean shutdown as a default? :confused:

---

### Post by sisco311 on 2010-09-16
The fstab entry should look like this:
```
UUID=**uuid-of-the-partition-here**  /media/Software  ntfs  defaults,uid=paul,gid=paul,dmask=002,fmask=113  0  0
```

To get the UUID of the partition, run:
```
sudo blkid -o list /dev/sdb2
```

---

### Post by CharlesA on 2010-09-16
You can also use /dev/sdxy, but it'll get messed up if the drive designation changes.

Best to use UUID IMHO.

---

### Post by necronom on 2010-09-16
I tried that, but nothing was any different.

```
paul@Paul-Linux:~$ sudo blkid -o list /dev/sdb2
[sudo] password for paul: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sdb2  ntfs    Software (not mounted)  000000004B239555
paul@Paul-Linux:~$ 

```Here is my full fstab file:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=9981f009-738a-46af-8ace-a0e8ef61a870  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=5a7bdd6c-f710-4885-bccf-f97eeb799116  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  

UUID=000000004B239555   /media/Software   fuseblk  rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096  0  0


```

---

### Post by CharlesA on 2010-09-16
Try this:

```
sudo mount /dev/sdb2 -t ntfs /mount/Software
```

I'm not 100% positive if the type should be ntfs or something else, since I don't have a machine I can test it with.

---

### Post by MooPi on 2010-09-16
It doesn't seem to have all the parts, missing file system .
try this:
```
UUID=000000004B239555   /media/Software ntfs defaults 0  0
```

---

### Post by necronom on 2010-09-16
I got this:

```
paul@Paul-Linux:~$ sudo mount /dev/sdb2 -t ntfs /media/Software
Using default user mapping

```

That does now let me see my Software partition, though when I reboot I assume it will be gone again.

---

### Post by necronom on 2010-09-16
> **MooPi said:**
> It doesn't seem to have all the parts, missing file system .
try this:
```
UUID=000000004B239555   /media/Software ntfs defaults 0  0
```

Isn't fuseblk the file system (file system in user space).  I think it's used to mount NTFS partitions for non root users.  Or so I read.

I could try simplifying the fstab line, but I was worried about not using the exact info that the (forgotton) linux command gave me when I mounted it manually.  Maybe the defaults aren't the same as what my drive uses.  I don't want to corrupt it.

---

### Post by MooPi on 2010-09-16
That is how I've mounted my ntfs partitions without error. Maybe I'm doing it wrong but it works.
 I would like to add that if your partition is labeled > Software and you have created a folder in media by the same name you may end up with two folders in your file manager indicating Software. The fstab addition should be enough for your file manager to show the proper folder.

---

### Post by CharlesA on 2010-09-16
OK I lied. I forgot that I have a VM with an NTFS partition..

I'll post a working fstab in a sec.

Here you go:
```
/dev/sda1     /media/ntfs     ntfs     (rw,nosuid,nodev,allow_other,default_permissions) 0 0

```

You can replace /dev/sda1 with the UUID of that partition if you like.

---

### Post by snoopo71 on 2010-09-16
> **CharlesA said:**
> OK I lied. I forgot that I have a VM with an NTFS partition..

I'll post a working fstab in a sec.

Here you go:
```
/dev/sda1     /media/ntfs     ntfs     (rw,nosuid,nodev,allow_other,default_permissions) 0 0

```

You can replace /dev/sda1 with the UUID of that partition if you like.


What do you think about that:

UUID=000000004B239555          /media/Software           ntfs-3g       defaults        0  0



Before of this (maybe you've already done it but), in a console do:

sudo mkdir /media/Software
sudo apt-get install ntfs-3g



I think the ntfs-3g is more recomendable(allows r/w access) and the defaults are what you normally need.

---

### Post by CharlesA on 2010-09-16
Heh I just mounted it and copied whatever it used into fstab.

The one I posted allowed rw access.

If you want to just use "defaults" go for it. :)

---

### Post by necronom on 2010-09-16
Thanks, that's sort of worked.

I'm still a bit worried about using different settings (like ntfs instead of fuseblk), but the main thing now is that it's using /media/ntfs instead of /media/Software.

Was there a reason for that?  My email and settings are referenced in /media/Software.  Can I just change it back to Software in fstab?

---

### Post by CharlesA on 2010-09-16
Should be able to.

Just unmount /media/ntfs and run ***sudo mount -a*** to remount it.

---

### Post by necronom on 2010-09-16
That's better! :D

I also re-found the command I'd forgotton:

```
sudo cat /etc/mtab
```

which now shows:

```

/dev/sdb2 /media/Software fuseblk rw,nosuid,nodev,allow_other,allow_other,blksize=4096,default_permissions 0 0

```

Which I think is exactly as it did originally, and what I wanted to see.

I have an empty /media/sdb2.  Is it safe to delete it?  It must have been created during my attempts to mount it using the device name rather than the ID.  Or possibly something else did it?


I might look into creating a new NTFS partition, and putting Opera (which also handles my email), and also my "Downloads" directory in it.  That way, nothing else will be at risk, and I'll back that one up often.

Thanks for the help everyone.  It's amazing that something that I expected to be easy (right click the drive, go to properties and choose mount at startup is what I expected), turned into a bit of a nightmare.  These are the sort of things that put people off Linux.  It won't put me off though. :)

Not yet, anyway.

---

### Post by CharlesA on 2010-09-16
You should be able to delete it if it's empty. There isn't normally anything in /media unless you create it yourself or have something mounted.

---

### Post by sisco311 on 2010-09-16
> **necronom said:**
> Thanks, that's sort of worked.

I'm still a bit worried about using different settings (like ntfs instead of fuseblk), ...

NTFS-3G often uses the FUSE file system interface, so it can run unmodified on many different operating systems. That's why the **mount** command (or cat /etc/mtab) reports it as **fuseblk**. 

In fstab the third field describes the filesystem type, which is **ntfs** (or ntfs-3g, it doesn't really matter, mount.ntfs is a symlink to mount.ntfs-3g).

---

