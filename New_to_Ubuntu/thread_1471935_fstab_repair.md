---
title: "fstab repair"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by outlaw45k on 2010-05-03
i tried to auto mount 2 of my media hdd and on the process i broken the fstab is there any automatic way to repair that ? or i better reinstall and dont lose my time

here is how the thing looks atm

/dev/sda1 /media/D ext4 default  1 1
/dev/sdc1 /media/E ext4 default  1 1
/dev/sdb1 /            ext4 default  1 2
/dev/sdb5 swap swap sw 0 0

---

### Post by GSF1200S on 2010-05-03
> **outlaw45k said:**
> i tried to auto mount 2 of my media hdd and on the process i broken the fstab is there any automatic way to repair that ? or i better reinstall and dont lose my time

What do you mean by broken your fstab? What leads you to believe it is broken?

Please post the contents of:
```
sudo gedit /etc/fstab
```
in a post here.

Also, paste the terminal output of the following two commands here in the same reply:
```
sudo fdisk -l
sudo blkid
```

Also, which two drives were you trying to mount?

---

### Post by switch10 on 2010-05-03
just remove the lines that you added...  

there may be a fstab~ (backup) file in /etc  

check this file to see if it is different than your broken fstab.  if so, just rename fstab~ to fstab:

```
sudo mv /etc/fstab~ /etc/fstab 
```

---

### Post by outlaw45k on 2010-05-03
> **GSF1200S said:**
> What do you mean by broken your fstab? What leads you to believe it is broken?

it say only root can mount the hdd
nvm i fixed this

---

