---
title: "mount points"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by DarinB on 2010-02-19
using LM 8 Karmic 32bit build
i created a separate partition for some personal files. 
after several attempts to use storage device manager i did the following and this is the entry in fstab: i made the entry bold and bigger 
my question is 
1. it mounts well but i have in my /media folder two mount point that were created with the storage device manager 
2. can i remove them????
and is the below entry correct????
darin@darin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sda5 during installation
UUID=14612f17-2d0c-47ad-8ef8-a7f4d3f8a4fa  /               ext4         errors=remount-ro         0  1  
# /home was on /dev/sdb1 during installation
UUID=6f0e63aa-b4ae-4c1c-90dc-1507ae8a0aa7  /home           ext3         defaults                  0  2  
# /mnt/music was on /dev/sdc1 during installation
UUID=63705dc6-133e-449e-9c9d-114a2a760102  /mnt/music      ext3         defaults                  0  2  
# swap was on /dev/sda6 during installation
UUID=751c0a41-95f0-41b0-ab41-8964640b0a2c  none            swap         sw                        0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0  
**[SIZE="5"]UUID=9a66b32b-8213-4469-a52b-ed24ba8357f7   /mnt/ps         ext4         defaults                  0  2 [/SIZE]**

---

### Post by argos3016 on 2010-02-19
First umount them. Then make yourself the mount points with
mkdir -p SOMETHING

and edit the /etc/fstab putting:

/dev/DEVICE         SOMETHING        ext3 or the fs do you want         defaults         1 1

Correct me if I am wrong

---

### Post by DarinB on 2010-02-19
no idea but after reboot it would not mount automatically 
here is my fstab my /mnt/music is 0   2 and it mounts automatically with permissions am i missing something?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sda5 during installation
UUID=14612f17-2d0c-47ad-8ef8-a7f4d3f8a4fa  /               ext4         errors=remount-ro         0  1  
# /home was on /dev/sdb1 during installation
UUID=6f0e63aa-b4ae-4c1c-90dc-1507ae8a0aa7  /home           ext3         defaults                  0  2  
# /mnt/music was on /dev/sdc1 during installation
UUID=63705dc6-133e-449e-9c9d-114a2a760102  /mnt/music      ext3         defaults                  0  2  
# swap was on /dev/sda6 during installation
UUID=751c0a41-95f0-41b0-ab41-8964640b0a2c  none            swap         sw                        0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0 
# /mnt/ps was on /dev/sdb2 added on 02//19/2010 
UUID=9a66b32b-8213-4469-a52b-ed24ba8357f   /mnt/ps         ext4         defaults                  0  2

---

### Post by DarinB on 2010-02-19
I Had aready made the mount point and i changed the entry to below in bold it seems to work the way i wanted it to i have no idea why modeling it after the above entries did not work? maybe because they were established during install the only Identifiers were the uuid numbers???

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sda5 during installation
UUID=14612f17-2d0c-47ad-8ef8-a7f4d3f8a4fa  /               ext4         errors=remount-ro         0  1  
# /home was on /dev/sdb1 during installation
UUID=6f0e63aa-b4ae-4c1c-90dc-1507ae8a0aa7  /home           ext3         defaults                  0  2  
# /mnt/music was on /dev/sdc1 during installation
UUID=63705dc6-133e-449e-9c9d-114a2a760102  /mnt/music      ext3         defaults                  0  2  
# swap was on /dev/sda6 during installation
UUID=751c0a41-95f0-41b0-ab41-8964640b0a2c  none            swap         sw                        0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0 
[B][SIZE="5"]/dev/sdb2   /mnt/ps   ext4   defaults   0   2 
[/SIZE][/B]

---

