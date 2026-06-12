---
title: "External Fat32 Permissions Problem"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by alexironaek on 2009-09-14
hey , even thought i am an old member i am actually new with ubuntu and i 've got the following problem ,i bought a 400gb external usb/e-sata hdd and there is no way i can write to the hdd , i spent all the afternoon without any luck... i 've tried "storage devise manager" but there is no option for permissions , if i try changing the permission as a route it still does not let me... i've tried editing the fstab too but i do not know what to do in there :P , according to partition editor the usb drive is on /dev/sdc .

here is the content of my fstab: 
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ac241e99-6d80-441e-b548-ba6ebec13e6f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3cd59dbe-18da-4bb1-914d-8bb404dd5adb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=FC5426365425F3D4 /media/sdb1     ntfs-3g   defaults,umask=000,uid=1000, 0       1

```

ps: i am using fat32 because i also use the drive on my ps3

---

### Post by NoaHall on 2009-09-14
Are you by any chance trying to copy files larger than 4GB?

And you need to set it as "rw" in fstab.

---

### Post by alexironaek on 2009-09-14
thanks for the quick reply 
no i do not , i know that fat32 does not let you do that...
i've tried to set it as "rw" too , not luck

---

### Post by oldfred on 2009-09-14
You said it was FAT32 but you have an entry for NTFS? 

My ntfs & my fat entry
# Entry for /dev/sda1 :
UUID=04B05B70B05B6768 /media/cdrive ntfs-3g defaults,locale=en_US.UTF-8 0 0
# Entry for /dev/sdc8 :
UUID=F6A6-705D /media/gdrive vfat user,auto,fmask=0111,dmask=0000 0 0

---

### Post by ajgreeny on 2009-09-14
You should not need to add anything to fstab in order to get the fat32 disk to mount and be read/write enabled, if I remember correctly, as usb disks mount automatically, and as they do not have permission attributes enabled, you should be able to write to it.  However, if that is not correct, you can make yourself the owner of the mount folder in /media that the disk mounts to and then you should not have a problem.

Try ```
sudo chown alex:alex /media/mountfolder
```but change the line to your own username and mount point first.

---

### Post by bodhi.zazen on 2009-09-14
First, you can not change the ownership and permissions with FAT using chown or chmod.

Ownership and permissions are set at the time of mounting.

In general you do not need an entry in /etc/fstab for removable devices.

Second your line is a tad off. You have:

> # /dev/sdb1[FONT=monospace]
[/FONT]UUID=FC5426365425F3D4 /media/sdb1     ntfs-3g   defaults,umask=000,uid=1000, 0       1

I would change that to :

```
# /dev/sdb1[FONT=monospace]
[/FONT]UUID=FC5426365425F3D4 /media/sdb1 vfat   umask=000,uid=1000,users 0 0
```And remount the device

If you wish to fine tune it, use dmask=000,fmask=111

---

### Post by alexironaek on 2009-09-14
my mistake i did not mention that the ntfs shown in my /etc/fstab is my other drive that is working.i ve' tried oldfred's entry with my mount point of course and now it's working perfectly , thanks mate , and i wanna thank everyone who answered ;-);-) , one more question though , is there a tutorial about fstab , because i still don't get it :( , i know that i can search on google but i would like someone of you guys to recommend me one :P:P

---

### Post by oldfred on 2009-09-14
Glad I could help. Sometimes my suggestions do not work as well.
some more info on fstab:

see this for fstab info:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by swerdna on 2009-09-14
[HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubufat32.html")

---

