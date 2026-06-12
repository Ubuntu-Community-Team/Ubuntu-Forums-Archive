---
title: "Corrupt microSD card... Is data recovery by myself possible?"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Baniita on 2011-05-03
Really important data to me that I lost soon before backup... Other threads don't help. And I just don't have the money to get a data recovery program, especially not a service. To have this fixed ASAP would mean a heck of a lot to me. Formatting the card is absolutely not an option, unfortunately...

It's been quite the helltastic day. More than sad, I want to hit something.

If I try to read the microSD...
```
 Unable to mount location
Error mounting: ...can't read superblock
``````
fsck.vfat -tr /dev/sdb
bash: /sbin/fsck.vfat: Input/output error
```fdisk -l
```
Disk /dev/sdb: 2040 MB, 2040528896 bytes
29 heads, 28 sectors/track, 4908 cylinders
Units = cylinders of 812 * 512 = 415744 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4909     1992580+   b  W95 FAT32
```cat /etc/fstab
```
sudo cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```df
```
Bus error (core dumped)
```disk /dev/sdb
```
Disk /dev/sdb: 2040 MB, 2040528896 bytes
29 heads, 28 sectors/track, 4908 cylinders
Units = cylinders of 812 * 512 = 415744 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4909     1992580+   b  W95 FAT32
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$ sudo cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$ disk /dev/sdb
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/ubuntu/+source/command-not-found
Please include the following information with the report:

command-not-found version: 0.2.21
Python version: 2.6.6 final 0
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick
Exception information:

[Errno 5] Input/output error
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/util.py", line 43, in crash_guard
    callback()
  File "/usr/lib/command-not-found", line 27, in main
    cnf = CommandNotFound(options.data_dir)
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/CommandNotFound.py", line 83, in __init__
    self.priority_overrides = map(string.strip, open(p).readlines())
IOError: [Errno 5] Input/output error
```...What do I do now? /Eye twitches in despair.

Thanks in advance for anybody who can be of help. ; v;')n

---

### Post by KL_72_TR on 2011-05-03
See if this can help: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) or this [http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)
Also check the Ubuntu Software Center
Next time backup your valuable data on Ubuntu One.

---

### Post by lkraemer on 2011-05-03
Baniita,
I am in the process of uploading a youtube video to the web, for you to follow.......You will need to do these things in order:

1. Install testdisk via Synaptic Package manager
2. Log out, then log back in....
3. In a Terminal, become ROOT to have the priviledges you need...
4. Insert your Media, then unmount it......
5. Run testdisk  -- Screencast starts here......
6. Make an IMAGE of your media, and save to your /home/loginuser
7. Scan for files, then copy one to /home/loginuser
8. Make a deeper scan of media
9. Copy more files as needed.
10. If you corrupt the media, you can use dd to copy the media's image
    back to the original media, and start over.

If that doesn't work you can try fsck:

To run fsck, you really need to become root, so you have permissions to
make the proper changes to correct your system, and you need to do it
on an un-mounted device, unless you are doing it in the background.....


The Ubuntu command syntax for fsck is:

 fsck [-sAVRTMNP] [-C [fd]] [-t fstype] [filesys...]  [--] [fs-specific-
       options]

REF:
man fsck



fsck -f -p -y -t vfat /dev/mysata


Also, you can keep running fsck until it comes up clean, and/or you may want to reboot, and unmount the device and run fsck again. Then try
testdisk again to copy your files.

Screencast URL (unlisted):
[http://www.youtube.com/watch?v=fikZCgbhyvk](http://www.youtube.com/watch?v=fikZCgbhyvk)

lk

---

### Post by manfromthezoo on 2011-05-03
I've had tremendous success using photorec before, albeit on a regular magnetic disk rather than a flash card (which I've never tried).

Still, it's definitely worth a try. Best of luck!

---

