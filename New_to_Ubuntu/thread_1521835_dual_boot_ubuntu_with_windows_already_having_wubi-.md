---
title: "dual boot ubuntu with windows already having wubi-installed ubuntu"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by naiquevin on 2010-07-01
Hi,

I am already using ubuntu installed using wubi on windows. Now i want to set up a proper dual boot with disk partitioning and all. I would like to keep the wubi installed version for now as i dont want to loose all data, bookmarks etc (have been using it for months now). I have a query that, if i go ahead with the installation, will i be able to log in to the wubi installed version later. Just a bit curious whether my machine will show this option in the operating system selection screen during boot.

Its a 9.10 version (wubi) and will most probably installing 10.04 now
 
Thanks

---

### Post by bcbc on 2010-07-01
> **naiquevin said:**
> Hi,

I am already using ubuntu installed using wubi on windows. Now i want to set up a proper dual boot with disk partitioning and all. I would like to keep the wubi installed version for now as i dont want to loose all data, bookmarks etc (have been using it for months now). I have a query that, if i go ahead with the installation, will i be able to log in to the wubi installed version later. Just a bit curious whether my machine will show this option in the operating system selection screen during boot.

Its a 9.10 version (wubi) and will most probably installing 10.04 now
 
Thanks
You won't see an entry for the Wubi install in the initial grub2 menu, but when you select the entry to boot Windows you'll then see the Windows boot menu you're used to seeing, with entries for Windows and your wubi Ubuntu. 
So, yes, you can still boot into wubi.

If you want to you can add a a custom entry to boot the wubi from your initial grub2 menu as well. I wouldn't bother, but if it's something you want, you can do it.

Additional info:
You can also mount your wubi install from the new ubuntu if you want to copy data.
First mount the windows partition, e.g. on /media/Windows
Then loop mount the wubi install and browse:
```
sudo mount -o loop /media/Windows/ubuntu/disks/root.disk /mnt
nautilus /mnt
```

---

### Post by naiquevin on 2010-07-01
Thanks a lot. that answered quite a few questions.

---

