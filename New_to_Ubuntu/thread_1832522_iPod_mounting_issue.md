---
title: "iPod mounting issue"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by Krystallynn341 on 2011-08-24
I'm very new to ubuntu and I've been trying to get my iPod to work. 
I'm using Ubuntu 10.1.
I have both GTKpod and Amarok. I put in the command sudo mkdir /media/iPod in the terminal then I added 
/dev/sdc2    /media/iPod  vfat    nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8    0 0
to my fstab. The iPod showed up in places but then when I try to open it I get an error message 
Unable to mount iPod
mount: special device /dev/sdc2 does not exist

Basically, I have no idea what to do now. If someone could please explain to me what exactly to do that'd be great.

---

### Post by fdrake on 2011-08-24
> **Krystallynn341 said:**
> I'm very new to ubuntu and I've been trying to get my iPod to work. 
I'm using Ubuntu 10.1.
I have both GTKpod and Amarok. I put in the command sudo mkdir /media/iPod in the terminal then I added 
/dev/sdc2    /media/iPod  vfat    nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8    0 0
to my fstab. The iPod showed up in places but then when I try to open it I get an error message 
Unable to mount iPod
mount: special device /dev/sdc2 does not exist

Basically, I have no idea what to do now. If someone could please explain to me what exactly to do that'd be great.

plug in your ipod and then do
```

fdisk -l

```
note:where "-l" is lowercase of "-L"
post here teh results. you probably just have assigned the wrong device name.

---

### Post by Krystallynn341 on 2011-08-24
okay so it shot back: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056    7  HPFS/NTFS

---

### Post by fdrake on 2011-08-24
> **Krystallynn341 said:**
> okay so it shot back: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056    7  HPFS/NTFS

my bad  can repeat the command using "sudo fdisk -l"
sometimes without sudo may give different results

---

### Post by Krystallynn341 on 2011-08-24
i used sudo when i did it the first time. without sudo it doesn't give me anything

---

### Post by fdrake on 2011-08-24
> **Krystallynn341 said:**
> i used sudo when i did it the first time. without sudo it doesn't give me anything

ohh pk i suppose u r using a wubi install right? your ipod does not show up in the devices. does you ipod has an "Mount as disk media" when you connect it to the pc. Check the connection options.  It's been a while that i do not use an ipod... :D

edit: what kind(generation) of Ipod do you have?

---

### Post by Krystallynn341 on 2011-08-24
okay so I'm bad at this. i have no idea if i'm using a wubi install. Also, how do i check the connection options?

---

### Post by Krystallynn341 on 2011-08-24
i have a 2g ipod touch

---

### Post by fdrake on 2011-08-24
> **Krystallynn341 said:**
> okay so I'm bad at this. i have no idea if i'm using a wubi install. Also, how do i check the connection options?

what kind of ipod

---

### Post by Krystallynn341 on 2011-08-24
2g ipod touch

---

### Post by ptn107 on 2011-08-24
The ipod is plugged into your pc when your running fdisk?

---

### Post by Krystallynn341 on 2011-08-24
yeah it is

---

### Post by fdrake on 2011-08-24
> **Krystallynn341 said:**
> yeah it is

while your ipod is plugged can you run:

```

lsusb

```
post here.


also check this thread :[http://ubuntuforums.org/showthread.php?t=1776738&page=2](http://ubuntuforums.org/showthread.php?t=1776738&page=2)

it looks to be a common issue.

---

### Post by Krystallynn341 on 2011-08-24
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:1293 Apple, Inc. iPod Touch 2.Gen
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by fdrake on 2011-08-24
ok so at least it is in the usb list.
follow the commands from the thread and check if they work

```

sudo add-apt-repository ppa:mcenery/ppa
sudo apt-get update
sudo apt-get upgrade

```
from the previous link.

---

### Post by Krystallynn341 on 2011-08-24
okay so i tried those commands and then i restarted the computer. At first it gives me the option to open the ipod with amarok and in places it lets me open my ipod like it's mounted. Then, as soon as I try to open it with amarok it goes back to giving me the mounting error message and it won't let me open the ipod.

---

### Post by fdrake on 2011-08-24
> **Krystallynn341 said:**
> okay so i tried those commands and then i restarted the computer. At first it gives me the option to open the ipod with amarok and in places it lets me open my ipod like it's mounted. Then, as soon as I try to open it with amarok it goes back to giving me the mounting error message and it won't let me open the ipod.

now run again :
```
sudo fdisk -l
```

---

### Post by Krystallynn341 on 2011-08-24
> **fdrake said:**
> now run again :
```
sudo fdisk -l
```


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056    7  HPFS/NTFS

---

### Post by fdrake on 2011-08-24
> **Krystallynn341 said:**
> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056    7  HPFS/NTFS

what version of ubuntu r u runnning ?
```

less /etc/lsb-release

```

---

### Post by Krystallynn341 on 2011-08-24
10.10

---

### Post by Krystallynn341 on 2011-08-25
I figured it out! If anyone wants to know... if you're mounting an iPod touch 2g on Ubuntu 10.10 you have to type the command:
sudo mkdir/ media/ ipod
then go into your fstab by typing the command
sudo gedit /etc/fstab
then add 
/dev/sda1 /media/iPod  vfat	nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8	0 0
to the bottom
Then type in all these commands:
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get upgradeafterwards, reboot computer and it should work.
you have to use GTKpod with the ipod touch though

---

### Post by fdrake on 2011-08-25
> **Krystallynn341 said:**
> I figured it out! If anyone wants to know... if you're mounting an iPod touch 2g on Ubuntu 10.10 you have to type the command:
sudo mkdir/ media/ ipod
then go into your fstab by typing the command
sudo gedit /etc/fstab
then add 
/dev/sda1 /media/iPod  vfat	nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8	0 0
to the bottom
Then type in all these commands:
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get upgradeafterwards, reboot computer and it should work.
you have to use GTKpod with the ipod touch though

i don't think that's possible .. you r mounting your win partition in the ipod folder. if you open the /media/ipod what files do you see?

```
ls /media/ipod
```

---

### Post by fdrake on 2011-08-25
do you have gvfs-backends installed?

```

sudo apt-get install gvfs-backends
sudo apt-get update && sudo apt-get upgrade

```
reboot and retry.

---

### Post by rrinjapan on 2011-08-25
Sorry if this is a question that I missed the answer to above ... is your iPod formatted for Mac or Windows? Don't know if that'll help much but you said that it recognized it at one point and then it wouldn't let you access it ... I had that trouble and it wasn't until I formatted it in windoze that it worked ... it wasn't a touch though so it might be different ...

---

