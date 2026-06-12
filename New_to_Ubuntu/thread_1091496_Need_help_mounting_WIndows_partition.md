---
title: "Need help mounting WIndows partition"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Mazza558 on 2009-03-09
I added the drive to fstab with all the correct options, and put the mount point as /media/disk, except when I restarted it told me /media/disk didn't exist. I created the folder and then tried to mount the drive manually, but it told me /media/disk/ still didn't exist. I then removed the information from fstab and mounted, but it mounted it at /medis/disk-1 instead. 

What should I do?

---

### Post by kestrel1 on 2009-03-09
Post the line that you entered in fstab.

---

### Post by drs305 on 2009-03-09
As you discovered, /media/disk is one of ubuntu's *automatic* mount points. If it already exists, ubuntu will try to mount at /media/disk-1. It probably should have worked anyway, but I would recommend you make a mount point with a different name, such as *windows*. The standard location is /mnt for permanent drives and /media for removable drives, but that is up to you.

You can easily add the entry automatcially to fstab using ntfs-config. Add it with synaptic and then run it via System Tools, NTFS Configuration Tool.

Alternatively, you can do it yourself, but it takes a bit more work on your part. Make the mount point. You can make yourself the owner, which I recommend, but it isn't really necessary since the ownership is determined at mounting for ntfs file systems.
```

sudo mkdir /media/windows
sudo chown -R *yourusername:* /media/windows  # example:  sudo chown -R john: /media/windows
chmod 755 -R /media/windows

```

Once you have created the mount point try adding your old entry into fstab with the revised mount point and see if it now works. If it doesn't, give us the error messages.

---

### Post by Mazza558 on 2009-03-09
> **drs305 said:**
> As you discovered, /media/disk is one of ubuntu's *automatic* mount points. If it already exists, ubuntu will try to mount at /media/disk-1. It probably should have worked anyway, but I would recommend you make a mount point with a different name, such as *windows*. The standard location is /mnt for permanent drives and /media for removable drives, but that is up to you.

You can easily add the entry automatcially to fstab using ntfs-config. Add it with synaptic and then run it via System Tools, NTFS Configuration Tool.

Alternatively, you can do it yourself, but it takes a bit more work on your part. Make the mount point. You can make yourself the owner, which I recommend, but it isn't really necessary since the ownership is determined at mounting for ntfs file systems.
```

sudo mkdir /media/windows
sudo chown -R *yourusername:* /media/windows  # example:  sudo chown -R john: /media/windows
chmod 755 -R /media/windows

```

Once you have created the mount point try adding your old entry into fstab with the revised mount point and see if it now works. If it doesn't, give us the error messages.

Thanks, I'll try the automatic method once I finish installing KDE4.

---

