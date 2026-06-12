---
title: "USB stick - permission"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by glx5667 on 2008-12-08
I'm trying to transfer folders and files from my old computer to my new one, using a Verbatim 4GB USB stick, called STORE N GO.  I'm unable to delete files/folders already on the stick, and files/folders show the locked icon.  Message:
"error while deleting "/media/STORE...  .jpg"  - cannot be deleted because it is a read only disc"

error message while trying to copy to "/media/Store N GO"  - you do not have permission to write to this folder.

Store N Go permissions:  R  W  E

Old computer running on 6.06, new one on 8.04, I'm the only person using these computers.

---

### Post by aheckler on 2008-12-08
Try to change the owner of the drive to you:

```
chown -R USERNAMEHERE "/media/STORE N GO"
```

EDIT: You'll have to use the exact name of the drive, with the correct capitalization and everything. You might also need to use sudo before the above command to get it working.

---

### Post by geirha on 2008-12-08
What filesystem does it have? And do you mount it manually or does it mount automatically when you plug it in?

The output of these commands while the device is plugged in should help identify the problem:
```

sudo fdisk -l
df -h
ls -ld "/media/Store N GO"

```

---

### Post by glx5667 on 2008-12-09
> **geirha said:**
> What filesystem does it have? And do you mount it manually or does it mount automatically when you plug it in?

The output of these commands while the device is plugged in should help identify the problem:
```

sudo fdisk -l
df -h
ls -ld "/media/Store N GO"

```

thanks for quick reply, the stick mounts automatically, now for some reason I'm unable to input my password at the sudo command.  I'll reboot and retry later this day.

---

### Post by glx5667 on 2008-12-09
> **glx5667 said:**
> thanks for quick reply, the stick mounts automatically, now for some reason I'm unable to input my password at the sudo command.  I'll reboot and retry later this day.

thanks for reply, I tried the chown command ad it has no effect on dicc performance.  I'll reboot, and try again later.  Thanks for taking time to help.

---

