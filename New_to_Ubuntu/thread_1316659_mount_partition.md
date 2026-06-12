---
title: "mount partition"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by MelDJ on 2009-11-06
i have installed ubuntu on an ext4 partition. now my computer dual boots ubuntu and vista which is on a ntfs partition. 

so, how do i mount that partition at startup? 
and how do i remove the partition's icon from my desktop
i tried finding ways, but nothing helped

---

### Post by Bunnybugs on 2009-11-06
you have to mount these disks manually...

you can add a diskmounting tool to you taskbars...

just rightclick on a bar>Add to Panel>Disk Mounter

that will do the job... but, don forget that you can open the disk where you installed Ubuntu, (in case you used Wubi.exe)

---

### Post by dharanitharan on 2009-11-06
by click alt+f2 open the run terminal and type gconf-editor. aft that in desktop section select apps n then nautilas and uncheck the volumes shown

---

### Post by dvlchd3 on 2009-11-06
Create a mount point
```

sudo mkdir /media/windows

```

Find your ntfs partition's device.  (i.e. /dev/sda1)

```

sudo fdisk -l

```

Edit fstab

```

sudo gedit /etc/fstab

```

Add this line to the bottom (replacing /dev/sda1 with your partition)

```

/dev/sda1 /media/windows ntfs-3g user,defaults 0 0

```

Mount everything in fstab

```

sudo mount -a

```

---

### Post by Teber on 2009-11-06
i too can mount my ntfs partition only manually, which is fine with me. to unmount i right click on its icon and select unmount.

wow! this forum is awesome! some guys gave great answers!

---

### Post by dharanitharan on 2009-11-06
post the output of the command:
sudo fdisk -l

---

### Post by SunnyRabbiera on 2009-11-06
Me I never needed the commandline to mount the windows drive, I was able to do it with PySDM.

---

### Post by alien8predator on 2009-11-06
check this thread:

[http://ubuntuforums.org/showthread.php?t=1886](http://ubuntuforums.org/showthread.php?t=1886)

---

### Post by MelDJ on 2009-11-06
thank you   [dvlchd3 ]("http://ubuntuforums.org/member.php?u=295128")
it worked.

now to remove the icon from the desktop
[]("http://ubuntuforums.org/member.php?u=295128")

---

### Post by cosine352 on 2009-11-06
> **dvlchd3 said:**
> create a mount point
```

sudo mkdir /media/windows

```

find your ntfs partition's device.  (i.e. /dev/sda1)

```

sudo fdisk -l

```

edit fstab

```

sudo gedit /etc/fstab

```

add this line to the bottom (replacing /dev/sda1 with your partition)

```

/dev/sda1 /media/windows ntfs-3g user,defaults 0 0

```

mount everything in fstab

```

sudo mount -a

```

+1

to remove the drive icon
[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

---

### Post by MelDJ on 2009-11-06
thanks cosine352. it worked. 
thank you all for taking time to help.:D

---

### Post by wirepuller134 on 2009-11-06
If you set the partition to mount in /mnt instead of /media it will not show the icon on the desktop and you can leave the icons enabled for usb drives so fourth.

---

### Post by The Funkbomb on 2009-11-06
If it's a partition or a drive physically in the computer, I much rather create a mount point and permanently mount the partition/drive.  I also prefer that the drive not show up on the desktop so use the /mnt/ directory.

---

