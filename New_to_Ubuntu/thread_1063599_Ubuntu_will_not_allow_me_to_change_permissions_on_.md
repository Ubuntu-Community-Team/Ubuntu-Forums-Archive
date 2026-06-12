---
title: "Ubuntu will not allow me to change permissions on an external fat32 drive."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by sunexplodes on 2009-02-08
SO, my girlfriend's mac died, and I removed the hard drive and put it in an enclosure. I then copied all the files over to my internal HD and formatted the mac drive to fat32, for maximum compatibility with mine and other computers. Of course afterwards, I copied all her files back.

NOW, I'm trying to set her up with an account on my Ubuntu machine, and the drive won't work for her. She can see it, it mounts fine, etc. But she can't write to it. I can write to it without any issue from my account. The owner is set as me, as is the group, which I cannot seem to change. 
[b]
Here's what I've tried:
[/b]
```
sudo chown -hR hayley /media/MacHD
``` resulted in a big string of "changing ownership of _______: Operation not permitted"

Simply adjusting the permissions by right-clicking the drive and checking the permissions tab does nothing. I've used chmod to change the permissions to 755, and nothing seems to change.

**Here's some info that might help in solving this:**

```
ls -la
``` produces this result for it:
```
drwxrwxrwx  8 kylo kylo 16384 2009-02-08 02:19 MacHD
```

My /etc/fstab line for it looks like:
```
UUID=BEDE-7D51	/media/MacHD	vfat	defaults,auto,umask=000,uid=1000,gid=1000 0 0
```

If I can provide any additional info, let me know. Thanks.

---

### Post by jrusso2 on 2009-02-08
Maybe because FAT 32 is very limited in the pemissions you can assign.

---

### Post by ugm6hr on 2009-02-08
Permissions don't really work with fat, you have to set them for the mountpoint.

Your fstab sets the owner / group as 1000, which is generally the default first created user in Ubuntu - hence you can write to it, but not the new user created.

Just change that line in fstab to use the new user id / group (uid, gid).

See this for detail: [http://ubuntuforums.org/showthread.php?p=5259070#post5259070](http://ubuntuforums.org/showthread.php?p=5259070#post5259070)

---

### Post by GCoffee on 2009-02-08
Have considered reformatting it as a Ext or NTFS Drive?

---

### Post by JKyleOKC on 2009-02-08
> **ugm6hr said:**
> 
Your fstab sets the owner / group as 1000, which is generally the default first created user in Ubuntu - hence you can write to it, but not the new user created.

Just change that line in fstab to use the new user id / group (uid, gid).

When you do this, she will be able to write to it but you won't. If you create a new group called "allofus" and look up its GID, then change the fstab value to match and go into each user profile and add both of you to group "allofus" then you will both be able to read and write to it.

---

### Post by sunexplodes on 2009-02-08
> **GCoffee said:**
> Have considered reformatting it as a Ext or NTFS Drive?

I'd rather not. It gets swapped between Windows, Linux and Mac machines, so I'm going for a neutral filesystem. And besides, I shouldn't have to reformat to make linux write to it, I'd rather have things work properly than to have to stoop to workarounds. I think I'll try making some edits to the fstab and see if that works.

---

### Post by kansasnoob on 2009-02-08
Try just installing pmount from synaptic or from terminal:

```
sudo apt-get install pmount
```

A brief description from synaptic;

> mount removable devices as normal user
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.

Canonical does not provide updates for pmount. Some updates may be provided by the Ubuntu community.

---

### Post by handydan918 on 2009-02-08
Just to be clear, there is no support for permissions ON any fat32 filesystem. You can certainly put any permissions you like on the mountpoint.

As long as none of the inherent limitations of the fat32 system rule it out for you,there is no reason it shouldn't "just work" with linux and all others you mentioned.

---

### Post by sunexplodes on 2009-02-08
> **handydan918 said:**
> Just to be clear, there is no support for permissions ON any fat32 filesystem. You can certainly put any permissions you like on the mountpoint.

As long as none of the inherent limitations of the fat32 system rule it out for you,there is no reason it shouldn't "just work" with linux and all others you mentioned.

Yeah, that's the thing. I don't care about putting any permissions on it. I just want my girlfriend's acct to have read/write, or ideally for both of us to have that. There's no reason for that to be out of the question with a fat32 drive.

Might just try pmount though, never heard of that.

---

### Post by ugm6hr on 2009-02-09
> **sunexplodes said:**
> There's no reason for that to be out of the question with a fat32 drive.

JKyleOKC has offered a solution.  There is no reason at all.

---

### Post by sunexplodes on 2009-02-09
Okay, so I've gone into the fstab and changed the uid and gid to her user and group. I can no longer write to the drive as predicted, but she is still unable, for whatever reason.

---

