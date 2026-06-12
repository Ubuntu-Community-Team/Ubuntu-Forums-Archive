---
title: "Need to mount Fat 32 Drives"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by StGeorge on 2008-12-05
Whenever I go to computer in 8.10 and click on one of my 5 fat 32 drives I get an unable to mount message.
When I close down the window the drive appears on the desktop and I can get into it.
Could someone tell me how to mount all my drives permanently.

---

### Post by stephanvaningen on 2008-12-05
You can add definitions in the /etc/fstab file for this. How? ... one sec...

---

### Post by nakama85 on 2008-12-05
> **StGeorge said:**
> Whenever I go to computer in 8.10 and click on one of my 5 fat 32 drives I get an unable to mount message.
When I close down the window the drive appears on the desktop and I can get into it.
Could someone tell me how to mount all my drives permanently.

Best way is to edit your fstab to do so.

This will show you all you need to know
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by nakama85 on 2008-12-05
In terminal run


```
sudo fdisk -l
```

and post the output

---

### Post by stephanvaningen on 2008-12-05
/dev/hd*[COLOR="Red"]x[/COLOR][COLOR="Blue"]y[/COLOR]* */folder/where-you-wnat-to-mount-it* vfat *options* 0 0 
[LIST]
[*]Where x is a (first disk), b (second disk), ...
[*]Where y is 0 (first partition), 1 (second partition), ...
[/LIST]
For *options*, you can enter some options, see [http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab) for possible options, possibly just option 'rw' is enough... (mounts read-write)

---

### Post by Michael.Godawski on 2008-12-05
fstab is your friend.
here some more resources:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

real life example:
[http://ubuntuforums.org/showthread.php?p=6241520](http://ubuntuforums.org/showthread.php?p=6241520)

---

### Post by StGeorge on 2008-12-05
Disk /dev/sda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ebeab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1247    10016496    c  W95 FAT32 (LBA)

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6535

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1020     8193118+  83  Linux
/dev/sdb2            1021        1149     1036192+  82  Linux swap / Solaris
/dev/sdb3            1150       14946   110824402+   f  W95 Ext'd (LBA)
/dev/sdb5            1150        3735    20772013+   b  W95 FAT32
/dev/sdb6            3736       11384    61440561    b  W95 FAT32
/dev/sdb7           11385       12393     8104761    b  W95 FAT32
/dev/sdb8           12394       14946    20506941    b  W95 FAT32

---

### Post by stephanvaningen on 2008-12-05
So start with creating 4 directories on a place where you want to mount these partitions, like i.e:
```
sudo mkdir /media/windows
sudo mkdir /media/windows/C
sudo mkdir /media/windows/D
sudo mkdir /media/windows/E
sudo mkdir /media/windows/F
```

Then edit the fstab-file:
```
sudo gedit /etc/fstab
```

and add these lines:
```
/dev/sdb5 /media/windows/C vfat ro 0 0
/dev/sdb6 /media/windows/D vfat ro 0 0
/dev/sdb7 /media/windows/E vfat ro 0 0
/dev/sdb8 /media/windows/F vfat ro 0 0
```

After saving and exiting gedit (Text Editor), re-mount the fstab:
```
sudo mount -a
```

And check if all mounts work fine by browsing to the folder(s) /media/windows/...

If all seems ok, you can edit fstab again, replace ro with rw and re-mount again with *mount -a*

---

### Post by nakama85 on 2008-12-05
:

---

### Post by Michael.Godawski on 2008-12-05
Make a backup of ths fstab file:
```
sudo cp /etc/fstab /etc/fstab_backup 
```You might have to create the mount point manually, so 
```
sudo mkdir /media/windowsx
```again change the x to a number ( just an example windows2, or whatever ountpoint you want) and create the mount point before editing the fstab file.
Add line to /etc/fstab:
```

gksudo gedit /etc/fstab
``````
/dev/sdbx       /media/windowsx  vfat    iocharset=utf8,umask=000   0       0
```Change the x to the according number from your fdisk output.

---

### Post by StGeorge on 2008-12-05
stephanvaningen
I get this on the final terminal entry:

stgeorge@stgeorge-desktop:~$ mount -a
mount: only root can do that

---

### Post by Michael.Godawski on 2008-12-05
```
sudo mount -a
```

PS:

Here is a project I started for the Education Focus Group
[http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)
it not finished yet...

---

### Post by StGeorge on 2008-12-05
nakama85

I have been going around in circles with the link you gave me I get all sorts of errors with the commands eg:

wget [http://media.ubuntu-nl.org/scripts/diskmounter--2008-12-05](http://media.ubuntu-nl.org/scripts/diskmounter--2008-12-05) 09:25:27--  [http://media.ubuntu-nl.org/scripts/diskmounter](http://media.ubuntu-nl.org/scripts/diskmounter)
Resolving media.ubuntu-nl.org... 81.171.100.21
Connecting to media.ubuntu-nl.org|81.171.100.21|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://media.ubuntu-nl.org/scripts/diskmounter/](http://media.ubuntu-nl.org/scripts/diskmounter/) [following]
--2008-12-05 09:25:27--  [http://media.ubuntu-nl.org/scripts/diskmounter/](http://media.ubuntu-nl.org/scripts/diskmounter/)
Reusing existing connection to media.ubuntu-nl.org:80.
HTTP request sent, awaiting response... 404 Not Found
2008-12-05 09:25:27 ERROR 404: Not Found.

---

### Post by stephanvaningen on 2008-12-05
> **StGeorge said:**
> stephanvaningen
I get this on the final terminal entry:

stgeorge@stgeorge-desktop:~$ mount -a
mount: only root can do that

What Michael.Godawski says is correct, just do the 'sudo mount -a' since then you '[COLOR="Blue"]do[/COLOR]' the command as the [COLOR="Blue"]s[/COLOR]uper-[COLOR="Blue"]u[/COLOR]ser (=root)

---

### Post by StGeorge on 2008-12-05
OK Guys will now to reboot to see if this works.
Will post back soon

---

### Post by StGeorge on 2008-12-05
Thanks all that worked a treat.):P

---

