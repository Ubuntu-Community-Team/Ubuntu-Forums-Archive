---
title: "Erasing Virtualbox Partitions"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-01-20
I used virtualbox to test out some other linux distros and gave each partition 8 gigs. I deleted the virtual hard disks from the virtual box menu but I still seem to be low on space. Should I have deleted the virtual hard disks another way or is it something else?

If it's not that I think it may be because I have several other versions of ubuntu installed. Is there a way to expand the main partition so that it uses everything?

Thanks

---

### Post by drs305 on 2009-01-20
I interpreted your post as giving the distros 8GB virtual partitions...

You can search for the .vdi files on your system:
```

sudo find / -name *.vdi

```

If you find them, you can delete them no matter where they reside by opening Nautilus with admin powers. *Be careful deleting things* - you can delete anything on your system, including system files:
```

gksudo nautilus

```

Don't forget to empty your Trash and root's Trash, since these large files still take up space until the trash is emptied. To find all the Trash on your system:
```

sudo find / -type d -name *Trash* 

```

---

### Post by Sup3r3g0 on 2009-01-20
Okay I was able to erase the virtual partitions, but is there any way to delete the partitions created by installing previous versions of Ubuntu? 

Thanks

---

### Post by fubbleskag on 2009-01-20
there's a partition editor:
```
gparted
```

---

### Post by drs305 on 2009-01-20
If you are talking about deleting/combining actual partitions, the most commonly-used app in ubuntu is gparted: System > Administration > Partition Editor (or gksudo gparted).

Here is a link showing how to use it:
[http://www.howtoforge.com/partitioning_with_gparted]("http://www.howtoforge.com/partitioning_with_gparted")

You can alter partitions that are unmounted (you can unmount from within gparted). Of course, to alter system partitions you would have to do it from the LiveCD or a third-party CD. Gparted is accessible from the LiveCD via the same menu.

---

### Post by Sup3r3g0 on 2009-01-20
Thanks for the help

---

