---
title: "Change permission on a folder"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by TheZumm on 2009-01-25
Hi, I find this to be weird, maybe you can help me out:

I'm trying to give a folder 777-permission. In BSD, I go "chmod 777 folder_name", and that was it.

Now this happens on my Ubuntu station:
```
TheZumm$ chmod -vR 777 folder_name
mode of `folder_name' changed to 0777 (rwxrwxrwx)
TheZumm$ ll
drwxr-xr-x 3 TheZumm TheZumm 64K 2009-01-26 01:07 folder_name/

```
What is this about? Why doesn't it change the folder permissions?

Thanks,

Jenny

---

### Post by taurus on 2009-01-25
What filesystem is that *folder_name*?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by TheZumm on 2009-01-25
Worst case scenario: FAT32... Aber wie könnte es damit zu tun haben?

Jenny

---

### Post by Hobgoblin on 2009-01-26
What you are seeing is a compatibility fudge.  The permissions don't exist on FAT but for compaitibility reasons Ubuntu applies virtual permissions.

---

### Post by TheZumm on 2009-01-26
So, does that mean I do have these permissions or can't I get them? I need another user to write into this folder...

---

### Post by taurus on 2009-01-26
Did you mount that partition (folder_name) through /etc/fstab or did you mount it by hand, from a terminal?

---

### Post by TheZumm on 2009-01-27
That's another issue that's been bothering me: In my fstab it says
```
/dev/sda5       /home/TheZumm/mount_point vfat    user,auto,rw    0       0

```
But after I booted, owner of mount_point is root and I therefore do not have write permission. When I remount the disk (sudo umount mountpoint && mount mountpoint) I'm the owner and have write permission.

It seems like I messed something up here. Is my understanding of mounting disks that wrong? :-(

Jenny

---

