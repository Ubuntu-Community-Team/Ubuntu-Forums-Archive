---
title: "My FAT32 Partition does not mount in ubuntu. Help needed!"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Alibix on 2010-02-14
So I had an accident with my windows installation on my net book while I was traveling, and the only backup I had was a usb stick with ubuntu on it.

So I installed Ubuntu, finally got everything up to date, and then sat down to handle my real problem, accessing my Fat32 internal HDD partition. I have read through a bunch off off tutorials on how to do it, and I`m at a loss now. I can not install Windows again, as windows will not recognize the hdd and will not install unless I Format my whole HDD, including all off my photos.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   5  Extended
/dev/sda3            3825       19456   125564008+   b  W95 FAT32
/dev/sda5               1        2711    21776044+  83  Linux
/dev/sda6            2712        2833      979933+  82  Linux swap / Solaris
/dev/sda7            2834        2955      979933+  83  Linux
/dev/sda8            2956        3824     6980211   83  Linux
aleksander@aleksander-laptop:~$ sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=100,umask=000 /dev/sda3 /media/fat_partition
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Using the df -h command :
aleksander@aleksander-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              21G  3.2G   17G  17% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  104K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  168K  497M   1% /dev
tmpfs                 497M  384K  496M   1% /dev/shm
lrm                   497M  2.2M  495M   1% /lib/modules/2.6.28-18-generic/volatile
/dev/sda7             942M   56M  839M   7% /boot
/dev/sda8             6.6G  4.6G  1.7G  74% /home


For some reason I can`t seem to mount my partition, or Ubuntu can`t read it, I remember something in the installation about enabling the partition, I unchecked this option, but I am unsure if that has anything to do with it.
I got all my photos and documents on the partition I am trying to access, so I can not format it. My goal is to save my files somehow, Format the partition and keep Ubuntu because although I am still a rookie I like it. :D

So in short, I know my files are there, I just can`t read them or mount the partition.
Any suggestions?

Thanks for all the help in advance,
Cheers, 
Aleksander.

---

### Post by Mustard on 2010-02-14
Which version of Ubuntu are you using atm?

---

### Post by Alibix on 2010-02-14
I installed 9.4, but I just did a full update, so right now I would guess 9.10 or the newest version available.

---

### Post by Kyugetsuki on 2010-02-14
Please specify your ubuntu version, 'flavor' and hardware, if possible.

---

### Post by jken146 on 2010-02-14
What happens when you use mount without all the options?
```
sudo mount /dev/sda3 /media/foo
```

---

### Post by Alibix on 2010-02-14
sudo mount /dev/sda3 /media/fat_partition
mount: you must specify the filesystem type.
Would this suggest that the file system is corrupt?
I don`t really know what "flavor" of  Ubuntu I have sorry.

---

### Post by jken146 on 2010-02-14
Alright. How about ```
sudo mount /dev/sda3 /media/fat_partition -t vfat
```?

---

### Post by Girya on 2010-02-14
try sudo mount -t vfat /dev/sda3 /media/fat_partition

---

### Post by Alibix on 2010-02-14
aleksander@aleksander-laptop:~$ sudo mount /dev/sda3 /media/fat_partition -t vfat
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And the other one :

aleksander@aleksander-laptop:~$ sudo mount -t vfat /dev/sda3 /media/fat_partition
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by jken146 on 2010-02-15
Looks like there might be something wrong with the FAT filesystem on the partition. You could run ```
sudo fsck.vfat /dev/sda3
``` to find and fix problems.

---

### Post by Alibix on 2010-02-15
I ran the code, and what came up was :
aleksander@aleksander-laptop:~$ sudo fsck.vfat /dev/sda3
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
Logical sector size is zero.
Does that mean the Partition is broken?

---

### Post by Alibix on 2010-02-15
Bump, thanks for all the help so far, but I still haven`t found the solution to my problems.

---

### Post by mikechant on 2010-02-16
Assuming your partition is corrupt (and as it's not recoverable by fsck) you might want to look into 'testdisk' (search this forum for refs). I haven't used it myself but lots of people recommend it for data recovery.

---

### Post by mikechant on 2010-02-16
Also you might want to look at this:
[http://ubuntuforums.org/archive/index.php/t-179057.html](http://ubuntuforums.org/archive/index.php/t-179057.html)
If you read through to the end it does have a (rather tricky) method using dd in Linux which might fix your partition. Or you could try mounting the disc in a USB enclosure and plugging into someone else's windows box and following the microsoft instructions referenced in the same thread.

---

### Post by mikechant on 2010-02-16
Here's another link about copying sector zero from sector 6 to fix the "Logical sector size is 0" error. This one looks a bit better explained.
[http://www.mycomputingart.com/hardware/z24.recover-sector-problem.html](http://www.mycomputingart.com/hardware/z24.recover-sector-problem.html)

---

