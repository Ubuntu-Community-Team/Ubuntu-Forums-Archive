---
title: "Restoring Grub"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by jamil_1 on 2009-11-01
I installed Ubuntu 9.10 and then upgraded Vista to windows 7. Now the defualt bootloader has been replaced and I cant login into Ubuntu.

I have tried the usual method of booting by the live CD but while trying to restore the grub when I enter 
     sudo grub
 it says that grub is not installed. I then installed the grub and issued
sudo grub
>root(hd0,0)
>setup(hd0)
can not mount the drive. Error 17.


Any help would be welcome...

---

### Post by LewRockwell on 2009-11-01
9.10 uses the new GRUB 2

not the legacy grub that you describe procedures for

you'll need to do some reading to understand how to proceed

here are the links:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

drs305 is GREAT!

kudos!

.

---

### Post by kansasnoob on 2009-11-01
> **jamil_1 said:**
> I installed Ubuntu 9.10 and then upgraded Vista to windows 7. Now the defualt bootloader has been replaced and I cant login into Ubuntu.

I have tried the usual method of booting by the live CD but while trying to restore the grub when I enter 
     sudo grub
 it says that grub is not installed. I then installed the grub and issued
sudo grub
>root(hd0,0)
>setup(hd0)
can not mount the drive. Error 17.


Any help would be welcome...

If you installed the package "grub" which is legacy grub you probably also removed "grub-pc" which is the new grub 2.

So boot your live CD (choose to try with no changes to disc) and when you get to the Live desktop post the output of these four commands:

```
grub-install -v
```

```
ls ~ /boot
```

```
ls ~ /boot/grub
```

```
sudo fdisk -l
```

---

