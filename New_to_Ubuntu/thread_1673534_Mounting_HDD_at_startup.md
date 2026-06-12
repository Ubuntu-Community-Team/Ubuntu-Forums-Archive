---
title: "Mounting HDD at startup"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Linux-is-super on 2011-01-22
Hi !

I have some shortcuts on my desktop. They point to some files and folders on separate HDD. But each time before using these shortcuts I have to mount HDD . Is there a way to mount HDD at startup . I use Ubuntu 10.10.

Thank you !

---

### Post by Wtower on 2011-01-22
Hi,

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Linux-is-super on 2011-01-22
Thank you Wtower !
I'l try !

---

### Post by Linux-is-super on 2011-01-22
Hi !
I just tried pysdk . I can mount HDD partitions that are on the same HDD like o.s. Linux is on. But I can't mount second HDD i.e. sda1

---

### Post by JKyleOKC on 2011-01-22
If you have Gigolo on your system, you can use it to mount most any drive, internal or external. It came as part of my install with 10.04 but I don't know if it's there in 10.10. If you don't have it, look for it in the Ubuntu Software Center or Synaptic Package Manager.

---

### Post by baddnady23 on 2011-01-22
Open the terminal and type ```
gksu gedit /etc/fstab

```
enter your password and then paste the output here.

---

### Post by Linux-is-super on 2011-01-22
Ok, thanks all !
 
Here is fstab 

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda2 during installation
UUID=cdabf6f2-12f8-4e12-aa00-d9496062537c  /               ext4  defaults                  0  1  
# /home was on /dev/sda5 during installation
UUID=0c9e83f4-fece-45c9-85aa-374a6bc4d5dd  /home           ext4  defaults                  0  2  
# swap was on /dev/sda6 during installation
UUID=869e29f2-a1c4-4be8-9d5d-f46ccce108c8  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb7                                  /media/sda1     ext4  users,user,owner          0  0  
/dev/sdb1                                  /media/sdb1     ntfs  defaults                  0  0

---

### Post by Linux-is-super on 2011-01-22
Hi JKyleOKC !

I just installed Gigolo . How can I use it for solving my problem ?

---

### Post by JKyleOKC on 2011-01-22
I may have misled you -- it will access any drives, but apparently you can already do that through Places, and what you're looking for is a way to mount them automatically at boot time.

Your fstab posting shows that you have a mount point established for sda1 but are mounting sdb7 to it instead. I would copy that line and paste the copy right below the original, then edit "sdb7" in the upper of the two to be "sda1" and change the "sda1" in the second to be "sdb7" so that both mount points have the same names as the drives (actually the partitions) that will be mounted there. Then before you reboot, use "sudo mkdir /media/sdb7" to create the mount point just added to the fstab file. You will have to have root privileges to edit fstab, and should also make a backup copy before making any changes:
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```The first line makes the backup and the second will launch the editor with root privilege so you can make the changes.

The pysdm program should be able to see any drives that your system has recognized, though, and will do all this for you. The left-hand side of its screen should list drives, with a small triangle to the left of the drive name such as sda or sdb. Clicking that triangle will pop down a list of the partitions, and when you highlight a partition, you should get a dialog asking if you want to configure it (if it's not yet configured)...

---

### Post by Linux-is-super on 2011-01-23
Hi !

This is my new, edited fstab. 


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda2 during installation
UUID=cdabf6f2-12f8-4e12-aa00-d9496062537c  /               ext4  defaults                  0  1  
# /home was on /dev/sda5 during installation
UUID=0c9e83f4-fece-45c9-85aa-374a6bc4d5dd  /home           ext4  defaults                  0  2  
# swap was on /dev/sda6 during installation
UUID=869e29f2-a1c4-4be8-9d5d-f46ccce108c8  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sda1                                  /media/sda1     ext4  users,user,owner          0  0  
/dev/sdb7                                  /media/sda1     ext4  users,user,owner          0  0  
/dev/sdb1                                  /media/sdb1     ntfs  defaults                  0  0  


It looks like sdb7 sda1 are somehow mixing ? I'm blindly leaded, I don't know what I am doing :)

---

### Post by Elfy on 2011-01-23
First I would stop using the /dev/sdxy way of referring to drives and use UUID's - they'll not change normally.

To find the uuid's 

```
sudo blkid
```

To use the UUID for sda1 for example the line would now read

```
UUID=longnumberfound /media/sda1 ext4 users,user,owner 0 0
```

Change the ntfs line - try 

```
UUID=longnumberfound /media/sdb1 ntfs auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

---

### Post by vanadium on 2011-01-23
In addition to foresptiksi: you also need to fix the issue of mounting two volumes on the same location (/mnt/sda1)
```

/dev/sda1 /media/sda1 ext4 users,user,owner 0 0
/dev/sdb7 /media/sda1 ext4 users,user,owner 0 0

```
should become
```

/dev/sda1 /media/sda1 ext4 users,user,owner 0 0
/dev/sdb7 [color=red]/media/sdb7[/color] ext4 users,user,owner 0 0

```
You will perhaps still need to create the directory /media/sdb7 if it is not yet there: "sudo mkdir /media/sdb7".

Do indeed change the device designation (/dev/sda1, /dev/sda7, etc by the UUIDS as foresptiksi suggested. On many hardware nowadays, device designations tend to change between boots.

A quick test to see whether your /etc/fstab is properly configured, is to issue the command
```

sudo mount -a

```

There should not be output. If there is not, then all drives will be mounted according to the instructions in /etc/fstab. This tip saves you a reboot.

---

### Post by Elfy on 2011-01-23
Good catch - missed that :)

/me blames lack of tea

---

### Post by JKyleOKC on 2011-01-23
> **vanadium said:**
> You will perhaps still need to create the directory /media/sdb7 if it is not yet there: "sudo mkdir /mnt/sdb7".In the mkdir command it should be [COLOR="Red"]/media/sdb7[/COLOR] to match the path put into fstab. Normally I wouldn't mention such a typo, but the OP says he is blindly following our directions!

Thanks for catching the errors, and for nudging me to fixing my own fstab to use UUID instead of the sd* notation!

---

