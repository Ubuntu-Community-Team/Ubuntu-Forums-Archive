---
title: "Troubles with fstab"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by kyeh on 2009-05-01
I'm trying to make my computer mount a second hard drive and swap (i accidentally formatted it to something else on gparted and hasn't been working since...) during boot. However it's not doing anything!

I've been reading a few guides about how to fstab but i still have no idea why mine's not working! It's getting really annoying that i have to mount these two things manually each time..

What i need the computer to do at boot is,

1) Mount swap (/dev/sda2)

2) Mount a second hard drive (/dev/sdb1),
filesystem = ext3,
mount location = /media/SEAGATE_1.5TB_HDD
The permissions of this mount needs to be read/writable to anyone

Section of my /etc/fstab file, not relevant parts removed
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda2
UUID=6820d9d5-5d36-4644-a732-cbafafd57d8f none            swap    sw              0       0
/dev/sdb1       /media/SEAGATE_1.5TB_HDD        ext3    auto,user,fmask=0111,dmask=0000 0       0

```

---

### Post by Bölvaður on 2009-05-01
> **kyeh said:**
> 
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#/dev/sda2 &#8592; comment out or replace for the uuid
UUID=6820d9d5-5d36-4644-a732-cbafafd57d8f none            swap    sw              0       0
/dev/sdb1       /media/SEAGATE_1.5TB_HDD        ext3    relatime        0       2

```

then change the permissions and owner of the directory sdb1 is mounted to
```

sudo chown kyeh /media/SEAGATE_1.5TB_HDD
chmod 766 /media/SEAGATE_1.5TB_HDD 
```

change accordingly to your needs... perhaps you dont want to give all other users close to full access to that partition...

---

### Post by kyeh on 2009-05-03
The second hard drive is now automounting, thanks!

However swap is still not mounting :confused:

---

### Post by logos34 on 2009-05-03
> **kyeh said:**
> 
However swap is still not mounting :confused:

If you also formatted swap, then the uuid has changed.

Check

sudo blkid

against swap line in fstab

And/or try the [troubleshooting steps]("https://help.ubuntu.com/community/SwapFaq#Troubleshooting") here (-> 2.2)

---

### Post by kyeh on 2009-05-03
Indeed, i checked the uuid and it was different. So now i have changed the uuid on fstab to reflect the changes and it now works perfectly!

Thanks a lot guys. :popcorn:

---

