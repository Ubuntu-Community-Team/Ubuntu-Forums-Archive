---
title: "USB Hardrive Permissions"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by clive littlewood on 2009-10-11
Hi All

I have purchased a USB hardrive to use for transferring files between 2 Ubuntu comps and to keep a backup of both home directories.

I have installed Karmic and to transfer my home files I had to change the file permissions on the drive from root.

Question : How can I format and use the drive so that it is NOT root and I can just drag and drop as normal to transfer.

I know this is probably simple but I cannot get my head round this.

Thanks

Clive

---

### Post by LewRockwell on 2009-10-11
File permissions are different from hard drive permissions

.

---

### Post by clive littlewood on 2009-10-11
Thanks Lew

Would you care to expand your comment !!

Clive

---

### Post by 3rdalbum on 2009-10-11
You know the mount point of the hard drive? It's the folder you open in the filesystem that appears to contain all the contents of the external hard disk. It's usually in /media.

Open a root file browser and right-click on the mount point. Go to Properties and the Permissions tab, and change the owner and group to your user account.

---

### Post by clive littlewood on 2009-10-11
Thanks 3rdalbum

Thats exactly what I was looking for. I will mark as solved.

Clive

---

### Post by cmcanulty on 2009-10-11
I logged in as root in nautilus and when I try to change ownership of my ext drive  it just goes back to root and won't change is there a special way of doing this?

---

### Post by fela on 2009-10-11
You can also do it using the CLI, like so, where user is your username and /media/disk is the mountpoint:

```
sudo chown user:user /media/disk
sudo chmod 755 /media/disk
```

---

### Post by mcduck on 2009-10-11
What filesystem the drive has? If you are using FA or NTFS it won't support Linux/Unix-style permissions and ownerships so you won't really be able to change them at all. (permissions for thosefilesystems are set at mount time and for the whole filesystem).

If it's Ext2/3/4 or some other Linux filesystem, what I usually do is simply that I create a directory in that drive's root and set ownership & permissions of *that directory*, and leave the filesystem itself owned by root.

---

### Post by cmcanulty on 2009-10-11
Oh that explains it as the drive is NTFS

---

