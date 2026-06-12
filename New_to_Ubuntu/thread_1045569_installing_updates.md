---
title: "installing updates"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by pafire on 2009-01-20
Need help with this error message that I recieved.

 E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version

 This is an update to Unbuntu 8.04.1 Do I need to install this update?

---

### Post by drs305 on 2009-01-20
Updates to Hardy are generally security or bug fixes since it is an LTS release. If your system is working without problems it is probably nothing to lose sleep over. On the other hand, it is a newer kernel and may provide you with some benefits. 

One thing you should probably check is your disk space, especially if you have a separate boot partition. Sometimes a backup cannot be created because there is no disk space remaining. This command will show your system partition(s) space and for that of any other mounted partitions:
```

df -h

```

---

### Post by kansasnoob on 2009-01-20
> **drs305 said:**
> Updates to Hardy are generally security or bug fixes since it is an LTS release. If your system is working without problems it is probably nothing to lose sleep over. On the other hand, it is a newer kernel and may provide you with some benefits. 

One thing you should probably check is your disk space, especially if you have a separate boot partition. Sometimes a backup cannot be created because there is no disk space remaining. This command will show your system partition(s) space and for that of any other mounted partitions:
```

df -h

```

+1!

At the very least the full output of:

```
sudo apt-get -f install
```

There could be a bunch of garbage lingering.

---

### Post by pafire on 2009-01-20
yes my system is running fine, however how can I keep this update from showing up since it will not install and it is staying on my update list as available.

---

### Post by drs305 on 2009-01-20
> **pafire said:**
> yes my system is running fine, however how can I keep this update from showing up since it will not install and it is staying on my update list as available.

Open synaptic, highlight your current kernel version (probably 2.6.24-19-generic) and then Package, Lock Version. You will not be shown updates for this kernel until you unlock it.

A different approach would be to continue to try to solve the immediate problem, but this is the answer to your request.

---

