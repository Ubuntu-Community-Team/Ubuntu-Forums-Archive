---
title: "Partitioning my windows HD to use with VBox"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by longtom on 2009-02-10
Hi

here is the plan:

I want partition my WinXP HD (250GB Sata), without destroying my XP in order to get space for VBox.

Installed are:

WindowsXP SP2 on a 250GB HD (not 200...) with 140GB free space (and once I get the old stuff off, probably even more.

Ubuntu 8.10 on a seperate harddrive (only 30Gb...I wanted only to test it.and now I'm hooked....terrible)

So in order to get some space to run WinXP in VirtualBox, I want to get 100GB from my XP HD.

Any way to do this, thateven I would understand?

Greetings

longtom

---

### Post by geirha on 2009-02-10
First off, this will probably work out ok, but bad things may happen, so make sure you first back up any data on the drive that you can't afford to lose.

Boot into windows and do a defrag on the filesystem you want to resize. If the filesystem is too fragmented, you won't be able to resize it.

Then boot into the ubuntu cd's live session, open System -> Administration -> Partition Editor, then just resize the windows partition and create a new partition in the freed space. If you only intend to use that new partition from Ubuntu, then choose ext3 as the filesystem type.

EDIT: Oh and once it is created, you'll need to add an entry for it in /etc/fstab.

Read [How to partition](https://help.ubuntu.com/community/HowtoPartition) for information on using the partition editor, and [Installing a new harddrive:Mount the Drive](https://help.ubuntu.com/community/InstallingANewHardDrive#Mount The Drive) for information on how to have it mounted automatically at boot, and how to make it writable.

---

### Post by longtom on 2009-02-10
Sounds simple enough.  

Thank you!  I'll have a go at that tomorrow first thing....

longtom

---

### Post by longtom on 2009-02-11
Right, I did have a go.  Took some time, but it appears to be a full success.  Partition is created, WinXP is still running (after doing a checkdisk).

One little thing...the new parttion appears to be mounted  and I tried to follow the "Mount At Boot" tips of geirha - but I obviously do something wrong.

My initial fstab looks like this

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=bdf8550a-4eaa-48b9-af06-f9db373afa33 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

What must I add to get it going?

Thanks

lt

Some additioanl info, if it is of any help:

```

cango@cango-desktop:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x202b039f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         365     2931831   82  Linux swap / Solaris
/dev/sda2   *         366        3649    26378730   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf89cf89c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       10200       30401   162272565    7  HPFS/NTFS
/dev/sdb2               1       10199    81923436   83  Linux

Partition table entries are not in disk order

```

sdb2 is the culprit in question...

lt

---

### Post by geirha on 2009-02-11
We need to know three things. 

1. What device is it? 
Probably [COLOR="Blue"]/dev/sdb2[/COLOR]. You should be able to identify it by running ```
sudo fdisk -l
``` or looking in the partition editor.

2. What filesystem type is it?
I'll assume it is [COLOR="Green"]ext3[/COLOR].

3. Where do you want it mounted? 
The recommended place to mount it is inside /media/. Let's say you want to mount it as [COLOR="Purple"]/media/storage[/COLOR], then you must create that mount-point.
```
sudo mkdir [COLOR="Purple"]/media/storage[/COLOR]
```

With the above assumptions, the line you want to add should look like:
```
[COLOR="Blue"]/dev/sdb2[/COLOR] [COLOR="Purple"]/media/storage[/COLOR] [COLOR="Green"]ext3[/COLOR] defaults 0 2
```

Using the device node (/dev/sdb2) directly is not such a good idea though, if you add/remove harddrives, the names may get shuffled, so /dev/sdb2 could become /dev/sdc2 and the mount fails. The UUID will remain the same though, so using UUID instead is a good idea. To find the uuid run ```
sudo blkid [COLOR="Blue"]/dev/sdb2[/COLOR]
```

Then change the fstab line to read
```
UUID=<the-uuid> [COLOR="Purple"]/media/storage[/COLOR] [COLOR="Green"]ext3[/COLOR] defaults 0 2
```

---

### Post by longtom on 2009-02-11
As for (1) see edit above.

Otherwise I did the rest you asked me to.  Now I get the message:


Cannot mount Volume

You are not privileged to mount this volume.

*headscratching....

what the heck did I do wrong now?

Please assist

longtom

---

### Post by longtom on 2009-02-11
My fstab now looks like this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=bdf8550a-4eaa-48b9-af06-f9db373afa33 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

UUID=d8ffaedc-0baa-4611-b23a-131f588c9224 /media/storage ext3 defaults 0 2
/dev/sdb2 /media/storage ext3 defaults 0 2
```

Don't I have the same thing twice now?

lt

---

### Post by drs305 on 2009-02-11
> **longtom said:**
> As for (1) see edit above.

Otherwise I did the rest you asked me to.  Now I get the message:


Cannot mount Volume

You are not privileged to mount this volume.

*headscratching....

what the heck did I do wrong now?

Please assist

longtom

Make yourself the owner of the mount point since it is currently owned by root:
```
sudo chown -R *yourusername: */media/storage
```
You could also add "user" or "users" after "defaults" so that you or anyone can mount the partition even if you don't own the mount point (ex: defaults,users).

In answer to the second question, it looks like you do have duplicate entries. You can eliminate the "/dev/sdb2" line if sdb2's UUID is d8ffaed...

Edited: Corrected typo, space added. Thanks geirha.
Just to clarify, the *username:* was not the typo, that convention is the same as typing *username:username*

---

### Post by longtom on 2009-02-11
I had 2 problems.  To start with the folder media/storage didn't exist.  Somehow that 

```

sudo mkdir /media/storage

```

didn't do what we wanted it to do.  The Terminal is still a magical book...and I've lost the key somehow.

So I did a 

```

gksu nautilus

```

which I somehow remembered from a different problem I had (one of my many...).

I created my storage subdirectory in media that way.  We Windows guys are hopeless, I know...

Than my drive was mounted again and with the trick and insight of drs305 it is writable as well!

So the mission succeded - thank you drs305 and especially geirha for your patience.  Much appreciated.

No to the next windmill...run Photoshop and Access in VBox on my new Partition.

But that will be a new thread....

Greetings

Longtom

---

### Post by geirha on 2009-02-11
You have two "equal" lines in your fstab, yes. Remove the one with /dev/sdb2 and keep the UUID version.

To have it mounted properly, either reboot or run the following commands
```
sudo umount /dev/sdb2   # unmounts the partition if it is mounted
sudo mount -a   # This will mount all partitions in /etc/fstab

```


Next you should run the "sudo chown" as the second howto explains, drs305 has a typo in his line, it should be
```
sudo chown $USER:$USER /media/storage
```
The above must be run after the partition is mounted. $USER (must be all uppercase) is a variable in the shell that contains you username, so the chown (change owner) command changes ownership of the drive to your user (instead of root which is the default)

EDIT: err, somehow I missed your last post. You already got it sorted :)

---

### Post by longtom on 2009-02-11
> **geirha said:**
> 
Next you should run the "sudo chown" as the second howto explains, drs305 has a typo in his line, it should be
```
sudo chown $USER:$USER /media/storage
```


I realised that once I checked it against one of the links you gave me...but he gave me the idea.  To find the correct syntax wasn't that difficult than.

lt

---

