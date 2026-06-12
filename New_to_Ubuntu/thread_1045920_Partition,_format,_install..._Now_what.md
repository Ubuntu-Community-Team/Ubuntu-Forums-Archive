---
title: "Partition, format, install... Now what?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by multiman on 2009-01-20
Hi there guys

I installed Gnome Ubuntu (two days ago) as my main and only OS on my PC. I had couple of problems during that and you were very helping, so thanks.

Now I have this little problem with my logic partition, it just cannot be accessed I mean I can mount it and open it without any problem, and I see a folder called "Lost and found" which reminds me with one of LOST series episodes, lol...

Back to the topic, as I said I can mount and open it, but I can't past or create any file or folder inside of it. What should I do?

Are there some magic words to write in the terminal, or is it something else?

---

### Post by Joe computer on 2009-01-20
try ```
gksudo nautilus
```

---

### Post by jerome1232 on 2009-01-20
Depends on what this partition is formated as.

If it's a linux filesystem you just need to change it's permissions to something that your user can create files in.

You can either open a root nautilus (gksu nautilus as mentioned above) and browse to this folder the partition mounted at, right click the folder, click the permissions tabs, and either make your user the owner, or just give all user read,write, execute permissions.

the terminal method for this, you would do one of the other it's up to you and how you want this drive accessed.

```
#give yourself ownership
sudo chown -R $USER: /path/to/mount-point
#give all users read/write permissions
sudo chmod -R a+rwx /path/to/mount-point
```

--edit-- forgot the rest lol

If it's a microsoft format (fat,ntfs) then it doesn't support unix style permissions and it's determined on mount time. To mount an ntfs partition with world readable/writable permissions for example:

```
sudo mount -t ntfs-3g /dev/sdxx /media/data -o umask=000
```

---

### Post by multiman on 2009-01-20
Mine is ext3 formatted, I tried the "gksudo nautilus", and I got this message:

```
hammudah@Hammudah-Monkey:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:5901): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root

(nautilus:5901): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:5901): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
Shutting down nautilus-share extension

```


I, by the way, have two partitions, one is called "Filesystem", and the other is "KaGaMo" for my files.

And, is there any other way but the terminal? lol, cause I like the direct commands, I'm very newbie to this world :)

---

### Post by jerome1232 on 2009-01-21
I'm not sure what the issue with nautilus there is but I can certainly help change ownership from the terminal.

While the disk is mounted post the output of these commands below and I can write the exact command you would need get ownership.

The first command lists out your disks and their partition tables, the second one lists out all of the currently active mounts.

```
sudo fdisk -l
mount
```

---

### Post by multiman on 2009-01-21
If this might help, a screenshot for permissions tab of my logic partition.

---

### Post by multiman on 2009-01-21
> **jerome1232 said:**
> The first command lists out your disks and their partition tables, the second one lists out all of the currently active mounts.

```
sudo fdisk -l
mount
```

This is it:
```
hammudah@Hammudah-Monkey:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b4844e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5877    47206971   83  Linux
/dev/sda2            5878        7534    13309852+  83  Linux
/dev/sda3            7535        8031     3992152+  82  Linux swap / Solaris
/dev/sda4            8032       38913   248059665    5  Extended
/dev/sda5            8032       38913   248059633+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4070    30769168+   7  HPFS/NTFS
/dev/sdb2            4071       20672   125511120    f  W95 Ext'd (LBA)
/dev/sdb5            4071       10849    51249208+   7  HPFS/NTFS
/dev/sdb6           10850       12474    12284968+   7  HPFS/NTFS
/dev/sdb7           12475       20672    61976848+   7  HPFS/NTFS
hammudah@Hammudah-Monkey:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hammudah/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hammudah)
/dev/sda5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
hammudah@Hammudah-Monkey:~$ 

```

Just forget about the NTFS partitions, I just want to copy my files from there.

---

### Post by jerome1232 on 2009-01-21
okay based on that I'm assuming the partition your trying to write to is /dev/sda5 that is formated as ext3 and mounted at /media/disk

```
sudo chown -R $USER: /media/disk
```

You can literally copy and paste that command $USER is a variable that means the "name of the user that's currently logged on".

--edit-- after running that command you should be able to copy files to the drive using nautilus as normal.

---

### Post by multiman on 2009-01-21
Done!! :)

Thank you jerome1232. You guys helped me for the third time.

I know that the word thank you is not enough, but I wish there is more I can say :)

---

### Post by multiman on 2009-01-21
Now I want to rename it to "KaGaMo", but it says it cannot be renamed. And is there a way to keep it mounted even after restarting the computer?

---

### Post by jerome1232 on 2009-01-21
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
for renaming you just need to change the label for the file-system (this works regardless of if it's a usb disk or not)

Those permissions you added will stick after a reboot.

If you want it mounted during the boot up time I wouldn't do that if it's a removable drive, at anyrate you will need to add an fstab entry to get it auto mounted during the boot up sequence.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

feel free to ask questions about the how-to's if you unsure of anything.

---

### Post by multiman on 2009-01-21
That was very helpful, thank you :)

---

