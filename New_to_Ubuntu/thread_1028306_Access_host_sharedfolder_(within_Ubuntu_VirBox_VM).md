---
title: "Access host sharedfolder (within Ubuntu VirBox VM)?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Xarok on 2009-01-02
So I'm running an Ubuntu Virtual Machine in VirtualBox.
I installed the the extra utilities and made a shared folder.

Now how do I mount that shared folder from within Ubuntu?

(I was able to do this just fine in the XP VM by just going to adding new network locations and it showed up)

Much thanks for your help guys!

---

### Post by balaknair on 2009-01-02
I'm assuming you've already created the shared folder on the Host OS.

Within the Ubuntu VM, open a terminal, and enter

```
mount -t vboxsf *mysharedfolder* *mountpoint*
```

replace *mysharedfolder* with the name of the shared folder, and *mountpoint* with the mount point where you want to mount it(eg. /mnt/sharedfolder. You will have to create the /mnt/sharedfolder directory before mounting the shared folder).

Eg:

The shared folder I want to use- vbshare
Mount point I want to use in the Ubuntu VM- /mnt/vbs

So the commands I'll use are-

```
sudo mkdir /mnt/vbs

mount -t vboxsf vbshare /mnt/vbs
```

---

### Post by superprash2003 on 2009-01-02
sudo smbmount //x.x.x/sharedfoldername /destination/path

---

