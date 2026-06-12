---
title: "Changing permissions on external HD?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by socref on 2008-12-07
Hello, everyone. 

Using Ubuntu 8.04 on my desktop. No Windoze.

I just got a Seagate external 500GB FreeAgent Go hard-drive (USB). When I looked at the permissions I noticed it said "root," so I figured it might be useful to change that so I could manipulate files and maybe partition the drive. But I'm having no success.

Previously I had written to this forum to ask about changing permissions on a memory stick that indicated all permissions as "root," so I tried what was suggested for the memory stick by typing in a terminal: gksudo nautilus /media

This was the output:

gil@Phred:~$ gksudo nautilus /media
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nautilus:7434): WARNING **: Unable to add monitor: Operation not supported seahorse nautilus module shutdown
gil@Phred:~$ 


I then went to the HD icon in /media, right clicked and tried to change permissions. I tried switching the owner from "root" to "gil" but it did not stick and immediately reverted to "root." 

I also tried to change group from "root" to "users" and the same thing happened. As soon as I lifted my finger from the mouse it switched back to "root."

So I'm stumped and would appreciate guidance on achieving control over the permissions on this external HD.

I also noticed after searching these forums a lot of discussion about problems mounting the Seagate FreeAgent HD on boot-up. When I tried to restart the computer with the external HD connected the boot never finished -- I just got a black screen with a flashing cursor that never advanced. 

Am I correctly understanding that without jumping through some hoops I can't restart the pooter unless I first unplug the external HD? That seems a bit ridiculous.

Thanks again for guidance.
socref

---

### Post by taurus on 2008-12-07
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by socref on 2008-12-08
> **taurus said:**
> Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

Here you go. Thanks for your help.

gil@Phred:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       30151   232420387+  83  Linux
/dev/sda3           30152       30394     1951897+  82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS
gil@Phred:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.3G  3.5G  5.4G  40% /
varrun               1013M  100K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   56K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   39M  974M   4% /lib/modules/2.6.24-22-generic/volatile
/dev/sda2             222G   19G  203G   9% /home
gvfs-fuse-daemon      9.3G  3.5G  5.4G  40% /home/gil/.gvfs
/dev/sdf1             466G  158M  466G   1% /media/FreeAgent Drive
gil@Phred:~$

---

### Post by lovelyvik293 on 2008-12-08
You have to mount the mount point of the drive not the /media folder.
So write 
```

gksudo nautilus /media/FreeAgent Drive

```

---

### Post by geirha on 2008-12-08
> **socref said:**
> 
gil@Phred:~$ sudo fdisk -l
Disk /dev/sdf: 500.1 GB, 500107862016 bytes
[...]
   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS


HPFS/NTFS. That means it has an NTFS filesystem. Permissions on NTFS filesystems in linux is not supported. That's why those changes doesn't stick. What is done instead, is that the permissions and ownership for all files are set when the filesystem is mounted, and currently root is set as the owner. You'll need to change the entry in /etc/fstab. Could you post the entry you have now in your fstab?

If you don't have an entry, you'll need to create one. And to do that you should find the UUID by running the command
```
sudo blkid /dev/sdf1
```

With the UUID, you can create an entry that looks something like this
```
UUID=ABCD1234... /media/FreeAgent\040Drive ntfs-3g defaults,uid=gil,gid=admin,dmask=002,fmask=113 0 0
```

That fstab line will make all files and folder owned by the user gil and the group admin. The user gil and members of the admin group will have write permissions while everyone else will only have read permissions.

Also, since the mountpoint has a space in it and fstab uses spaces as field delimiter, you need to use the special sequence \040 to represent the space. 040 is the octal value of a space.

When the entry is created, unmount the filesystem, make sure the mountpoint exists, then mount it again.
```

sudo umount "/media/FreeAgent Drive"
sudo mkdir "/media/FreeAgent Drive"
sudo mount "/media/FreeAgent Drive"

```

---

### Post by socref on 2008-12-08
> **geirha said:**
> HPFS/NTFS. That means it has an NTFS filesystem. Permissions on NTFS filesystems in linux is not supported. That's why those changes doesn't stick. What is done instead, is that the permissions and ownership for all files are set when the filesystem is mounted, and currently root is set as the owner. You'll need to change the entry in /etc/fstab. Could you post the entry you have now in your fstab?

If you don't have an entry, you'll need to create one. And to do that you should find the UUID by running the command
```
sudo blkid /dev/sdf1
```

With the UUID, you can create an entry that looks something like this
```
UUID=ABCD1234... /media/FreeAgent\040Drive ntfs-3g defaults,uid=gil,gid=admin,dmask=002,fmask=113 0 0
```

That fstab line will make all files and folder owned by the user gil and the group admin. The user gil and members of the admin group will have write permissions while everyone else will only have read permissions.

Also, since the mountpoint has a space in it and fstab uses spaces as field delimiter, you need to use the special sequence \040 to represent the space. 040 is the octal value of a space.

When the entry is created, unmount the filesystem, make sure the mountpoint exists, then mount it again.
```

sudo umount "/media/FreeAgent Drive"
sudo mkdir "/media/FreeAgent Drive"
sudo mount "/media/FreeAgent Drive"

```


OK, below I have attached the output of /etc/fstab (don't speak this language). :lolflag: 

I don't see a UUID associated with this external drive -- only with the three partitions on the internal drive, correct? 

So do I go forward with the commands you've suggested or am I overlooking something? 

Is there a space between the UUID and /media in this command you suggested:

Code:
UUID=ABCD1234... /media/FreeAgent\040Drive ntfs-3g defaults,uid=gil,gid=admin,dmask=002,fmask=113 0 0


Then when I get to this point, do I include the quotation marks (") you show?

Code:
sudo umount "/media/FreeAgent Drive"
sudo mkdir "/media/FreeAgent Drive"
sudo mount "/media/FreeAgent Drive" 


Thanks, and here's the output of /etc/fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2b212aec-4f22-48bb-89b3-0af5b7aed634 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=b69f9d36-2e98-4b23-bb53-017c2b7c984d /home           jfs     relatime        0       2
# /dev/sda3
UUID=e528387c-13e5-4a3c-818a-57301cd38a2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by geirha on 2008-12-08
> **socref said:**
> OK, below I have attached the output of /etc/fstab (don't speak this language). :lolflag: 

No problem. I sometimes forget which forum I'm answering in.

> **socref said:**
> 
I don't see a UUID associated with this external drive -- only with the three partitions on the internal drive, correct? 


Correct.

> **socref said:**
> 
So do I go forward with the commands you've suggested or am I overlooking something? 


Yes.

> **socref said:**
> 
Is there a space between the UUID and /media in this command you suggested:

Code:
UUID=ABCD1234... /media/FreeAgent\040Drive ntfs-3g defaults,uid=gil,gid=admin,dmask=002,fmask=113 0 0

Yes, each line of the file must contain 6 fields separated by whitespace, unless it is a comment (lines starting with #). The fields are explained in the man-page, which you can read by typing ```
man fstab
``` In short, it is: 

<source device> <mount point> <filesystem type> <options> <fs_freq> <fs_passno>

With source device being UUID=your-uuid, 
the mount-point being the directory in /media/,
filesystem type being ntfs-3g, 
and options being the comma-separated list of options uid=gil,gid=admin,etc..

The last two fields are a bit special. Just set them to 0.


> **socref said:**
> 
Then when I get to this point, do I include the quotation marks (") you show?

Code:
sudo umount "/media/FreeAgent Drive"
sudo mkdir "/media/FreeAgent Drive"
sudo mount "/media/FreeAgent Drive" 


Yes they are quite important, because for instance, the mkdir command can create several directories in one go, and you do that by seperating each directory by spaces, so if you run ```
mkdir /media/FreeAgent Drive
``` it will create two directories, /media/FreeAgent and Drive. The quotes tells it that the space in between is part of the directory name.

---

### Post by socref on 2008-12-08
> **geirha said:**
> HPFS/NTFS. That means it has an NTFS filesystem. Permissions on NTFS filesystems in linux is not supported. That's why those changes doesn't stick. What is done instead, is that the permissions and ownership for all files are set when the filesystem is mounted, and currently root is set as the owner. You'll need to change the entry in /etc/fstab. Could you post the entry you have now in your fstab?

If you don't have an entry, you'll need to create one. And to do that you should find the UUID by running the command
```
sudo blkid /dev/sdf1
```

With the UUID, you can create an entry that looks something like this
```
UUID=ABCD1234... /media/FreeAgent\040Drive ntfs-3g defaults,uid=gil,gid=admin,dmask=002,fmask=113 0 0
```

That fstab line will make all files and folder owned by the user gil and the group admin. The user gil and members of the admin group will have write permissions while everyone else will only have read permissions.

Also, since the mountpoint has a space in it and fstab uses spaces as field delimiter, you need to use the special sequence \040 to represent the space. 040 is the octal value of a space.

When the entry is created, unmount the filesystem, make sure the mountpoint exists, then mount it again.
```

sudo umount "/media/FreeAgent Drive"
sudo mkdir "/media/FreeAgent Drive"
sudo mount "/media/FreeAgent Drive"

```


OK, I tried but no luck creating the entry. Here is the output of the terminal with the first two commands you suggested:

gil@Phred:~$ sudo blkid /dev/sdf1
/dev/sdf1: UUID="BC6C66826C6636F4" LABEL="FreeAgent Drive" TYPE="ntfs" 
gil@Phred:~$ UUID="BC6C66826C6636F4" /media/FreeAgent\040Drive ntfs-3g defaults,uid=gil,gid=admin,dmask=002,fmask=113 0 0
bash: /media/FreeAgent040Drive: No such file or directory
gil@Phred:~$ 

I also tried it without the quotation marks around UUID="BC6C66826C6636F4"

No luck doing that either.

What next coach?

And once I get the permissions I still have to figure out how to format this external drive. I see that right clicking on the drive does not give me a quick and easy format option as is available in SuSE Linux.

Thx
socref

---

### Post by geirha on 2008-12-08
> **socref said:**
> 
gil@Phred:~$ UUID="BC6C66826C6636F4" /media/FreeAgent\040Drive ntfs-3g defaults,uid=gil,gid=admin,dmask=002,fmask=113 0 0
bash: /media/FreeAgent040Drive: No such file or directory


Ah sorry, that's not a command, but should be added to /etc/fstab by editing that file and inserting that line at the end. This should open /etc/fstab as root in gedit:
```
gksudo gedit /etc/fstab
```

> **socref said:**
> 
And once I get the permissions I still have to figure out how to format this external drive. I see that right clicking on the drive does not give me a quick and easy format option as is available in SuSE Linux.

Thx
socref

If you intend to partition and/or format it, then you need to do that before setting it up in /etc/fstab; formatting the partition will change the UUID. To repartition and format, install [gparted](apt://gparted). Once installed you'll find it under System -> Administration -> Partition Editor. You'll need to make sure it is unmounted or else gparted will refuse to do anything with it.

---

### Post by socref on 2008-12-08
> **geirha said:**
> Ah sorry, that's not a command, but should be added to /etc/fstab by editing that file and inserting that line at the end. This should open /etc/fstab as root in gedit:
```
gksudo gedit /etc/fstab
```



If you intend to partition and/or format it, then you need to do that before setting it up in /etc/fstab; formatting the partition will change the UUID. To repartition and format, install [gparted](apt://gparted). Once installed you'll find it under System -> Administration -> Partition Editor. You'll need to make sure it is unmounted or else gparted will refuse to do anything with it.

OK, I followed the instructions, unmounted the drive, and used gparted to format the drive. That went fine.

Sorry that I misunderstood "entry" was not something that goes into the terminal but, rather, was to be appended to /etc/fstab. I did that in gedit following your instructions.

Here is the new UUID:

gil@Phred:~$ sudo blkid /dev/sdf1
[sudo] password for gil: 
/dev/sdf1: UUID="5cd236c1-9e04-43e3-8d41-651080d7cb8a" 

And I took that, put it into the entry you provided and pasted it as the last line in /etc/fstab

UUID="5cd236c1-9e04-43e3-8d41-651080d7cb8a" /media/FreeAgent\040Drive ntfs-3g defaults,uid=gil,gid=admin,dmask=002,fmask=113 0 0

Then the final three commands:

gil@Phred:~$ sudo umount "/media/FreeAgent Drive"
umount: /media/FreeAgent Drive: not found
gil@Phred:~$ sudo mkdir "/media/FreeAgent Drive"
gil@Phred:~$ sudo mount "/media/FreeAgent Drive"

But still problems. An icon for the drive appears on my desktop. It is labeled "500.1 GB Media." If I click on that, a folder appears in the disk-1 file browser labeled "lost+found." I cannot drag and drop anything into the hard drive.

If I right click on the drive icon on the desktop and go to the permissions tab it says: The permissions of "disk-1" could not be determined. 

So I went to a terminal and typed gksudo nautilus /media. The drive appears in the media file browser. Here it is labeled "FreeAgent Drive." And I can change permissions here, and I can drag and drop here. 
Owner: gil
Folder access: Create and delete files
File access: (Changes won't stick here)

Group: admin
Folder access: Create and delete files
File access: (Again, the changes won't stick here)

But these changes are only in /. 

Nothing has changed in my /home for the new HD. I still can't change permissions there and now I cannot drag and drop into the HD whereas before I could.

Ack!!!  :confused:

socref

---

### Post by geirha on 2008-12-08
> **socref said:**
> 
gil@Phred:~$ sudo blkid /dev/sdf1
[sudo] password for gil: 
/dev/sdf1: UUID="5cd236c1-9e04-43e3-8d41-651080d7cb8a" 

Aha, you've formatted it as ext3(?). That changes things a little bit since ext3 handles permissions and ownership.

> **socref said:**
> 
And I took that, put it into the entry you provided and pasted it as the last line in /etc/fstab

UUID="5cd236c1-9e04-43e3-8d41-651080d7cb8a" /media/FreeAgent\040Drive ntfs-3g defaults,uid=gil,gid=admin,dmask=002,fmask=113 0 0

Since you changed it from NTFS to ext3(?), you'll need to change the filesystem type and options for the fstab entry:
```
UUID="5cd236c1-9e04-43e3-8d41-651080d7cb8a" /media/FreeAgent\040Drive ext3 defaults 0 0
```

> **socref said:**
> 
Then the final three commands:

gil@Phred:~$ sudo umount "/media/FreeAgent Drive"
umount: /media/FreeAgent Drive: not found
gil@Phred:~$ sudo mkdir "/media/FreeAgent Drive"
gil@Phred:~$ sudo mount "/media/FreeAgent Drive"


After changing the fstab entry to reflect that the partition has ext3 filesystem, you need to run the umount and mount command again (you've already created the directory so mkdir is not needed any more). After that, you should be able to change the permissions and ownership on the drive via gksudo nautilus like you just tried.

> **socref said:**
> 
But still problems. An icon for the drive appears on my desktop. It is labeled "500.1 GB Media." If I click on that, a folder appears in the disk-1 file browser labeled "lost+found." I cannot drag and drop anything into the hard drive.

If I right click on the drive icon on the desktop and go to the permissions tab it says: The permissions of "disk-1" could not be determined. 


Possibly because you mounted it as ntfs when it is ext3, though I'm not quite certain ...

---

### Post by socref on 2008-12-08
> **geirha said:**
> Aha, you've formatted it as ext3(?). That changes things a little bit since ext3 handles permissions and ownership.


Since you changed it from NTFS to ext3(?), you'll need to change the filesystem type and options for the fstab entry:
```
UUID="5cd236c1-9e04-43e3-8d41-651080d7cb8a" /media/FreeAgent\040Drive ext3 defaults 0 0
```



After changing the fstab entry to reflect that the partition has ext3 filesystem, you need to run the umount and mount command again (you've already created the directory so mkdir is not needed any more). After that, you should be able to change the permissions and ownership on the drive via gksudo nautilus like you just tried.



Possibly because you mounted it as ntfs when it is ext3, though I'm not quite certain ...


Deep sigh... :confused:

I started from scratch by formatting the drive. Then went through all the steps again including getting a new UUID. Used the newest entry for /etc/fstab to reflect ext3 rather than ntfs file system. (Sorry, I thought then when my initial post said "No Windoze" that would have implied I wanted to format this drive for Linux and would not use ntfs. My apologies for not being more specific and for not being astute enough to realize that the entry you originally suggested specified ntfs.)

Present condition: I can now drag and drop into the file browser window that opens when I click the HD icon on my desktop. However, I **cannot** create new folders in that browser window (as I can in the browser window for the internal HD on which I do have permissions). And I still cannot change the permissions on the external drive from root. 

I think we're making progress but?? :lolflag:

Here is what I did:

gil@Phred:~$ sudo blkid /dev/sdf1
/dev/sdf1: UUID="7557cc0f-8c00-4d0f-9014-4502468daab9" SEC_TYPE="ext2" TYPE="ext3" 

Then created the entry for /etc/fstab and pasted it in as the last line:

UUID="7557cc0f-8c00-4d0f-9014-4502468daab9" /media/FreeAgent\040Drive ext3 defaults 0 0

Then the final commands:

gil@Phred:~$ sudo umount "/media/FreeAgent Drive"
umount: /media/FreeAgent Drive: not mounted
gil@Phred:~$ sudo mount "/media/FreeAgent Drive"
mount: special device /dev/disk/by-uuid/7557cc0f-8c00-4d0f-9014-4502468daab9 does not exist

Is the "does not exist" at the end of the line above a problem? 

Then used gksudo to try to change permissions:

gil@Phred:~$ gksudo nautilus /media
seahorse nautilus module initializedInitializing nautilus-share extension
gil@Phred:~$ 

Sorry that this is dragging on so long.
Thx!
socref

---

### Post by geirha on 2008-12-08
> **socref said:**
> 
gil@Phred:~$ sudo umount "/media/FreeAgent Drive"
umount: /media/FreeAgent Drive: not mounted
gil@Phred:~$ sudo mount "/media/FreeAgent Drive"
mount: special device /dev/disk/by-uuid/7557cc0f-8c00-4d0f-9014-4502468daab9 does not exist

Is the "does not exist" at the end of the line above a problem? 


Yes, that means it didn't get mounted. When you reformatted, it got a new UUID. Mount needs a special link in /dev/disk/by-uuid that points to the actual block device, but this does not get created automatically. Sorry I forgot about that. You need to restart udev for that to get set up.
```
sudo /etc/init.d/udev restart
```
A restart would fix it too.

After that, try mounting again, and try changing ownership from the terminal. The error messages the terminal commands give are often more descriptive than the ones the GUI gives ... at least for me :)

```
sudo mount "/media/FreeAgent Drive"
sudo chown gil:gil "/media/FreeAgent Drive"

```

> **socref said:**
> 
Sorry that this is dragging on so long.
Thx!
socref

No worries. 

«The time you enjoy wasting is not wasted time.» -- Bertrand Russell.

---

### Post by socref on 2008-12-08
More info.

When I look in /media file browser I see two interesting folders:

One is labeled "disk" and the other is labeled "FreeAgent Drive."

When I right click on "disk," then properties, and then the basic tab I am told that total capacity is 462.1GB of which 23.5GB are used and 438.6 GB are free.

But when I right click on "FreeAgent Drive," then properties, and then the basic tab I am told that total capacity is only 9.2GB of which 3.9GB are used and 5.3GB are free.

I wonder what this 9.2GB FreeAgent Drive is? 

And I wonder why the icon representing the drive on my desktop is labeled 500.1 GB Media (and I cannot change that label).

My head is spinning and my brain hurts!! :lolflag:

socref

---

### Post by geirha on 2008-12-08
> **socref said:**
> More info.

When I look in /media file browser I see two interesting folders:

One is labeled "disk" and the other is labeled "FreeAgent Drive."

When I right click on "disk," then properties, and then the basic tab I am told that total capacity is 462.1GB of which 23.5GB are used and 438.6 GB are free.

But when I right click on "FreeAgent Drive," then properties, and then the basic tab I am told that total capacity is only 9.2GB of which 3.9GB are used and 5.3GB are free.

I wonder what this 9.2GB FreeAgent Drive is? 

And I wonder why the icon representing the drive on my desktop is labeled 500.1 GB Media (and I cannot change that label).

My head is spinning and my brain hurts!! :lolflag:

socref

If there isn't a matching entry (that works) in fstab, gnome will mount external partitions automatically, and mount them to /media/disk, then /media/disk-1, /media/disk-2, etc... so /media/disk is probably your new filesystem, and the info on "FreeAgent Drive" is most likely just the info on the / filesystem.

Come to think of it, it might be just easier to have gnome mount the drive, since you don't need any special mount options on it now that it is ext3. You can change the mount-point by altering the label on the drive. If you choose that path, then remove the fstab entry again, unmount the drive, run e2label on it, and also remove the mount-point we created for the fstab entry:
```
sudo umount /dev/sdf1
sudo rmdir "/media/FreeAgent Drive"
sudo e2label /dev/sdf1 "FreeAgent Drive"

```
unplug it, and plug it back in, and it should pop up as "FreeAgent Drive" on your desktop. If you want it to be called something else, change "FreeAgent Drive" on the e2label command to whatever you like (but it cannot be more than 16 characters)

You'll still need to change ownership of it though.

---

### Post by socref on 2008-12-08
> **geirha said:**
> 

(snips)

Come to think of it, it might be just easier to have gnome mount the drive, since you don't need any special mount options on it now that it is ext3. You can change the mount-point by altering the label on the drive. If you choose that path, then remove the fstab entry again, unmount the drive, run e2label on it, and also remove the mount-point we created for the fstab entry:
```
sudo umount /dev/sdf1
sudo rmdir "/media/FreeAgent Drive"
sudo e2label /dev/sdf1 "FreeAgent Drive"

```
unplug it, and plug it back in, and it should pop up as "FreeAgent Drive" on your desktop. If you want it to be called something else, change "FreeAgent Drive" on the e2label command to whatever you like (but it cannot be more than 16 characters)

You'll still need to change ownership of it though.

Yikes. Just a bit too fast for me and several thoughts run together. :o)

Step by step:

1) "If you choose that path..."  What path?  By "path" do you mean if I choose to take that approach? Or is this "path" in the sense of pointing to a file?

2) remove the fstab entry we did previously?

3) unmount the drive?

4) then...?

```
sudo umount /dev/sdf1
sudo rmdir "/media/FreeAgent Drive"
sudo e2label /dev/sdf1 "FreeAgent Drive"

```

5) then unplug and replug HD?

6) If I want to change the name to external_drive I assume I do NOT need the quotation marks since I'm not leaving a space. Correct?

What am I not understanding? Have I left out any steps or misstated anything?

Do I need to do the UUID thing again and then put back the line in /etc/fstab, or does this process preclude the need for all of that? (I think that is what you're implying.)

Also, as I mentioned way back at the beginning, I cannot restart the pooter with the HD plugged in. The pooter won't boot. Does any of this change your thoughts?

Thx
socref

---

### Post by geirha on 2008-12-09
Good morning!

> **socref said:**
> 
1) "If you choose that path..."  What path?  By "path" do you mean if I choose to take that approach? Or is this "path" in the sense of pointing to a file?

Yes, approach is probably a better word.

> **socref said:**
> 
2) remove the fstab entry we did previously?

Yes. Only needed to add one in order to set permissions and ownership on the ntfs filesystem. With ext3 you just use chown and chmod or nautilus to set permissions and ownership

> **socref said:**
> 
3) unmount the drive?

The filesystem should be unmounted when changing the label on it, so doing "sudo umount /dev/sdf1" first ensures that it is unmounted.

> **socref said:**
> 
4) then...?

```
sudo umount /dev/sdf1
sudo rmdir "/media/FreeAgent Drive"
sudo e2label /dev/sdf1 "FreeAgent Drive"

```

sudo umount /dev/sdf1  # unmount the filesystem on /dev/sdf1, wherever it may be mounted. (It appeared to be mounted at /media/disk according to your previous post.)

sudo rmdir "/media/FreeAgent Drive"  # rmdir is short for remove dir. If you add an entry in fstab, the mount point needs to exist and be a directory. Gnome is a bit "smarter" and creates the mount point when needed, and removes it when the drive is unmounted. So that directory we created is no longer needed. It doesn't matter if it is still there, but it's nice to remove it since it isn't needed anymore.

sudo e2label /dev/sdf1 "label"   # e2label is short for ext2 label. It changes labels for ext2 and ext3 filesystems. 

> **socref said:**
> 
5) then unplug and replug HD?


Yes, physically, to test that it gets mounted automatically as it should when you plug it in.

> **socref said:**
> 
6) If I want to change the name to external_drive I assume I do NOT need the quotation marks since I'm not leaving a space. Correct?

Correct. They are optional when you don't add a space in the name.

sudo e2label /dev/sdf1 "MyDrive"

is equivalent to

sudo e2label /dev/sdf1 MyDrive

> **socref said:**
> 
What am I not understanding? Have I left out any steps or misstated anything?

Do I need to do the UUID thing again and then put back the line in /etc/fstab, or does this process preclude the need for all of that? (I think that is what you're implying.)

Correct. You don't need the UUID and you don't need to have an entry in /etc/fstab since you don't need any special mount options for ext3.

> **socref said:**
> 
Also, as I mentioned way back at the beginning, I cannot restart the pooter with the HD plugged in. The pooter won't boot. Does any of this change your thoughts?


I missed that part. It could sound like your computer attempts to boot from your external drive when it is connected, but I can't be certain based on the information at hand. Do you see the Ubuntu splash screen before it stops? Do you see the GRUB menu?

If you don't see the splash screen or GRUB menu, then it probably tries to boot the external drive instead of the regular one. You can change that behavior in the BIOS setup. To enter the BIOS setup you'll need to consult the manual to your motherboard/computer. You hit a special key during the early stages of the boot, but the key is different depending on the motherboard manufacturer. Usually it is F2, F10 or the delete key. Once in the BIOS, there should be an option to change boot order, and there you can set it to boot internal drives before external.

I just did a search on that external drive and found this interesting page: [http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)

It installs e2fsprogs before running e2label, which indicates that it isn't installed by default, so make sure to install [e2fsprogs](apt://e2fsprogs).

And on the third part, if your drive also spins down like it says, then try running those sdparm commands on it. You want to run it on the harddrive, which is /dev/sdf (not /dev/sdf1 which is partition 1 on the drive).

EDIT: Hey, this was my 2000th post! :popcorn:

---

### Post by socref on 2008-12-09
> **geirha said:**
> Good morning!

(snips)

I missed that part. It could sound like your computer attempts to boot from your external drive when it is connected, but I can't be certain based on the information at hand. Do you see the Ubuntu splash screen before it stops? Do you see the GRUB menu?

If you don't see the splash screen or GRUB menu, then it probably tries to boot the external drive instead of the regular one. You can change that behavior in the BIOS setup. To enter the BIOS setup you'll need to consult the manual to your motherboard/computer. You hit a special key during the early stages of the boot, but the key is different depending on the motherboard manufacturer. Usually it is F2, F10 or the delete key. Once in the BIOS, there should be an option to change boot order, and there you can set it to boot internal drives before external.

I just did a search on that external drive and found this interesting page: [http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)

It installs e2fsprogs before running e2label, which indicates that it isn't installed by default, so make sure to install [e2fsprogs](apt://e2fsprogs).

And on the third part, if your drive also spins down like it says, then try running those sdparm commands on it. You want to run it on the harddrive, which is /dev/sdf (not /dev/sdf1 which is partition 1 on the drive).

EDIT: Hey, this was my 2000th post! :popcorn:

Good morning to you. Are you in OZ?

Status update: The entry in /etc/fstab has been removed. The external drive's permissions are changed and I can drag-and-drop into the drive. The name of the drive icon on the desktop has been changed! :guitar:

Your suggestions were great. Thanks. The website you pointed me to ([www.mattcutts.com](www.mattcutts.com)) was very informative. (e2fsprogs was already installed on my pooter by default.) I have not tried matt cutt's suggestions on changing the drive spin-down characteristics as I have not yet experienced a spin-down (nothing on the drive yet).

Now to the issue of rebooting the pooter with the external drive plugged in. It simply won't reboot. I checked the BIOS and the boot order is:

1) CD/DVD
2) hard drive
3) removable

I don't know what removable refers to... a USB card reader I have attached? It said removable before I had this external HD.

Anyway, the pooter tries to restart and displays the Dell splashscreen. Then it shows a screen that says "Boot from AHCI CD Rom" and there is a flashing cursor under the line of text.

At this point the system stalls and the process stays on this screen forever. It never advances to the screen that says "Grub loading..." unless I have previously unplugged the external HD. 

Finally, and I know this is incredibly stupid, I can't get the external drive to mount from the command line. I **can** unmount it with "umount /dev/sdf1" -- no problem. But if I try to mount using "mount /dev/sdf1" it tells me there is no entry in fstab. Do I have brain-lock and I'm trying the wrong command to mount, or is something amiss? 

The only way I can mount the drive is to unplug it and replug. As you can imagine, this is incredibly inconvenient, and not being able to restart the pooter unless I unplug the external drive is also incredibly inconvenient.

Thx, sensei :lolflag:
socref

---

### Post by geirha on 2008-12-09
> **socref said:**
> Good morning to you. Are you in OZ? No, I'm in Norway. What does OZ stand for?

> **socref said:**
> 
Status update: The entry in /etc/fstab has been removed. The external drive's permissions are changed and I can drag-and-drop into the drive. The name of the drive icon on the desktop has been changed! :guitar:

Your suggestions were great. Thanks. The website you pointed me to ([www.mattcutts.com](www.mattcutts.com)) was very informative. (e2fsprogs was already installed on my pooter by default.) I have not tried matt cutt's suggestions on changing the drive spin-down characteristics as I have not yet experienced a spin-down (nothing on the drive yet).


Excellent.
> **socref said:**
> 
Now to the issue of rebooting the pooter with the external drive plugged in. It simply won't reboot. I checked the BIOS and the boot order is:

1) CD/DVD
2) hard drive
3) removable

I don't know what removable refers to... a USB card reader I have attached? It said removable before I had this external HD.

Anyway, the pooter tries to restart and displays the Dell splashscreen. Then it shows a screen that says "Boot from AHCI CD Rom" and there is a flashing cursor under the line of text.

At this point the system stalls and the process stays on this screen forever. It never advances to the screen that says "Grub loading..." unless I have previously unplugged the external HD. 


Removable stands for any storage device not connected inside the computer I think, so your external drive should fall under that category. I tried a little google search for freeagent drive, and this is the closest I found to a possible work around. 
[http://stx.lithium.com/stx/board/message?board.id=freeagent&message.id=195](http://stx.lithium.com/stx/board/message?board.id=freeagent&message.id=195)
the seventh post seems promising. 

> **socref said:**
> 
Finally, and I know this is incredibly stupid, I can't get the external drive to mount from the command line. I **can** unmount it with "umount /dev/sdf1" -- no problem. But if I try to mount using "mount /dev/sdf1" it tells me there is no entry in fstab. Do I have brain-lock and I'm trying the wrong command to mount, or is something amiss? 

The only way I can mount the drive is to unplug it and replug. As you can imagine, this is incredibly inconvenient, and not being able to restart the pooter unless I unplug the external drive is also incredibly inconvenient.

Thx, sensei :lolflag:
socref

Why do you unmount it? Do you unmount it to power it down when you don't use it perhaps?

Anyway, to mount it on the command line you'll need to either add an entry for it in /etc/fstab (again :)), or supply all the needed information to the mount-command, which is source device and mount point in your case.
```
sudo mount /dev/sdf1 /media/SomeName
```

The mount-point must exist when using the mount command, so you'll need to create the mount-point with mkdir (or nautilus).

---

### Post by socref on 2008-12-09
> **geirha said:**
> No, I'm in Norway. What does OZ stand for?




Removable stands for any storage device not connected inside the computer I think, so your external drive should fall under that category. I tried a little google search for freeagent drive, and this is the closest I found to a possible work around. 
[http://stx.lithium.com/stx/board/message?board.id=freeagent&message.id=195](http://stx.lithium.com/stx/board/message?board.id=freeagent&message.id=195)
the seventh post seems promising. 



Why do you unmount it? Do you unmount it to power it down when you don't use it perhaps?

Anyway, to mount it on the command line you'll need to either add an entry for it in /etc/fstab (again :)), or supply all the needed information to the mount-command, which is source device and mount point in your case.
```
sudo mount /dev/sdf1 /media/SomeName
```

The mount-point must exist when using the mount command, so you'll need to create the mount-point with mkdir (or nautilus).


OK, in order: OZ is Australia. When you said "no worries" in a previous post I thought you might be there. :o)

I am **very** impressed by your exceptional proficiency in English. English is such an illogical language in its spelling, pronunciation, and use of idioms that I am in awe of accomplished non-native speakers.

I thoroughly reviewed the message board website you pointed to and saw multiple instances of the same problem I'm having. Unfortunately none of the BIOS setting changes described there can be done on my Dell (the described settings don't exist in my version of the BIOS). So it appears that I am stuck having to unplug the external HD at restart or shut down, then plug back in after the pooter has arrived at the desk top. 

Next, why do I unmount the HD? Because of the problem restarting or cold-starting. If the HD is plugged in then I can't get the machine to boot up.

Next, thanks for pointing out where I was using an incomplete command to mount the HD. It now mounts and unmounts from the command line.  :o)

Geirha, thanks so much for all your help through this. You have been very patient with a relative Linux newbie. Though I have used SuSE for several years I am trying to learn Ubuntu. I have only the most rudimentary understanding of the command line, and I found SuSE easier for a GUI-based newbie.

Its GUI and KDE just seem to do allow tasks to be done with a lesser level of "computer-speak" (e.g., right clicking on a drive in SuSE allows you to call up an option to format the drive). Ubuntu and Gnome seem to require a more detailed understanding of the **underlying processes** (command line expertise) that cause things to work rather than being able to accomplish a task by knowing where to click. :o)

I really like Ubuntu, and I'm going to continue using it. But Ubuntu is a challenge for someone who is utterly dependent on the GUI and not accomplished in command line operations.

Anyway, you are a great resource to this forum, and I thank you.
socref

---

