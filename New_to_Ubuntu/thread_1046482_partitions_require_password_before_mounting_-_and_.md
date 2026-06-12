---
title: "partitions require password before mounting - and can't save or edit anything on them"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by phantomjoker on 2009-01-21
Hi there.

I have partitioned my HDD to have 3 partitions - my boot (10GB), my home(20GB) and my stuff(600GB). But to access my 600GB partition requires me to first mount it, then enter my password, and even then i can't touch anything on it - or i get the message 'access denied'. 

How can i change this - i really want it to be mounted like the others so it doesn't even require a password, let alone not let me use it!

cheers

---

### Post by jerome1232 on 2009-01-21
If "my stuff" is a linux partition then you need to add it to your fstab and then change the permissions on it so that your users or all users have access to the files.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If also stumbled on a gui tool for editing fstab in another, thread. I haven't personally used it so no adivce on it's usage. It's called pysdm.
To install it
```
sudo apt-get install pysdm
```

To change permissions you can open a root nautilus and browse to the mount point, right click the folder, click permissions, modify them to your needs.

or from a command-line
```
sudo chown -R $USER: /path/to/mount/point
```

If it's a microsft partition (fat, ntfs) then you need to add it to fstab and give it a umask that allows users to modify files on it. Check the link above for detail on fstab editing.

---

### Post by drs305 on 2009-01-21
You can add that partition to fstab to load it at boot, and/or set it up so you won't have to be 'root' to mount it. Please post the results of:
```

sudo blkid
sudo fdisk -l
cat /etc/fstab

```

Also tell us the name of the mount point you desire (normally /media/XXXXXX)

---

### Post by phantomjoker on 2009-01-21
> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5ced3d9e-bb13-4189-823f-63c505c812d7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=05565e84-9c10-4d6c-bc4b-2b56062633e8 /home           ext3    relatime        0       2
# /dev/sda5
UUID=b64698a1-5cab-4827-ac24-94d962935b44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


> sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b099b09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        3648    19535040   83  Linux
/dev/sda4            4014       91201   700337610    5  Extended
/dev/sda5            4014        4535     4192933+  82  Linux swap / Solaris
/dev/sda6            4536        5840    10482381   83  Linux
/dev/sda7            5841        8451    20972826   83  Linux
/dev/sda8            8452       91201   664689343+  83  Linux


> 
mckenzie@mckenzie-home:~$ sudo blkid
/dev/sda1: UUID="5ced3d9e-bb13-4189-823f-63c505c812d7" TYPE="ext3" 
/dev/sda2: UUID="05565e84-9c10-4d6c-bc4b-2b56062633e8" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b64698a1-5cab-4827-ac24-94d962935b44" 
/dev/sda6: UUID="d244f752-2436-4746-9e1e-e72e0240be18" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="7efba4f4-762a-4ea4-9373-5cc6f21c237e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="28ddb621-10d6-4747-a569-311cf324d779" SEC_TYPE="ext2" TYPE="ext3" 


the location of the partition is /media/disk

---

### Post by drs305 on 2009-01-21
Make a mount point for sda[COLOR="Red"]8[/COLOR] (If the partition isn't sda8 change all instances to the appropriate designation) I recommend changing the name to something other than "disk" since this is a name automatically used by the system. The system would adjust, but another name won't hurt. I picked "data" - choose whatever you want.

Bold requires user input:

Make the mountpoint:
```
sudo mkdir /media/**data[COLOR="Red"][/COLOR]**
```

Change ownership of mountpoint to yourself and set permissions. Replace *username* with your logon name:
```
sudo chown -R ***username:username*** /media/**data**
chmod -R 750 /media/**data**

```

Backup fstab and open for editing (example uses gedit but you can use any text editor):
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Add this line:
```

UUID=28ddb621-10d6-4747-a569-311cf324d779 /media/**data** ext3 defaults,users 0 2 

```
Save the file.

Mount the new partition:
```

sudo umount /dev/sda8
sudo mount /dev/**sda8**

```
When you run the second command, if it works you will see nothing and sda8 will now be mounted on /media/data.

---

### Post by phantomjoker on 2009-01-21
how do i know whether or not that partition is sda8?

---

### Post by jerome1232 on 2009-01-21
Post the output from mount, you said it's currently mounted at /media/disk right?

```
mount
```

---

### Post by phantomjoker on 2009-01-21
ah yes - it is sda8!

---

### Post by phantomjoker on 2009-01-21
Um, i dont know what all those commands did - but i have the same problem - but i now have a /media/disk , which is 5Gbs!

where did this come from? what have i just done?

---

### Post by drs305 on 2009-01-21
> **phantomjoker said:**
> Um, i dont know what all those commands did - but i have the same problem - but i now have a /media/disk , which is 5Gbs!

where did this come from? what have i just done?

If sda8 wasn't mounted at the time, the /media/disk folder probably contains files that were saved to that mount point when the partition was not mounted to it. Not to worry - you haven't lost any data on the partition.

Normally mount points remain empty when the device is not mounted on it. Decide where you want that data and move it there.

Use a file browser and see if you have a /media/data folder (or whatever you named it). Your sda8 files will probably be there.

When you ran the mount command for sda8, what messages, if any, did you get?

PS: I'm sending you a PM.

---

### Post by jerome1232 on 2009-01-21
Show us your current fstab and what your mounts currently look like to give us an idea of the current state of the system

```
cat /etc/fstab
mount
```

---

### Post by phantomjoker on 2009-01-21
ok

> mckenzie@mckenzie-home:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5ced3d9e-bb13-4189-823f-63c505c812d7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=05565e84-9c10-4d6c-bc4b-2b56062633e8 /home           ext3    relatime        0       2
# /dev/sda5
UUID=b64698a1-5cab-4827-ac24-94d962935b44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

UUID=28ddb621-10d6-4747-a569-311cf324d779 /media/data ext3 defaults,users 0 2



> mckenzie@mckenzie-home:~$ mount
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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mckenzie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mckenzie)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=mckenzie)


---

### Post by drs305 on 2009-01-21
Mount doesn't show sda8 mounted.

Did you run:
```

sudo mount /dev/sda8

```

Did you get any error messages?  If so, what were they?

If not:
```

nautilus /media/data

```

---

### Post by phantomjoker on 2009-01-21
now hold on - i jusd did the two commands you just posted, and nautilus opened 'data' which is the 600GB partition - so it did work... ?!

---

### Post by drs305 on 2009-01-21
Yes it did. 

Did you understand what I was trying to say about the data still existing in the /media/disk folder? I will try to explain it better if you desire.

---

### Post by phantomjoker on 2009-01-21
if you would - i would be much appreshiating! cheers

---

### Post by phantomjoker on 2009-01-21
but one more thing - how come when i attempt to download a file to that drive i am told - access denied?

---

### Post by phantomjoker on 2009-01-21
im affriad this has not worked, as after a reboot - the partiton is mounted, but not accessable.

---

### Post by drs305 on 2009-01-21
Did you change the ownership of the mount point? I'll use phantomjoker as your username. Use your *actual username*:
```

sudo chown -R phantomjoker:phantomjoker /media/data
chmod 755 -R /media/data

```
The first command makes sure you are the owner of /media/data  If you are the owner you should be allowed to write and access it.
The second command sets read/write/execute permissions for you, read/execute for your group and others.

As for initially being able to find 5GB of stuff on /media/data:

Linux/ubuntu doesn't really think of hardware, just files.

When an device/partition automounts, it creates the mount point if it doesn't exist - in this case "disk". When you then look at it with a file browser, you click on /media/disk but what you are really seeing are the contents of the mounted device ( sda8 ). When the device ( sda8 ) is unmounted, the mount point will either disappear entirely or will remain and appear empty. If you click on it there won't be any files in it.

Let's say the device isn't mounted but the mount point still exists. Normally it would be empty. However, you could save files to it if you tried. This is probably what happened in your case. A small amount of data was copied to this folder when sda8 was not mounted, so it was written to /media/disk. When you clicked on it with sda8 unmounted, you couldn't see the contents of sda8 but you could see the data that was written directly to /media/disk.

A situation that arises from time to time is a user who has a script to backup something. It normally writes the backups to the *mounted* sda8 via the /media/disk mount point. If for some reason the device isn't mounted at the time. The backup is _still_ written to /media/disk. The difference is that it is now being written to /media/disk on the system partition. Suddenly the / partition is completely full and the user doesn't understand why.

---

### Post by phantomjoker on 2009-01-21
um - i think i just screwed up, i entered

sudo chown -R $USER: /

what did i just do?

---

### Post by drs305 on 2009-01-21
I just read your other post. It probably progressed too far to recover the normal structure but you can look to see what has changed.

You can search to see how far the action progressed by running this (assuming your uid is 1000). See if it extends into most of the folders (/usr, /root, etc):
```

sudo find / -maxdepth 2 -user 1000 | grep -v "proc"

```

That you have a separate home partition is a good thing if you have to reinstall the system. There are threads from others who have done the same thing. 

See what problems you have with your current setup and watch your other thread and wait for some responses before you determine your next step. 

If you reinstall, make sure you select your *current* /home partition and * make sure you  do not format it*.

Here is something you can do to retrieve all your installed apps after a new install, if it comes to that:
```

dpkg --get-selections > $HOME/Desktop/installed.apps

```
After the install:
```

sudo dpkg --clear-selections
sudo dpkg --set-selections < $HOME/Desktop/installed.apps

```

---

### Post by phantomjoker on 2009-01-21
i tried the command, but got the message

> sudo: must be setuid root

---

### Post by drs305 on 2009-01-21
As a minimum you will need to go to the LiveCD, mount your system partition and chown /usr back to root to get sudo. Here is a link from a post by another user:

[http://ubuntuforums.org/showthread.php?t=219767]("http://ubuntuforums.org/showthread.php?t=219767")

If you have a backup, good for you. It would be easier to restore it than to try to figure out exactly what needs to be changed back.

---

