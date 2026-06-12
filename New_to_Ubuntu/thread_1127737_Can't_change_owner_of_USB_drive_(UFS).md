---
title: "Can't change owner of USB drive (UFS)"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by techno-wiz on 2009-04-16
I have a drive that was formatted in UFS in a freenas system. I've redone my NAS using openfiler and trying to get the data off this drive. I've connected it to my desktop with a USB adapter cable and have mounted the drive successfully.

The problem is some of the movie folders I get access denied when trying to copy them. Permissions shows "21" as owner with create and delete rights and "root" group with access rights. Others have access rights.

I want to take ownership and change the permissions so I can copy everything. Have done sudo chown -R <username> movies on my movies folder and it seems to run but says the filesystem is read-only and nothing changes. Same thing happens if I use the GUI running nautilus from sudo gksu.

Is there a way I can get past this permissions issue to copy my data?

---

### Post by llamabr on 2009-04-16
Have you also been plugging this thing into a windows box?

I understand that neglecting to properly unmount from the windows box will leave the filesystem read only.

If so, properly unmounting from your ms box might fix the problem.

---

### Post by steve101101 on 2009-04-16
try chown command

---

### Post by techno-wiz on 2009-04-16
As noted in the original post I've tried chown but it doesn't work because it sees the filesystem as read-only. This drive has never been connected to a windows system.

---

### Post by techno-wiz on 2009-04-17
I mounted the drive using:

```
sudo mount -r -t ufs -o ufstype=ufs2 /dev/sdb1 /mnt
```

Thinking maybe I needed to mount a directory I owned I rebooted and mounted the drive to /home/user/media. It is still read only though which prevents me from taking ownership. I've tried remounting with the rw option but it didn't change anything. Are permissions unsupported for the UFS filesystem?

---

### Post by techno-wiz on 2009-04-17
Still haven't figured this out.

---

