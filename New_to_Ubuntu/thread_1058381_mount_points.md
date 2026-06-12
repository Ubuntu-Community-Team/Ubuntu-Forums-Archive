---
title: "mount points"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by alican timur on 2009-02-02
Ok. Yesterday, when i switched to ubuntu (again), I've created a 90gb fat32 partition to stuff in my music and pictures for backup. I've mounted this partition as /backup when I was installing ubuntu 8.04. Then, the same evening, i found out about 8.10 and tried to upgrade. It didn't work properly, none of my hardcore-necessary software (ie firefox, pidgin) worked. So i made a clean install. 

Now ubuntu doesn't see my 90gb fat32 partition. It recognises it as a CD, and mounts it to /media/ something. I tried to change the mount point to /backup again, but i think i got the idea of mount points wrong, because it gives the error
```

Cannot mount volume.
Unable to mount the volume. 

mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR (usually /)
```

then i tried to solve this by manually editing the fstab file, but i didn't understand how that worked, so i tried to make this go away by deleting the line that belonged to that partition. that didn't work either. This is my current fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=83dc6bf6-2eaf-4eae-96ba-9ddeca40229d /               reiserfs notail,relatime 0       1
# /dev/sda5
UUID=99af0c62-8330-4887-bf51-5cc4cdcccf58 none            swap    sw              0       0

```

(my 90gb drive is not displayed here, because i've deleted it, but i can still see it when i go to places -> computer as "90.1gb media")

I want to mount this partition as /backup again. Help please?

---

### Post by cdtech on 2009-02-02
You'll need two bits of information:
```
blkid
```
And:
```
sudo fdisk -l
```
Then we can edit the fstab file.........

---

### Post by akelsall on 2009-02-02
alican, is there a reason you're using fat32, rather than ext3 if this is just to back up music files? 

Try this. Open Gparted (click System | Administration | Partition editor.

See if you can locate the 90 Gb partition you want to mount. If you see it there, note the partition number (e.g. /dev/sda12). 

Now, open a terminal window and enter the command:

**sudo /sbin/vol_id   --uuid   /dev/sdaX**  (where X is the partition # you noted above). It's hard to see here, but there's a space between vol_id and the --uuid. Also, there's a space between --uuid and /dev.

Now, go into fstab (sudo vi /etc/fstab) and add the following line (this assumes you end up going with an ext3 filesystem). Just change the X to your partition number:

# /dev/sda**[COLOR="Red"]X[/COLOR]**
UUID=**[COLOR="DarkOrange"]your_volume_ID[/COLOR]** /**[COLOR="DarkOrange"]dir_you_created_as_a_mountpoint[/COLOR]**         ext3    relatime        0       2

HTH

Andy

---

### Post by alican timur on 2009-02-02
@cdtech:
```
psychaos@psychaos-desktop:~$ blkid
/dev/sda1: UUID="83dc6bf6-2eaf-4eae-96ba-9ddeca40229d" TYPE="reiserfs" 
/dev/sda5: UUID="99af0c62-8330-4887-bf51-5cc4cdcccf58" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
```

what's that loop0?

```

psychaos@psychaos-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19d019d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18236   146480638+  83  Linux
/dev/sda2           18237       30401    97715362+   5  Extended
/dev/sda5           18237       18722     3903763+  82  Linux swap / Solaris
/dev/sda6           18723       30401    93811536    b  W95 FAT32

```

@akelsall

yes there is a reason i want to use fat32. I've been switching to windoze and ubuntu back and forth instinctively for about a year now, and it's very boring to wait for a 45gb music archive to copy to an external hard drive.

yes, i can see the 90gb partition. it's defined as /dev/sda6.

I did as you said, but modified it a bit according to my needs, so i added the line

> # /dev/sda6
UUID=759c02e2-fdb4-46fe-a9c6-76163a086f69 /backup fat32 relatime 0 2

should work right?

---

### Post by alican timur on 2009-02-02
i applied changes, and i've restarted (by using ctrl + alt + bs, should i reboot fully btw?) and nothing has changed.

and again btw, is there a possibility that it should be realtime instead of relatime?

---

### Post by laffinet on 2009-02-02
No, it's relatime.

---

### Post by alican timur on 2009-02-02
bump

---

### Post by cdtech on 2009-02-02
Just type "mount -a" after an fstab change....

**UPDATE::.**
# Entry for /dev/sda3 :
UUID=C6AAD33AAAD325A9 /media/Storage ntfs defaults,umask=002,gid=46 0 2

Try using the device rather than the UUID..........

---

### Post by jerome1232 on 2009-02-02
A couple of things, in order for it get mounted to /backup that folder must exist.


I would also add some option's to your fstab, since fat doesn't support linux permissions it has to emulate them at mount time. (but more on that later)

what happen's when you try to mount it

```
sudo mount -a
```

---

### Post by alican timur on 2009-02-02
@cdtech:

that didn't work. 

> mount: special device /dev/disk/by-uuid/C6AAD33AAAD325A9 does not exist


@jerome1232:

i created the folder, gave some other error, which i missed. 

--

can't i just format the backup partition and mount it again with default settings?

---

### Post by alican timur on 2009-02-02
okay. now i seriously screwed everything up. I can only boot up as partitions mounted read only, and i have no swap partition. here's my fstab file: 
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=83dc6bf6-2eaf-4eae-96ba-9ddeca40229d /               reiserfs notail,relatime 0       1
# /dev/sda5
UUID=99af0c62-8330-4887-bf51-5cc4cdcccf58 none            swap    sw              0       0
# /dev/sda6
UUID=C6AAD33AAAD325A9 /media/Storage ext3 defaults,umask=002,gid=46 0 2

and this is how gparted looks: (see attachment)

---

### Post by cdtech on 2009-02-02
> **alican timur said:**
> @cdtech:

that didn't work. 



@jerome1232:

i created the folder, gave some other error, which i missed. 

--

can't i just format the backup partition and mount it again with default settings?
I just put that there for an example, use your own UUID. Rather, just use the device instead of the UUID.........

---

### Post by laffinet on 2009-02-02
Does that partition contain any data ? I'm a bit surprised it shows "unknown" as filetype in gparted. If it does not contain data, you might want to reformat to fat32 using gparted and then try editing fstab to mount it. 
As others said, make sure you use the right UUID (or device) and that the folder you want to mount to exists.

---

### Post by laffinet on 2009-02-02
You might also want to do a bit more reading [here]("http://ubuntuforums.org/showthread.php?t=283131"). Explains quite well what fstab does, what to put in etc.
Always good to have some background information when trying to do things.

---

### Post by alican timur on 2009-02-03
alright, i followed the fstab manual laffinet gave, fstabbed using my own UUID's and solved it. thanks a lot to everyone.

---

### Post by desktopanalyst on 2009-02-11
I personally am a little confused. Did you say you created a 90gb fat32 partition? I thought fat32 only "read" a max of 4gb partition. Am I totally missing what is going on? This is my first reply, ever...

---

### Post by jerome1232 on 2009-02-11
> **desktopanalyst said:**
> I personally am a little confused. Did you say you created a 90gb fat32 partition? I thought fat32 only "read" a max of 4gb partition. Am I totally missing what is going on? This is my first reply, ever...

fat32 has a maximum file size limit of 4 GB's. Meaning a single file can't be over 4 GB's. So you couldn't put a dvd image on a fat32 filesystem.

The filesystem itself can be quite large actually. I'm not sure what the actual limit is. (512 GB's or something like that)

---

### Post by mc4man on 2009-02-11
> thought fat32 only "read" a max of 4gb partition

That 4Gb limitation is for 'file size' not partition size. 

If you were reading this thread with interest to the orig. problem, the solution was in the error message and would have only taken a few seconds to fix.

> mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR (usually /)
He tried to create a new mount point, probably by editing the properties of the drive/volume. When done that way you are only editing how it mounts in /media.

> I tried to change the mount point to /backup

So it probably turned into /media//backup which is not allowed.

It could have been fixed by running 
gconf-editor
and removing the 'bad' mount point edit in system -> volumes or drives.

All partitions not in fstab by default will mount to /media/volume label or /media/volume size if it has no label

if one wanted to have it mount to /media/backup then in the properties of the volume you'd just enter in the mount point line

backup

---

