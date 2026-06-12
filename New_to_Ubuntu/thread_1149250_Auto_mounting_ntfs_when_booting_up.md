---
title: "Auto mounting ntfs when booting up"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by el.norman on 2009-05-05
ok, i know how to mount partition using the terminal,

but how i make a partition (sda2) mounts automatically when i log in?

---

### Post by pastalavista on 2009-05-05
Install ntfs-3g (probably already installed), ntfs-config and pysdm.
```
sudo apt-get install ntfs-3g ntfs-config pysdm
```
pysdm is a Storage Device Manager and will be in System > Administration menu

---

### Post by iaculallad on 2009-05-05
> **el.norman said:**
> ok, i know how to mount partition using the terminal,

but how i make a partition (sda2) mounts automatically when i log in?

Or you could do it manually. Get the informations needed first before editing the /etc/fstab file.

Create your mountpoint:

```
sudo mkdir /media/NTFS_Drive
```

Get the UUID of the NTFS partition:

```
blkid
```

Then open up your /etc/fstab file for editing:

```
gksudo gedit /etc/fstab
```

And insert the line of texts below on the last part of the file.
```

**[COLOR="DarkRed"]UUID=08086C8E086C7C96[/COLOR]** /media/NTFS_Drive     ntfs    defaults,umask=007,gid=46 0       1
```

Replace UUID=08086C8E086C7C96 with the value you get from blkid.

Save and Close.

While on terminal, issue the command below:

```
sudo mount -a
```

HTH.

---

### Post by el.norman on 2009-05-05
This is what i got


ntfs-3g: Failed to access volume '/dev/disk/by-uuid/2E33698E25F690A': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.


maybe th UUID that blkid gave me was wrong. any ideas???

---

### Post by DJonsson2008 on 2009-05-05
I use a handy gui for getting a grip on ntfs drives/mapping
its in the repostitories and is called ntfs-config

---

