---
title: "Drives are mounted in Places Menu but actually not Mounted"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-21
Hi there.

I have 4 partitions on my Disk. i Have a triple boot of Vista , Leopard n Ubuntu and an Others drive that is FAT32.

I have got my songs n wallpapers in FAT32(Others) and used a wallpaper from it for my uBuntu Desktop. But whenever i login to the desktop that wallpaper doesnt appear i think because my drives are not mounted. The drives are available in Places menu but they are not on Desktop as when i click that Drive in Places Menu it appears on Desktop.

Somebody please explain this??

---

### Post by amingv on 2009-05-21
The drives appear as "listed" when you boot up the pc, but do not mount automatically on startup.
For them to mount automatically, you need to [add them to fstab]("https://help.ubuntu.com/community/Fstab").

If you're going to add it to fstab, make sure you make a backup of the old fstab file first.

---

### Post by raziiq on 2009-05-21
oh i m sorry, i just found these 2 commands and will try n run these, if i have any other probs i ll post.

[B]sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222[/B]

---

### Post by amingv on 2009-05-21
> **raziiq said:**
> oh i m sorry, i just found these 2 commands and will try n run these, if i have any other probs i ll post.

[B]sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222[/B]

That command is telling it to mount an ntfs drive (yours is FAT32).
Even if it worked, it will just mount it for this session, so you'd still need to modify fstab.

---

### Post by nandemonai on 2009-05-21
> **raziiq said:**
> Hi there.

I have 4 partitions on my Disk. i Have a triple boot of Vista , Leopard n Ubuntu and an Others drive that is FAT32.

I have got my songs n wallpapers in FAT32(Others) and used a wallpaper from it for my uBuntu Desktop. But whenever i login to the desktop that wallpaper doesnt appear i think because my drives are not mounted. The drives are available in Places menu but they are not on Desktop as when i click that Drive in Places Menu it appears on Desktop.

Somebody please explain this??

They're not actually mounted that's the problem. Places is just listing the drives or partitions it can see hence you needing to click on them to actually mount them.

Your best bet is to mount them on boot via the /etc/fstab file.

The lines you will need depend entirely on what file system each partition is.

An example vfat mount would be:

```
/dev/sdb1    /media/mynewdrive   vfat    defaults     0        2
```

The first bit is the device file, second the mount point and then file system type and options.

One trick you can use is to mount the drives via places first, then in terminal:

```
cat /etc/mtab
```

That will list what you have mounted where. Simply copying the relevant lines to the bottom of the /etc/fstab file should suffice though I've had problems using this method with NTFS drives.

for NTFS you want something more like this:

```
/dev/sda4 /media/wintel ntfs-3g quiet,defaults,rw 0 0
```

As for the leopard partition(s) I'm not too sure myself. I know that HFS+ is supported but it's been ages since I've needed to mount one.

If you have trouble with it, post back the output from:

```
sudo fdisk -l
```

---

### Post by raziiq on 2009-05-21
> **nandemonai said:**
> They're not actually mounted that's the problem. Places is just listing the drives or partitions it can see hence you needing to click on them to actually mount them.

Your best bet is to mount them on boot via the /etc/fstab file.

The lines you will need depend entirely on what file system each partition is.

An example vfat mount would be:

```
/dev/sdb1    /media/mynewdrive   vfat    defaults     0        2
```

The first bit is the device file, second the mount point and then file system type and options.

One trick you can use is to mount the drives via places first, then in terminal:

```
cat /etc/mtab
```

That will list what you have mounted where. Simply copying the relevant lines to the bottom of the /etc/fstab file should suffice though I've had problems using this method with NTFS drives.

for NTFS you want something more like this:

```
/dev/sda4 /media/wintel ntfs-3g quiet,defaults,rw 0 0
```

As for the leopard partition(s) I'm not too sure myself. I know that HFS+ is supported but it's been ages since I've needed to mount one.

If you have trouble with it, post back the output from:

```
sudo fdisk -l
```

Hey thanks
i ll try these and let you know if i have any problem.

---

### Post by nandemonai on 2009-05-21
> **raziiq said:**
> Hey thanks
i ll try these and let you know if i have any problem.

Just be sure to substitute your dev references and mount points with your own and not use my examples word for word ;)

---

### Post by raziiq on 2009-05-21
ya sure man n i can get my disk info using this command right?

```
sudo fdisk -l
```

---

### Post by nandemonai on 2009-05-21
> **raziiq said:**
> ya sure man n i can get my disk info using this command right?

```
sudo fdisk -l
```

Exactly ;)

---

### Post by raziiq on 2009-05-21
alright, i ll check and post back my results, thanks :)

---

### Post by raziiq on 2009-05-21
i have successfully mounted fat32 and ntfs but i cant write to ntfs

---

### Post by rob2uk on 2009-05-21
do you have ntfsprogs installed?

---

### Post by raziiq on 2009-05-21
no i dont have it installed, is it necessary to install that?
Cant i write on ntfs without any software?

---

### Post by nandemonai on 2009-05-22
> **raziiq said:**
> no i dont have it installed, is it necessary to install that?
Cant i write on ntfs without any software?

Install the NTFS drivers:

```
sudo apt-get install ntfs-3g
```


Options at the end of your /etc/fstab line for said drive should look like this:

```
/dev/sda4 /media/wintel **ntfs-3g quiet,defaults,rw 0 0**
```

---

### Post by Paqman on 2009-05-22
Instead of telling a newbie to mess around with a dangerous and confusing file like /etc/fstab, I like to point them towards pysdm. You'll find it in Applications > Add/Remove under "storage device manager".

Should be part of the default install, IMO.

---

### Post by raziiq on 2009-05-24
> **nandemonai said:**
> Install the NTFS drivers:

```
sudo apt-get install ntfs-3g
```


Options at the end of your /etc/fstab line for said drive should look like this:

```
/dev/sda4 /media/wintel **ntfs-3g quiet,defaults,rw 0 0**
```

Hey thanks man it worked, now i can write on ntfs partitions. BTW can you please explain this code

```
/dev/sda4 /media/wintel **ntfs-3g quiet,defaults,rw 0 0**
```

i can understand that /dev/sda4 and /media/wintel but i cant get the remaining part of the code. Also can you please tell me what code to use for MAC OS X? i used the code below but its not mounting.

```
/dev/sda3    /media/mac      hfsplus user,auto,file_umask=0111,dir_umask=0000
```

---

### Post by nandemonai on 2009-05-24
> **raziiq said:**
> Hey thanks man it worked, now i can write on ntfs partitions. BTW can you please explain this code

```
/dev/sda4 /media/wintel **ntfs-3g quiet,defaults,rw 0 0**
```

i can understand that /dev/sda4 and /media/wintel but i cant get the remaining part of the code. Also can you please tell me what code to use for MAC OS X? i used the code below but its not mounting.

```
/dev/sda3    /media/mac      hfsplus user,auto,file_umask=0111,dir_umask=0000
```

Fstab entries go like this:

```
[Device] [Mount Point] [File_system] [Options] [dump] [fsck order]
```

So ntfs-3g is the file system, quiet,defaults,rw the options and the last two digits the dump and fsck order (which are kind of useless here as it's a ntfs drive but needed regardless).

Extra info:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

As for HFS I'm not too sure, again it's been years since I've used it. Search the forums here about mounting hfsplus, seems a few people have it working ok.

---

### Post by raziiq on 2009-05-24
Alright, thanks man for the help, i ll check the forums for HFS mouting.

---

