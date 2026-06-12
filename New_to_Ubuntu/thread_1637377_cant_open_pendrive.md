---
title: "cant open pendrive?"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by gmenfan83 on 2010-12-04
i searched and could not find an answer to this ...i have files on a pendrive i need to transfer to my computer but when i go to open my pendrive nothing happens .....i right click on it and mount it but still cant open after that?

---

### Post by cosine352 on 2010-12-04
Have you tried to 'cd' to the folder?

---

### Post by gmenfan83 on 2010-12-04
> **cosine352 said:**
> Have you tried to 'cd' to the folder?
im sorry im not sure as to what you mean

---

### Post by azertyh on 2010-12-04
hello,
how did you mount it?

---

### Post by cosine352 on 2010-12-04
sorry for that.
open the terminal and change directory (cd) in command line way.
The pendrive should be in the \media folder.

---

### Post by karthick87 on 2010-12-04
Plug your USB drive and then type the following commands in terminal and post the outputs here,

```
sudo fdisk -l
```                  
```
cat /etc/mtab
```

---

### Post by gmenfan83 on 2010-12-04
> **azertyh said:**
> hello,
how did you mount it?
by right clicking and selecting mount but nothing happens

---

### Post by gmenfan83 on 2010-12-04
> **karthick87 said:**
> Plug your USB drive and then type the following commands in terminal and post the outputs here,

```
sudo fdisk -l
``````
cat /etc/mtab
```
output

gmenfan83@gmenfan83-Satellite-A205:~$ sudo fdisk -]
[sudo] password for gmenfan83: 
fdisk: invalid option -- ']'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

gmenfan83@gmenfan83-Satellite-A205:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32fc1a2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       13154   104116469+   7  HPFS/NTFS
/dev/sda3           13154       19458    50635777    5  Extended
/dev/sda5           13154       19194    48520192   83  Linux
/dev/sda6           19194       19458     2114560   82  Linux swap / Solaris

Disk /dev/sdb: 2003 MB, 2003795968 bytes
32 heads, 63 sectors/track, 1941 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e7572ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1941     1956496+   6  FAT16
gmenfan83@gmenfan83-Satellite-A205:~$ cat /etc/mtab
/dev/sda5 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/gmenfan83/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=gmenfan83 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda2 /media/SQ004585V03 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
gmenfan83@gmenfan83-Satellite-A205:~$

---

### Post by gmenfan83 on 2010-12-04
> **cosine352 said:**
> sorry for that.
open the terminal and change directory (cd) in command line way.
The pendrive should be in the \media folder.
do you know thw code to change directories?

---

### Post by cosine352 on 2010-12-04
> cd /media
then 
> ls
if you see your pendrive there, then
> cd pendrive_folder

---

### Post by gmenfan83 on 2010-12-04
> **cosine352 said:**
> then 

if you see your pendrive there, then
this was my output of those commands

gmenfan83@gmenfan83-Satellite-A205:~$ cd /media 
gmenfan83@gmenfan83-Satellite-A205:/media$ ls 
SQ004585V03
gmenfan83@gmenfan83-Satellite-A205:/media$ cd pendrive_folder 
bash: cd: pendrive_folder: No such file or directory
gmenfan83@gmenfan83-Satellite-A205:/media$

---

### Post by karthick87 on 2010-12-04
```
cd /media
```
```
cd SQ004585V03
```
```
ls
```

---

### Post by gmenfan83 on 2010-12-04
> **karthick87 said:**
> ```
cd /media
``````
cd SQ004585V03
``````
ls
```
here is the output of that....i really appreciate everyones help but i still cant open it even after these commands or any other for that matter

gmenfan83@gmenfan83-Satellite-A205:~$ cd /media
gmenfan83@gmenfan83-Satellite-A205:/media$ cd SQ004585V03
gmenfan83@gmenfan83-Satellite-A205:/media/SQ004585V03$ ls
autoexec.bat       Documents and Settings      ProgramData.LOG2
$AVG               f499efffff55221215a669c358  Program Files
Boot               hiberfil.sys                $RECYCLE.BIN
bootmgr            install.dat                 scramble.log
BOOTSECT.BAK       Memeo                       setup.log
caavsetupLog.txt   MSOCache                    System Volume Information
caisslog.txt       pagefile.sys                TOSHIBA
config.sys         PerfLogs                    Users
coreuninstall.log  ProgramData                 Windows
DOCS               ProgramData.LOG1            WORKSSETUP
gmenfan83@gmenfan83-Satellite-A205:/media/SQ004585V03$

---

### Post by karthick87 on 2010-12-04
That's showing the data on your pen drive.

---

### Post by gmenfan83 on 2010-12-04
> **karthick87 said:**
> That's showing the data on your pen drive.
something funny seems to have went on because it is in media also but thats prety much everything thats on my windows side?

---

### Post by gmenfan83 on 2010-12-04
either way everytime i insert a usb stick i have to run those commands?

---

### Post by karthick87 on 2010-12-04
You can change the mount point,
[URL="https://help.ubuntu.com/community/MoveMountpointHowto"][COLOR=DarkOrange][B]
see this thread[/B][/COLOR][/URL]

---

### Post by gmenfan83 on 2010-12-04
> **karthick87 said:**
> You can change the mount point,
[URL="https://help.ubuntu.com/community/MoveMountpointHowto"][COLOR=DarkOrange][B]
see this thread[/B][/COLOR][/URL]
thank you and thank you for bearing with me ....the problem is that im so very confused with how the file in media could possibly be my pen drive ....i have a 2 gig pendrive and here is a screen shot of the properties iof the only file in media

---

### Post by cosine352 on 2010-12-04
so what happens if you click on the "PENDRIVE" ?

---

### Post by gmenfan83 on 2010-12-04
> **cosine352 said:**
> so what happens if you click on the "PENDRIVE" ?
nothing at all .......and when i right click i get an option to mount and when i try that nothing happens either..i do feel retarrted at the moment a 2 gig flash drive is getting the best of me for hours

---

### Post by karthick87 on 2010-12-04
With USB drive plugged in type the following command in terminal and post the output,

```
df -hT
```

---

### Post by gmenfan83 on 2010-12-04
> **karthick87 said:**
> With USB drive plugged in type the following command in terminal and post the output,

```
df -hT
```
here is the output..
now i notice that on the bottom line it is recognizing the drive


gmenfan83@gmenfan83-Satellite-A205:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext4     46G   13G   31G  30% /
none      devtmpfs    994M  268K  994M   1% /dev
none         tmpfs   1002M  180K 1002M   1% /dev/shm
none         tmpfs   1002M  100K 1002M   1% /var/run
none         tmpfs   1002M     0 1002M   0% /var/lock
none       debugfs     46G   13G   31G  30% /var/lib/ureadahead/debugfs
/dev/sdb1     vfat    1.9G  1.9G   38M  99% /media/PENDRIVE
gmenfan83@gmenfan83-Satellite-A205:~$

---

### Post by karthick87 on 2010-12-04
The result says that it is mounted at /media/PENDRIVE
> 
/dev/sdb1     vfat    1.9G  1.9G   38M  99% /media/PENDRIVE

---

### Post by gmenfan83 on 2010-12-04
> **karthick87 said:**
> The result says that it is mounted at /media/PENDRIVE
well i dont know what happened but since you had me type in the last command the content of my pendrive comes up when i click on it without going into media ....thanks for all the help and patience

---

