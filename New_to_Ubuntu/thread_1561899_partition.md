---
title: "partition"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by k-boy on 2010-08-26
***[SIZE=5]How can i partition my HDD???[/SIZE]***

---

### Post by skatinjj on 2010-08-26
> **k-boy said:**
> ***[SIZE=5]How can i partition my HDD???[/SIZE]***

open terminal:
```

sudo apt-get install gparted
```

After it installs, go to System > Administration > GParted

---

### Post by jtarin on 2010-08-26
With Gparted. Type the name in a terminal ```
sudo gparted 
```to see if is installed. if it is it should be in your menu.

---

### Post by -kg- on 2010-08-26
For further information on Partitioning operations, click on the "How To Partition" link in my signature block below.

---

### Post by k-boy on 2010-08-27
> **skatinjj said:**
> open terminal:
```

sudo apt-get install gparted
```After it installs, go to System > Administration > GParted
[QUOTE=k-boy]after partition the drive should appear in places menu right but i don't find it there & even the above u said (System > Administration > GParted) gparted is missing in dropdown menu

---

### Post by jtarin on 2010-08-27
> after partition the drive should appear in places menu right but i don't find it.It will only appear if you have formatted and have a filesystem on it.

---

### Post by k-boy on 2010-08-27
> **jtarin said:**
> It will only appear if you have formatted and have a filesystem on it.
[QUOTE=k-boy]in partition editor (which i find in System>Administration>partition Editor) i find this drive which says file system is fat32 & mount point is /dos

---

### Post by skatinjj on 2010-08-27
> **k-boy said:**
> [QUOTE=k-boy]in partition editor (which i find in System>Administration>partition Editor) i find this drive which says file system is fat32 & mount point is /dos

Sounds like you have a drive/partition mounted to a folder called dos on the root of your drive

---

### Post by jtarin on 2010-08-27
> **k-boy said:**
> [QUOTE=k-boy]in partition editor (which i find in System>Administration>partition Editor) i find this drive which says file system is fat32 & mount point is /dosYou will want to follow [this tutorial]("http://www.psychocats.net/ubuntu/mountwindowsfstab") for this partition to mount at boot time. The part you want is toward the bottom.

---

