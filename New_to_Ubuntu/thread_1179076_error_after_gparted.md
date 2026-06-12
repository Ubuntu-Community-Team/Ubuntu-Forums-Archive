---
title: "error after gparted"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by cjv8888 on 2009-06-05
I just used gparted live CD to resize my / and /home partitions.  Now when I rebooted, the screen is rolling over lines with message that starting firestarter firewall has failed.  The system then boots as normal.  I then started Firestarter manually and it seems to be functioning.  Everything else seems to be working otherwise.  
Is there anything I can do or should do ?

I tried rebooting a few times and it happened every time with the same firestarter firewall failed message.

---

### Post by plucky on 2009-06-05
Post output from a terminal of ```
sudo blkid
cat /etc/fstab
``` as your UUID's have probably changed and you are getting a text message boot.

---

### Post by cjv8888 on 2009-06-05
sudo blkid
```
/dev/sda1: UUID="b334d7a0-58ce-4a3d-9d8c-5b57b1ad6270" TYPE="ext3" 
/dev/sda5: UUID="BE74E659A274FB91" LABEL="Storage" TYPE="ntfs" 
/dev/sda6: UUID="9b44b01e-46ae-441a-a8b7-4ee686c33988" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda7: TYPE="swap" UUID="9e1616ae-3361-4141-b643-bb17d09815c2" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0104" TYPE="vfat" 
/dev/sdb2: UUID="0A24A3BD24A3A9E1" TYPE="ntfs" LABEL="WinXP" 
/dev/sdb5: UUID="63EBEE86713F0B73" LABEL="E_Drive" TYPE="ntfs"
```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b334d7a0-58ce-4a3d-9d8c-5b57b1ad6270 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9b44b01e-46ae-441a-a8b7-4ee686c33988 /home           ext3    relatime        0       2
# /dev/sda7
UUID=35ee917a-fe5e-47e5-8d4a-98f37a1d9de4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=BE74E659A274FB91 /media/Storage ntfs defaults,umask=000,gid=46 0 1
UUID=0A24A3BD24A3A9E1 /media/WinXP ntfs defaults,umask=000,gid=46 0 1

```

---

### Post by plucky on 2009-06-05
I am very surprised that only your swap partition UUID seems to have changed after resizing your / and /home partitions.You should edit your fstab file and replace the UUID for the swap partition with the one given by the "blkid" command.

Also as your swap has changed then the "resume" uuid might have changed.Please post output of ```
cat /etc/initramfs-tools/conf.d/resume
``` and compare it with the swap UUID.

Good Luck

---

### Post by cjv8888 on 2009-06-05
> **plucky said:**
> I am very surprised that only your swap partition UUID seems to have changed after resizing your / and /home partitions.You should edit your fstab file and replace the UUID for the swap partition with the one given by the "blkid" command.

Also as your swap has changed then the "resume" uuid might have changed.Please post output of ```
cat /etc/initramfs-tools/conf.d/resume
``` and compare it with the swap UUID.

Good Luck

Yes, sorry I forgot to mention that before resizing the / and /home I also reduced the swap and expanded the /media/storage partition.
I am at the office at the moment.  When I get home in 8 hours, I will do the above and post back.
Thanks very much.

---

### Post by cjv8888 on 2009-06-06
I have now changed the swap uuid on the /etc/fstab
the error on boot remains though.
Here is the sudo blkid
```
/dev/sda1: UUID="b334d7a0-58ce-4a3d-9d8c-5b57b1ad6270" TYPE="ext3" 
/dev/sda5: UUID="BE74E659A274FB91" LABEL="Storage" TYPE="ntfs" 
/dev/sda6: UUID="9b44b01e-46ae-441a-a8b7-4ee686c33988" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda7: TYPE="swap" UUID="9e1616ae-3361-4141-b643-bb17d09815c2" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0104" TYPE="vfat" 
/dev/sdb2: UUID="0A24A3BD24A3A9E1" TYPE="ntfs" LABEL="WinXP" 
/dev/sdb5: UUID="63EBEE86713F0B73" LABEL="E_Drive" TYPE="ntfs" 

```
cat /etc/initramfs-tools/conf.d/resume
```
RESUME=UUID=35ee917a-fe5e-47e5-8d4a-98f37a1d9de4
```

---

### Post by cjv8888 on 2009-06-06
Noticed that the resume uuid is still the old one.
Should I edit the resume file to the new swap uuid as well?

---

### Post by plucky on 2009-06-06
> **cjv8888 said:**
> Noticed that the resume uuid is still the old one.
Should I edit the resume file to the new swap uuid as well?

Yes and then run in terminal ```
sudo update initramfs -u -k all
``` to update the kernel and you should be good to go.

Good Luck

---

