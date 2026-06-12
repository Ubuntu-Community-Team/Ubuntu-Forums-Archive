---
title: "Ubuntu 8.10 does not see DVD drive"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by apartmentDweller on 2009-02-03
So I took apart my laptop to clean out some dust. But then when I put it back together and booted to Ubuntu, my dvd drive went missing....

I am able to boot from a DVD, so I know the drive is connected....

How you get my drive back?

---

### Post by 73ckn797 on 2009-02-03
> **apartmentDweller said:**
> So I took apart my laptop to clean out some dust. But then when I put it back together and booted to Ubuntu, my dvd drive went missing....

I am able to boot from a DVD, so I know the drive is connected....

How you get my drive back?


Read the following link and follow the instructions.
[https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting)

Also go to Applications/Accessories/Terminal. From there enter the following command and see if the CD is recognized:

```
sudo fdisk -l
```

Also enter:
```
sudo lshw -C disk
```

All of this is covered in the first link.

---

### Post by 73ckn797 on 2009-02-03
The following will be your friend if you use it:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

