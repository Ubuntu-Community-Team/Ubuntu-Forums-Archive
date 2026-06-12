---
title: "Messed up mounting ntfs drive"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by littlegreenman on 2009-01-30
Hello,

I have Ubuntu Intrepid. I mounted my ntfs drive, named "Disco_K". I mounted it no problem. Until I messed up in the preferences of the mounted disk.

And now when I try to mount it I get this error:

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

:(

can you help me mount the partition again?

------

PS-this is what i find annoying about linux. it is not noob-safe :( I wish it would tell me everytime i try to do something stupid: "hei moron... stop that!" :p

---

### Post by taurus on 2009-01-30
See if you can still mount it from a terminal.  What's the output of this command?

```
sudo fdisk -l
```

---

### Post by littlegreenman on 2009-01-30
hello taurus,

thanks for the quick reply. here it is:

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8237893

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080       20023   112005180    5  Extended
/dev/sda5           19206       20023     6570553+  82  Linux swap / Solaris
/dev/sda6            6080       19205   105434532   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a2c8284

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312568832    7  HPFS/NTFS
```

---

### Post by Ben Page on 2009-01-30
I had the same problem, I edited the path manually in the preferences. You made a syntax error and now you can't mount the partition. To mount it, use terminal command:

mount /dev/sda* (* is for the number of your partition, witch you will know when you do in terminal what taurus wrote, find out the number of the partition, mount it, and then undo the changes you have made to the partition via GUI.

---

### Post by littlegreenman on 2009-01-30
hello ben page,

thank you for your reply. unfortunatelly no luck:

```
littlegreenman@ubuntu:~$ mount /dev/sdb1 
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
```


/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dff68513-909c-4396-9b94-d2064edfd750 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2f35e256-8bd0-4d71-9d33-7c2756bc9f99 /home           ext3    relatime        0       2
# /dev/sda5
UUID=d996abf5-48b9-4446-9ddd-67e583b3bd88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

/etc/mtab:
```
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda6 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/littlegreenman/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=littlegreenman 0 0
tmpfs /lib/modules/2.6.27-11-generic/volatile tmpfs rw,mode=0755 0 0
```

---

### Post by kansasnoob on 2009-01-30
I use ntfsprogs:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

I see their website is down at the moment, but ntfsprogs is available in synaptic as are the "man" pages.

---

### Post by taurus on 2009-01-30
Try something like

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by Ben Page on 2009-01-30
Littlegreenman, I can see that there is a syntax error in the error message you got after typing dev/sda, you typed mount /dev/sd**b**.
How is your partition big (that one you are trying to mount)? This can help me locate the number...
Never mind that, I see it now, I made a mistake. probably taurus's code will work, try that one

---

### Post by littlegreenman on 2009-01-30
Thanks taurus. The drive is mounted!

```
Sistema de Ficheiros            Tamanho Utilizado disponível Use% Montado em
/dev/sda1              46G  2,6G   41G   6% /
tmpfs                 1,3G     0  1,3G   0% /lib/init/rw
varrun                1,3G  116K  1,3G   1% /var/run
varlock               1,3G     0  1,3G   0% /var/lock
udev                  1,3G  3,0M  1,3G   1% /dev
tmpfs                 1,3G  104K  1,3G   1% /dev/shm
lrm                   1,3G  2,0M  1,3G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6              99G  218M   94G   1% /home
tmpfs                 1,3G  2,0M  1,3G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             299G  165G  134G  56% /media/sdb1

```

Thank you all! man, the support in this forum is great. it's almost as calling a helpline! the difference is that in here you help, and there is no annoying message saying, press 1 for this... press 2 for that...

---

### Post by Ben Page on 2009-01-30
...and you can download app called NTFS configuration tool (NTFS-config) witch will help you mount your partitions at startup if you like to.

---

### Post by littlegreenman on 2009-01-30
cool ben page, yes i wanted to do that.

i will try that tool. 

how do i close this post to SOLVED?

---

### Post by drs305 on 2009-01-30
> **littlegreenman said:**
> how do i close this post to SOLVED?

Normally it is done via the *Thread Tools* link to the top right of the original post. This feature has been temporarily disabled while the ubuntu folks work on the server. I believe you can edit the title to include the word "Solved" if desired by hitting "Edit" and then hitting the "Edit" button a second time after the original post opens for editing.

---

### Post by littlegreenman on 2009-01-30
> **Ben Page said:**
> ...and you can download app called NTFS configuration tool (NTFS-config) witch will help you mount your partitions at startup if you like to.

it doesn't work. all it does is set permissions to write on the ntfs partition... how can i set it to mount automatically upon start-up?

---

### Post by taurus on 2009-01-30
You probably need to unmount it first before you run ntfs-config.

Otherwise, you can edit it hand with

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ntfs-3g   defaults,**locale=en_US.UTF-8**   0   0
```
Save it and close down gedit.  Then, reboot.

p.s.  Change the **locale** to whatever you want to.

---

### Post by Sinsinnati on 2009-02-01
...tayloring?! Even under the auspices of Websterian lexicography... I could've sworn the name worked like "Smith". My apologies to the King's and whosoever else's English.

---

### Post by Sinsinnati on 2009-02-01
I don't know the file system but I'm pretty sure the answers that lead this concise thread to be "Solved" would require little tailoring to my situation:

I use SDHC cards as external storage for my netbook and edited the latest (with all of my school stuff;)) to have the mount point "/media/Christian", thinking I could rename it. In hindsight it seems the naming might have been redundant if not all together better sans '/(s)'... Anyone have a quick revision to offer?

Also, I tried to follow the conversation and could use help deleting (with root privileges) the directories created under "/media".

---

### Post by drs305 on 2009-02-02
> **Sinsinnati said:**
> Also, I tried to follow the conversation and could use help deleting (with root privileges) the directories created under "/media".

You can open your file browser with admin privileges and delete any folders you wish. [COLOR="Red"]CAUTION[/COLOR]: While running this with "gksudo" you can delete *any* folders/files, including system folders. Make sure you know which ones you are deleting. Also, **before deleting any /media folders, make sure the folder you want to delete does not have a  device mounted to it (i.e. make sure the folder is empty) or you will also delete the contents of the mounted device**.

```

gksudo nautilus /media

```

I label my cards so when they mount they are mounted to /media/<labelname>. Since each file format seems to have a different command for labeling, I usually just do it via *gparted*'s "Partition" > "Label" command.

---

### Post by Sinsinnati on 2009-02-02
Yeah. I did just that (only with sudo as opposed to gk~). Thanks! I'd ask about the difference but I'd digress.

Also, I used 'Disk Manager' to force-mount the misnamed Micro SD card. Though I have a few extra repositories enabled, I think it's readily available through the "Add/Remove..." GUI for Synaptic.

---

