---
title: "dual booted: How can I mount Windows &quot;OS&quot; partition permanently?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by MikeBrown on 2009-01-21
I have dual booted Windows Vista and Ubuntu 8.10 (which is a really big achievement for this Linux n00b who broke a computer trying to do this previously). But I digress. 

I use my Linux install much more often than my Vista install (actually I only have the MS boot around still for the few progz and games I can't run in the Linux boot) and mount the "OS" partition to save files to my Windows partition if I ever need them in Windows. 

The problem is that I have created a link to these files on the other partition that breaks at startup because I haven't mounted the "OS" partition yet for that session. 

How can I keep the OS partition mounted permanently?

I can provide screens if needed. Thanks for the help in advance!

---

### Post by drs305 on 2009-01-21
Install and run ntfs-config. It will automatically add an entry in fstab for an ntfs partition. ntfsprogs are utilities that might come in handy down the road:

```

sudo apt-get install ntfs-config ntfsprogs

```
Run with: Applications, System Tools, NTFS Configuration Tool
or: 
```

sudo ntfs-config

```

Select the device (sdXX). Next it will ask for a mount point, which will be placed in /media, and you tick to enable write support for internal/external devices.

It adds the fstab entry and you should be done.

---

### Post by MikeBrown on 2009-01-21
Thanks! I think that did it! 
I'll let you know if it works after a reboot after I check later.

If I want to change any settings (such as mount point), how would I go back and do so?

---

### Post by drs305 on 2009-01-21
> **MikeBrown said:**
> Thanks! I think that did it! 
I'll let you know if it works after a reboot after I check later.

If I want to change any settings (such as mount point), how would I go back and do so?

To change the mount point, first make a new mount point and make yourself the owner. Technically the second step isn't required for ntfs since the owner is whoever mounts it. But it will come in handy should you ever mount an ext3 partition to it.
```

sudo mkdir /media/yournewmountpoint
sudo chown -R yourusername:yourusername /media/yournewmountpoint   # makes you owner
chmod -R 755 /media/yournewmountpoint   # sets permissions

```

Then edit /etc/fstab and change the mount point:
```

sudo cp /etc/fstab /etc/fstab.bak  # back it up
gksudo gedit /etc/fstab

```
Change the mount point name in the appropriate line, then save.
Test it with:
```

sudo mount -a

```
You shouldn't see any messages regarding that device if everything is correct.

---

