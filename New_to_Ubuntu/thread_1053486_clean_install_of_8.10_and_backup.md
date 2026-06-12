---
title: "clean install of 8.10 and backup"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by cosine352 on 2009-01-28
Hi friends,
I upgraded from 8.04 to 8.10 and it is not working properly. So I have decided to do a clean install. It will be really helpful to know the way of doing it such that I will be able to use the applications I have already installed and also the data I have. 

I can reinstall the applications. I am more interested in backing up the data files. 

Thanks

---

### Post by taurus on 2009-01-28
Do you have a separate /home partition or do you only have one large partition for everything?

```
sudo fdisk -l
```

---

### Post by cosine352 on 2009-01-28
one large partition for everything

> Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4866     1502077+   5  Extended
/dev/sda5            4680        4866     1502046   82  Linux swap / Solaris



---

### Post by yeats on 2009-01-28
I JUST did this a week and a half ago (though I was moving back to Kubuntu 8.04 :-) ).  If you're installing the same version, though, you can just back up your /home directory somewhere safe.  Before you do, though, make a list of your installed programs (for future reference) by doing

```

dpkg -l > installed

```
 
somewhere in your home directory.

---

