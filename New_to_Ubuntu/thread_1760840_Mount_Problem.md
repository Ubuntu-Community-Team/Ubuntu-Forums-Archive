---
title: "Mount Problem"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-05-17
I installed Mount manager application for auto mounting the partitions at the start up! I dunno what went wrong, in the beginning one of partitions was not mounted in the desired location and it was looping with /mnt directory again and again and after that I reconfigured the mount manager to disable the auto mount at the start up! now none of the partitions are getting mounted when i tried through the dolphin!

pls help

thank you!

---

### Post by bioterror on 2011-05-17
> **1991sudarshan said:**
> I installed Mount manager application for auto mounting the partitions at the start up! I dunno what went wrong, in the beginning one of partitions was not mounted in the desired location and it was looping with /mnt directory again and again and after that I reconfigured the mount manager to disable the auto mount at the start up! now none of the partitions are getting mounted when i tried through the dolphin!

pls help

thank you!

What's wrong with adding drives to /etc/fstab for automount?
I have no experience with Mount Manager, but I have used fstab for almost 15 years and that's the way it is done still today.

Create /media/foobar folder for the drive and then add to fstab line

```

# <file system>        <dir>         <type>    <options>          <dump> <pass>

UUID=21cc4b5d-af63-4a25-8707-8b64f60c0e96 /media/Backup ext4 defaults 0 1

```

You can get your drives UUID with command
```
sudo blkid
```

---

### Post by Morbius1 on 2011-05-17
> **bioterror said:**
> I have no experience with Mount Manager, but I have used fstab for almost 15 years and that's the way it is done still today.
Mountmanager  is a GUI that enables you to edit fstab ( among other things ) by selecting options. In reality it's a GUI to "man mount" offering the unsuspecting victim ... er ... user a dizzying array of options which usually results in the kind of posts you see here.

In addition to the advice you gave I would suggest posting the output of the following as well:
```
cat /etc/fstab
mount
```

---

### Post by 1991sudarshan on 2011-05-17
> **Morbius1 said:**
> Mountmanager  is a GUI that enables you to edit fstab ( among other things ) by selecting options. In reality it's a GUI to "man mount" offering the unsuspecting victim ... er ... user a dizzying array of options which usually results in the kind of posts you see here.

In addition to the advice you gave I would suggest posting the output of the following as well:
```
cat /etc/fstab
mount
```


[B]kevin@kevin-desktop:~$ cat /etc/fstab
UUID=5210A9B810A9A407 /mnt/sda1 ntfs-3g noauto 0 0
UUID=b1332f0f-d55b-4082-8350-e17a14c2a316 swap swap sw 0 0
UUID=10791e7b-df61-4a5b-a543-a250c0d1ca49 /media ext4 noauto 0 0
UUID=0F75E0010C16ED5B /mnt/sda5 ntfs-3g noauto 0 0
UUID=4a616438-6a2f-41c0-9f5a-b9ad54d500f0 / ext4 defaults 0 1
UUID=6AD0D8DA3589C220 /mnt/sda6 ntfs-3g noauto 0 0
UUID=349551E454320BE4 /mnt/sda7 ntfs-3g noauto 0 0
UUID=6C44538F27B40F61 /mnt/sda8 ntfs-3g noauto 0 0
UUID=23E4386C3B553D13 /mnt/sda9 ntfs-3g noauto 0 0
kevin@kevin-desktop:~$ mount
/dev/sda3 on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
kevin@kevin-desktop:~$ [/B]

---

### Post by 1991sudarshan on 2011-05-18
??

---

### Post by Morbius1 on 2011-05-18
Then only coherent fstab entries are the ones you created in your initial install. All the rest of them have the exact same problem:
> UUID=5210A9B810A9A407 /mnt/sda1 ntfs-3g [COLOR=Blue]noauto[/COLOR] 0 0
UUID=10791e7b-df61-4a5b-a543-a250c0d1ca49 /media ext4 [COLOR=Blue]noauto[/COLOR] 0 0
UUID=0F75E0010C16ED5B /mnt/sda5 ntfs-3g [COLOR=Blue]noauto[/COLOR] 0 0
UUID=6AD0D8DA3589C220 /mnt/sda6 ntfs-3g [COLOR=Blue]noauto[/COLOR] 0 0
UUID=349551E454320BE4 /mnt/sda7 ntfs-3g [COLOR=Blue]noauto[/COLOR] 0 0
UUID=6C44538F27B40F61 /mnt/sda8 ntfs-3g [COLOR=Blue]noauto[/COLOR] 0 0
UUID=23E4386C3B553D13 /mnt/sda9 ntfs-3g [COLOR=Blue]noauto[/COLOR] 0 0"noauto" tells the system to not automatically mount these partitions on boot which is exactly what it's doing. For all the ntfs partitions I would suggest changing "noauto" to "defaults,uid=1000". 

For the ext4 partition you have two problems: the "noauto" and a proper mount point. So...
Create a mount point:
```
sudo mkdir /media/Data
```[COLOR=Blue]*I don't know what that partition holds so I randomly called it Data.*[/COLOR]
And change "noauto" to "defaults,noatime".

So when you're done the lines in fstab that I quoted above should look like this:
> UUID=5210A9B810A9A407 /mnt/sda1 ntfs-3g defaults,uid=1000 0 0
UUID=10791e7b-df61-4a5b-a543-a250c0d1ca49 /media/Data ext4 defaults,noatime 0 0
UUID=0F75E0010C16ED5B /mnt/sda5 ntfs-3g defaults,uid=1000 0 0
UUID=6AD0D8DA3589C220 /mnt/sda6 ntfs-3g defaults,uid=1000 0 0
UUID=349551E454320BE4 /mnt/sda7 ntfs-3g defaults,uid=1000 0 0
UUID=6C44538F27B40F61 /mnt/sda8 ntfs-3g defaults,uid=1000 0 0
UUID=23E4386C3B553D13 /mnt/sda9 ntfs-3g defaults,uid=1000 0 0
When you are done making the changes and since these partitions are not mounted you can run the following command to test for errors and mount the new partitions without a reboot:
```
sudo mount -a
```[COLOR=Blue]EDIT:[/COLOR] You should run the "sudo blkid" command as bioterror suggested just to make sure that mountmanger didn't screw up the UUID numbers too.

---

### Post by 1991sudarshan on 2011-05-18
> **Morbius1 said:**
> Then only coherent fstab entries are the ones you created in your initial install. All the rest of them have the exact same problem:
"noauto" tells the system to not automatically mount these partitions on boot which is exactly what it's doing. For all the ntfs partitions I would suggest changing "noauto" to "defaults,uid=1000". 

For the ext4 partition you have two problems: the "noauto" and a proper mount point. So...
Create a mount point:
```
sudo mkdir /media/Data
```[COLOR=Blue]*I don't know what that partition holds so I randomly called it Data.*[/COLOR]
And change "noauto" to "defaults,noatime".

So when you're done the lines in fstab that I quoted above should look like this:
When you are done making the changes and since these partitions are not mounted you can run the following command to test for errors and mount the new partitions without a reboot:
```
sudo mount -a
```[COLOR=Blue]EDIT:[/COLOR] You should run the "sudo blkid" command as bioterror suggested just to make sure that mountmanger didn't screw up the UUID numbers too.


[B]UUID=5210A9B810A9A407 /mnt/sda1 ntfs-3g auto 0 0
UUID=b1332f0f-d55b-4082-8350-e17a14c2a316 swap swap sw 0 0
UUID=10791e7b-df61-4a5b-a543-a250c0d1ca49 /media ext4 noauto 0 0
UUID=0F75E0010C16ED5B /mnt/sda5 ntfs-3g auto 0 0
UUID=4a616438-6a2f-41c0-9f5a-b9ad54d500f0 / ext4 defaults 0 1
UUID=6AD0D8DA3589C220 /mnt/sda6 ntfs-3g auto 0 0
UUID=349551E454320BE4 /mnt/sda7 ntfs-3g auto 0 0
UUID=6C44538F27B40F61 /mnt/sda8 ntfs-3g auto 0 0
UUID=23E4386C3B553D13 /mnt/sda9 ntfs-3g auto 0 0
kevin@kevin-desktop:~$ [/B]

Thanks for the suggestion to change "noauto " to "uid=1001"! **I change "noauto" to "auto"** before you posted this suggestion and it seems that it is working properly! When ever I enter any of the partitions auto mounted on /mnt, I get the the short cut of that partition in the **"PLACES" side panel** and when I navigate out of that mounted partition the icon or the partition disappears from the **"PLACES" side panel **in dolphin

---

### Post by Morbius1 on 2011-05-18
> ** UUID=10791e7b-df61-4a5b-a543-a250c0d1ca49 /media ext4 noauto 0 0**That's still not right. 
> Thanks for the suggestion to change "noauto " to "uid=1001"!My suggestion was to change "noauto" to "defaults,uid=1000" for the ntfs partitions. "uid=1000" will among other things prevent you from getting an error message when you try to send something to the trash.
> **I change "noauto" to "auto"** before you posted this suggestion and it seems that it is working properly!"auto" is in "defaults" by .. um ... default.
> When ever I enter any of the partitions auto mounted on /mnt, I get the the short cut of that partition in the **"PLACES" side panel** and when I navigate out of that mounted partition the icon or the partition disappears from the **"PLACES" side panel **in dolphin     I know nothing of dolphin other than it is an aquatic animal as I do not use KDE.

---

### Post by 1991sudarshan on 2011-05-20
> **Morbius1 said:**
> That's still not right. 
My suggestion was to change "noauto" to "defaults,uid=1000" for the ntfs partitions. "uid=1000" will among other things prevent you from getting an error message when you try to send something to the trash.
"auto" is in "defaults" by .. um ... default.
I know nothing of dolphin other than it is an aquatic animal as I do not use KDE.


I am not getting any error message when i delete the items from the partitions mounted on /mnt! Shall i leave the /etc/fstab file as such or shall I edit? Till now everything is going on well!

---

### Post by fuLLcoLLapse on 2011-05-20
hi, i have the same problem, I can't browse the other partition in my hard drive. 
This is the output of **sudo blkid**

/[B]dev/sda1: LABEL="PQSERVICE" UUID="8A1222031221F4BB" TYPE="ntfs" 
/dev/sda2: LABEL="eMachines" UUID="986216FA6216DCB6" TYPE="ntfs" 
/dev/sda4: LABEL="Open Files" UUID="E2E4BBE8E4BBBD5B" TYPE="ntfs" 
/dev/sda5: UUID="866c11f8-efba-422b-8ae5-06dc1ec207f3" TYPE="ext2" 
/dev/sda6: UUID="386136af-e999-499c-8ba6-a97ccc3f152b" TYPE="swap" 
/dev/sda7: UUID="e9e1e564-65a6-4ee8-8ce3-d83167403c52" TYPE="ext4" 
/dev/sda8: UUID="520f4cb2-1b2b-489f-8126-87fcb8267140" TYPE="ext4" 
/dev/sdb1: LABEL="MULTIBOOT" UUID="821E-FEBC" TYPE="vfat"[/B]

and this is the output of [B]cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=e9e1e564-65a6-4ee8-8ce3-d83167403c52 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb5 during installation
UUID=866c11f8-efba-422b-8ae5-06dc1ec207f3 /boot           ext2    defaults        0       2
# /home was on /dev/sdb8 during installation
UUID=520f4cb2-1b2b-489f-8126-87fcb8267140 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=386136af-e999-499c-8ba6-a97ccc3f152b none            swap    sw              0       0[/B]

---

### Post by Morbius1 on 2011-05-20
> **1991sudarshan said:**
> I am not getting any error message when i delete the items from the partitions mounted on /mnt! Shall i leave the /etc/fstab file as such or shall I edit? Till now everything is going on well!
You are getting an error message when you "Move to Trash" any file in the ntfs partitions. If it doesn't bother you it doesn't bother me.

---

