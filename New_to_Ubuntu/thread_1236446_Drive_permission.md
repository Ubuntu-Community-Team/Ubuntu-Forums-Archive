---
title: "Drive permission"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by PartsMan on 2009-08-10
How come if I create/format a drive I don't have permission to use it?

How do I set Permissions? I have searched and searched and can only find file permission not drive.

I had this problem with my thumb drive the other day. Ended up using a vista machine to format it and them I had permission in Ubuntu.:( Not cool!

Now I have a second hard drive that I can't use. Don't think I can put it in my wifes laptop to fix.

---

### Post by credobyte on 2009-08-10
```
sudo chown -R user:user /media/flash

```Replace user:user with your username ( eg. dainis:dainis ) and /media/flash with your drive mount point.

---

### Post by 3rdalbum on 2009-08-10
> **PartsMan said:**
> How come if I create/format a drive I don't have permission to use it?

You're not quite "thinking Unix" yet. Root can format a drive, your user account can't. So, the user that formatted the drive has permission to use it. Root needs to extend permission to the users, in order for the users to access it.

> How do I set Permissions? I have searched and searched and can only find file permission not drive.

Change the permission of the mount point. If the device is mounted at /media/disk, for instance, you change the permission of /media/disk, as root, to allow your user account to access it.

---

### Post by PartsMan on 2009-08-10
Will that give me permission or make me able to change permission?

---

### Post by asmoore82 on 2009-08-10
And remember that all filesystems from the DOS world cannot store UNIX permissions.

---

### Post by PartsMan on 2009-08-10
> **3rdalbum said:**
> You're not quite "thinking Unix" yet. Root can format a drive, your user account can't. So, the user that formatted the drive has permission to use it. Root needs to extend permission to the users, in order for the users to access it.



Change the permission of the mount point. If the device is mounted at /media/disk, for instance, you change the permission of /media/disk, as root, to allow your user account to access it.

But I didn't log in as root to format. I used partition editor.
Partition editor should let you set permissions. It's only doing half the work.

---

### Post by PartsMan on 2009-08-10
> **asmoore82 said:**
> And remember that all filesystems from the DOS world cannot store UNIX permissions.

Not even a faint memory on these drives. I have to deal with Microsoft all day at work.

---

### Post by asmoore82 on 2009-08-10
> **PartsMan said:**
> Not even a faint memory on these drives. I have to deal with Microsoft all day at work.

I don't follow here;
In the OP you said that using a Vista machine "fixed" a similar issue.
Surely it's not a Unix filesystem then...

---

### Post by PartsMan on 2009-08-10
> **asmoore82 said:**
> I don't follow here;
In the OP you said that using a Vista machine "fixed" a similar issue.
Surely it's not a Unix filesystem then...

Sorry, My thumb drive is formatted FAT32 by a vista machine so that I could backup my files before formatting my hard drive. Both my hard drives were formatted to run linux. (can't think of it now. "f?3")

Kills me that a drive formatted on a separate windows machine works but one done on Ubuntu with the supported program does not.

---

### Post by Paqman on 2009-08-10
> **PartsMan said:**
> I have searched and searched and can only find file permission not drive.


In Linux, everything is a file. Even devices like drives.

> **PartsMan said:**
> But I didn't log in as root to format. I used partition editor.


Notice how you need to supply your password to open Gparted? That's where you're elevating your privileges to become a super user (aka: root)

> 
Partition editor should let you set permissions. It's only doing half the work.

Maybe it should. You could suggest that to the Gparted devs.

---

### Post by PartsMan on 2009-08-10
Ah Ha! That make sence.

Now back to this.
> **credobyte said:**
> ```
sudo chown -R user:user /media/flash

```Replace user:user with your username ( eg. dainis:dainis ) and /media/flash with your drive mount point.
Will that make me the owner or change the permissions?

---

### Post by credobyte on 2009-08-10
> **PartsMan said:**
> Ah Ha! That make sence.

Now back to this.

Will that make me the owner or change the permissions?

You will be the owner - permissions ( execute, etc. ) will not be modified.

---

### Post by Paqman on 2009-08-10
chown = change ownership

You could do the same by setting the permissions to be very relaxed (eg: 777, meaning read/write/execute for owner/group/others) which is fine for data storage.

Getting your head wrapped around the idea of ownership and permissions will make using Linux a lot easier.

---

