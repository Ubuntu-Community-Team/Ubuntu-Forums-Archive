---
title: "fstab help"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by jquis8411 on 2010-10-14
I have read maybe 20-30 how to's and for the life of me I cant write an fstab entry that works. What I was hoping to do was have   ```
    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       33853    83886080   83  Linux

```   

 mount on /mnt/sda1 at start up. its an ext4 file system on a second internal HDD and I have the uuid but for some reason I just cant figure it out. I have already made a directory and I can manually mount it, I just cant get it to mount at startup. TY

---

### Post by Elfy on 2010-10-14
```
UUID=longnumberstring /mnt/sda1 [COLOR="Red"]ext4[/COLOR] defaults 0 2
```

add it to fstab  - ```
gksudo gedit /etc/fstab
```

making sure the drive is unmounted do ```
sudo mount -a
``` to check

If the drive is not formatted to ext4 use whatever suits.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by CharlesA on 2010-10-14
Fstab is.. complicated.

I'd suggest using the UUID instead of the name of the device.

One of my entries looks like this:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

UUID=05c730b5-680d-4d33-8e2e-76947d7a93fa       /array  ext4    defaults 0      0

```

EDIT: piskie beat me to it. :)

---

### Post by jquis8411 on 2010-10-14
Thanks guys, much better than what I had. I think I got into trouble figuring out what specific info I needed to enter because my entry was a mess, but Im rolling now .TY 

edit: It also helps to have no space between UUID= and the hex numbers : )

---

