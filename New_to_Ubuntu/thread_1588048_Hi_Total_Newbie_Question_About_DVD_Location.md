---
title: "Hi Total Newbie Question About DVD Location"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by Megaman255 on 2010-10-04
Hi There!!

I've been using Ubuntu for a while now but mainly under the guidance of my friend.
Everything works great and I've been reading some training manuals. In there it says that 
My dvd player should be in 
/dev/dvd
 but it isn't...
In fact i can't find it anywhere.
When i put a dvd into the drive it autoloads and runs fine.
But when i check its location it says
/media/whateverthecdscalled

But i need it to be located in the dev/dvd location for dvd burning reasons
:confused::confused::confused:

any help would be greatly appreciated

Many Thanks
Will

---

### Post by andrewthomas on 2010-10-04
/dev/dvd should be a link to /dev/sr0.

What burner software are you having a problem with?

---

### Post by Megaman255 on 2010-10-04
Acidrip.
When i put a dvd in it says /dev/dvd does not exist...
But it will autorun and work fine.
Also when im using dosbox if its a game that requires a cd it wont work because i dont know where to point it to. 

Cheers for the reply

Will

---

### Post by andrewthomas on 2010-10-04
```
andrew@790Fx:~$ ls -al /dev | grep dvd
lrwxrwxrwx   1 root root           3 2010-10-04 08:30 dvd -> sr0
lrwxrwxrwx   1 root root           3 2010-10-04 08:30 dvdrw -> sr0

```

---

### Post by Megaman255 on 2010-10-04
This is what i got from that:

will@will-desktop:~$ ls -al /dev | grep dvd
lrwxrwxrwx   1 root root           3 2010-10-04 16:02 dvd1 -> sr0
drwxr-xr-x   2 root root          60 2010-10-04 16:01 pktcdvd
will@will-desktop:~$ lrwxrwxrwx   1 root root           3 2010-10-04 08:30 dvd -> sr0
lrwxrwxrwx: command not found
will@will-desktop:~$ lrwxrwxrwx   1 root root           3 2010-10-04 08:30 dvdrw -> sr0


Also i noticed from reading threads that people ask about the fstab. when i looked at other peoples they are quite long whereas mine is:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e050662c-20ef-4bce-8873-f19d947786e1 none            swap    sw              0       0
UUID=6516C76D0F91F7D7 /media/sdd1 ntfs-3g users 0 0

I dunno what that means tho...

cheers

---

### Post by andrewthomas on 2010-10-04
```
cd /dev
```

then do 

```
sudo ln -s sr0 dvd
```

and check

```
ls -al /dev | grep dvd
```

---

### Post by Megaman255 on 2010-10-04
Spot on!!
Worked a treat reading dvd now...
What did that mean just so i can at least try to understand lol:)

Thanks again 

Will

---

### Post by andrewthomas on 2010-10-04
read 

```
man ln
```

the command created a symbolic link from /dev/dvd to /dev/sr0

---

