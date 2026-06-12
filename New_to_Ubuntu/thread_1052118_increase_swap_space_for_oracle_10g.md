---
title: "increase swap space for oracle 10g"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Binny88 on 2009-01-27
I want to install Oracle 10g database in ubuntu 8.04 hardy heron,All the dependencies were satisfied bit it failed to install because it requires about 1024 mb of swap space whereas i have only about 450mb
How can i increase the swap space. I dualboot xp & ubuntu onmy 80gb harddrive & ubuntu takes up about 14 gb  & the rest is windows.
P.s. I have it as a debian package.

---

### Post by Tim Sharitt on 2009-01-27
You can boot into a LveCD and run the GParted (System > Administration > Partition Editor) and shrink either your windows or Linux partition to expand your swap partition.

Or, you can create a swap file and avoid messing with your partition layout and the risks that go with it. To make a swap file, use the following steps.

Create the swap file
```
sudo dd if=/dev/zero of=/mnt/1024Mb.swap bs=1M count=1024
```

Format swap file for use
```
sudo mkswap /mnt/1024mb.swap
```

Activate the swap
```
sudo swapon /mnt/1024mb.swap
```

Add the swap file to /etc/fstab. First open an editor
```
gksudo gedit /etc/fstab
```

Then add the following line to the end
```
/mnt/1024Mb.swap  none  swap  sw  0 0
```

---

