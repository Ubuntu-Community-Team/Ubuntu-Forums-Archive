---
title: "Read and write to data partition as standard user?"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-08-24
I have a 190gig data partition on my hard drive and it mounted just fine (gave it my password and it appeared in nautilus) how ever I have to be root to send files to it... Why is this and how can I change it so my default user can also write files to it as normal?

Thanks,
~Jeff

---

### Post by mikewhatever on 2009-08-24
Can you post the output of the df -h command to verify the mount point. Usually all you need to do is chown it to give yourself the ownership.

---

### Post by beastrace91 on 2009-08-24
Here is the output from it (under Fedora11) but I am having the same issue on Fedora/Ubuntu/OpenSUSE
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              14G  2.9G   11G  21% /
/dev/sda1              92M   15M   73M  17% /boot
/dev/sda10             25G  202M   23G   1% /home
tmpfs                 2.0G  488K  2.0G   1% /dev/shm
/dev/sda5             175G  210M  166G   1% /media/152c56e9-0303-4c97a6f7-f57e99d65883
```

Hope that helps.

~Jeff

---

### Post by mikewhatever on 2009-08-24
Is sda5 the partition in question? Any idea why the mount point looks odd?

---

### Post by bodhi.zazen on 2009-08-24
We need to know what file system you are using on the data partition.

Permissions are set on FAT/NTFS different then on Linux Partitions.

---

### Post by mikewhatever on 2009-08-24
I was thinking chwoning the mount point will do, but that mount point is very odd, looks like a UUID. Can you also post your fstab: **cat /etc/fstab**

---

### Post by beastrace91 on 2009-08-24
Here is the output you asked for: ```
jeff@sager-lintop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=4f3e5977-17fe-41de-9389-996fbc143d20 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=db1a50f2-7ce5-4d1b-8595-5ac50666a985 /home           ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=88efcbe5-2e24-4af5-b5a8-bb8008f42d74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

The data partition is formatted to ext3 - I have currently have the system multi-booted (Fedora/Ubuntu/OpenSUSE) with the following partition layout:

```
Primary Partitions:
ext3 - 100megs
swap - 4gigs
Extended Partitions:
  ext3 - 190gig
  ext3 - 15gig
  ext3 - 25gig
  ext4 - 15gig
  ext4 - 25gig
  ext3 - 15gig
  ext3 - 25gig
```

The 15/25 gig partitions at the end are the root and home partitions for each of the three distros.

~Jeff

---

### Post by beastrace91 on 2009-08-24
I can confirm that it is indeed an owner ship issue with the drive... when I run ```
chown jeff /media/storage
``` in terminal I can them read/write the to partition as normal. Is there a way I can have it auto run the chown command when the drive is mounted? 

Also here is the line in my fstab file for auto mounting the partition if it matters: ```
UUID=152c56e9-0303-4c97-a6f7-f57e99d65883 /media/storage	ext3	rw,user,auto,exec 	0	0
```

Thanks,
~Jeff

---

### Post by bodhi.zazen on 2009-08-24
First mount the partition.

Then 

```
sudo chown jeff.users /media/storage
sudo chmod 770 /media/storage
```

With the partition unmounted , /media/storage will be owned by root, but when you mount it it should automatically revert back to jeff.users with permissions of 770, or whatever you set.

---

### Post by wojmur on 2009-08-25
> ```
sudo chown jeff.users /media/storage
sudo chmod 770 /media/storage
```It's not that automatic, though :lolflag:.
How about creating a subdir in the root of your extra partition, e.g. while mounted:
```

sudo mkdir /media/storage/dataforall
sudo chmod 777 /media/storage/dataforall
sudo ln -s /media/storage/dataforall /media/dataforall

```And keep all your data inside that subdir. Would all users be able to then use /media/dataforall as their access point to the partition? Not sure if /media is a good spot to place your symlink in, from a filesystem purist point of view. Perhaps, somewhere in /usr/share is more appropriate.

Anyway, would that general solution be acceptable?

---

### Post by bodhi.zazen on 2009-08-26
> **wojmur said:**
> It's not that automatic, though :lolflag:.


Why not ? If it is not automatic, adjust /etc/fstab

```
# With the partition unmounted :
bodhi@Samsara:~$ ll /mnt | grep Zen
drwxr-xr-x.  2 [COLOR=red]root root[/COLOR]  4.0K 2009-05-26 23:42 Zen

#Now mount
bodhi@Samsara:~$ mount /mnt/Zen                            
bodhi@Samsara:~$ ll /mnt | grep Zen                           
drwxrwx---. 66 [color=green]root users[/color] 4.0K 2009-08-04 00:25 Zen
```See how ownership and permissions changed when I mounted the partition ?

I set the device to be shared , thus owned by root and available to anyone in the users group.

sudo chown root.users /mnt/Zen
sudo chmod 770 /mnt/Zen

In fstab use auto or noauto , users

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by beastrace91 on 2009-08-26
Yea... so it turns out after I ran chown for the first time it kept the permission change. No need to auto run it every time the device is detected like I thought :)

~Jeff

---

