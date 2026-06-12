---
title: "Cant copy files to a newly formated drive (9.10)"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Hans-Black on 2010-05-04
HI All i hope you can help me

I had 2 internal NTFS drives i coped the files from them to an external drive and formatted them (with gparted as ext 3) now i cant copy the files back to the drive i get told i don't have the permissions, what have i done wrong?

---

### Post by WiReIs on 2010-05-04
how big are the files you are transferring?

---

### Post by Hans-Black on 2010-05-04
the largest file size is about 2gb,

---

### Post by Morbius1 on 2010-05-04
If you formatted them with ext3 then they will mount with owner = root and permissions set to 755 - root can read and write but everyone else can only read.

You need to either change ownership of the mount point,. For example:
```
sudo chown -R morbius /mountpoint
```OR change permissions
```
 sudo chmod -R 0777 /mountpoint
```Or any variation in between.

I'm assuming these are just data partitions and not another Linux OS. You don't want to be changing ownership and permissions on a linux system partition.

---

### Post by ScottinSoCal on 2010-05-04
I've got a similar situation with my laptop - it has a secondary hard drive installed in the module bay. I mounted it under my home directory (/home/[username]) and I have all the permissions I need.

And my other half, who occasionally logs onto my laptop, doesn't have access. It's best that way.;)

---

### Post by ScottinSoCal on 2010-05-04
On reflection, if you're asking that question, you may not know how to change the mount point. Open a terminal window and type in:

sudo gedit /etc/fstab

Enter your password when prompted and it will bring your fstab file up in a text editor. Go down to the bottom of the file and add a new line, similar to this:

UUID=[your hd's UUID] /home/[username]/Storage ext3 defaults 0 0

To get your hard drive's UUID, open another terminal window and type in

sudo blkid

Enter your password when prompted, and it will display the UUID for every device it can find in your system. Copy and paste the one you need into the new entry in fstab. Reboot and your drive will be mounted under your home directory - you'll have full access, but no one else will.

Edited to add:
Whatever you're using as a mount point (in the example above, it's /home/[username]/Storage) you *must* have a folder named *exactly* the same thing in your home directory. Capitalization matters. If you use a cap letter in the fstab file, the folder has to have the same cap letter. And, in case it isn't obvious, replace [username] with your user name.

---

### Post by Maringouin on 2010-05-05
ScottinSoCal,

I'd like to clarify my situation with you because I think you've provided the answer to my problem but I want to be sure!

I have an Asus EeePC 901, which as a 4GB SSD and a 16GB SSD. Originally I had the OS (Ubuntu Karmic Koala) on the 4GB drive and /home on the 16GB drive, but then the 4GB drive was getting too full for all the programmes I wanted to run, so I partitioned the 16GB drive in two, left /home where it was on sdb1 and put the OS (/) on sdb2. Everything is fine EXCEPT for the original 4GB drive (sda) which I can't access now. I tried reformatting it to FAT32 but finally checked permissions (duh) and only root can change the permissions. Contents of fstab and fdisk -l appended at the end of this message. Somehow I managed to name the mountpoint as /data.

Do I just need to use the change ownership of mountpoint suggested earlier so that the owner is meg -- or should I change the mountpoint itself as in your last post? At the moment the partition is formatted as extended with a FAT32 partition but I would change that to ext4 (or ext3?) before proceeding with anything, if that's what I should do.

I'm not a very sophisticated Linux user but can follow instructions very well once I'm clear on them.

Your assistance is much appreciated. Thanks.

By the way, sdc is the SD card. I've been using it as a partition and it has my swap space on it. I'm probably going to remove that partition so I can swap cards more easily.

sudo gedit /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=5e9cd989-9689-4e49-abc8-6873f2bb172b /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda1 during installation
UUID=47cea96d-c740-4828-9bc2-d7274c10b4a3 /data           ext4    defaults        0       2
# /home was on /dev/sdb1 during installation
UUID=dab038d5-e4d4-46dc-adb2-5d53c0e8551f /home           ext4    defaults        0       2
# swap was on /dev/sdc2 during installation
UUID=35f78833-8dfd-479d-8cb8-5291ff861df7 none            swap    sw              0       0
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


sudo fdisk -l

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd643d643

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         490     3935893+   5  Extended
/dev/sda5               1         490     3935862    b  W95 FAT32

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         981     7879851   83  Linux
/dev/sdb2   *         982        1962     7879882+  83  Linux

Disk /dev/sdc: 8017 MB, 8017936384 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000a124

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             256         974     5775367+   b  W95 FAT32
/dev/sdc2               1         255     2048256   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Morbius1 on 2010-05-05
Maringouin, You really should start your own thread because your problem is quite different from the original posters'.

> Everything is fine EXCEPT for the original 4GB drive (sda) which I can't access now. I tried reformatting it to FAT32 but finally checked permissions (duh) and only root can change the permissions .....Somehow I managed to name the mountpoint as /data >  UUID=47cea96d-c740-4828-9bc2-d7274c10b4a3 /data           ext4    defaults        0       2> /dev/sda5               1         490     3935862    b  W95 FAT32Assuming my interpretation of your post is correct ( it's early here ;) ), you reformatted sda5 ( and has a mount point of /data ) as FAT32 but left your fstab entry as ext4.

You need to change that fstab entry to look something like this:
```
/dev/sda5 /data vfat utf8,umask=007,gid=46 0 2
```**umask=007** will give owner (root) and group ( 46 ) read/write permissions.
**gid=46** is the plugdev group and by default all local login users are members of the plugdev group.
So this will give all local login users read / write access to that partition. This is the old school way.:wink:

If you want to use "UUID=###" instead of "/dev/sda5" you won't be able to use the same uuid number that you had because uuid's for fat32 partitions have a different pattern than for ext4. You'll  need to issue the following command to find out what the correct uuid number is for that partition:

** sudo blkid -c /dev/null**

This will clean up the blkid cache and give you an accurate readout.

---

### Post by Hans-Black on 2010-05-05
> **ScottinSoCal said:**
> On reflection, if you're asking that question, you may not know how to change the mount point. Open a terminal window and type in:

sudo gedit /etc/fstab

Enter your password when prompted and it will bring your fstab file up in a text editor. Go down to the bottom of the file and add a new line, similar to this:

UUID=[your hd's UUID] /home/[username]/Storage ext3 defaults 0 0

To get your hard drive's UUID, open another terminal window and type in

sudo blkid

Enter your password when prompted, and it will display the UUID for every device it can find in your system. Copy and paste the one you need into the new entry in fstab. Reboot and your drive will be mounted under your home directory - you'll have full access, but no one else will.

Edited to add:
Whatever you're using as a mount point (in the example above, it's /home/[username]/Storage) you *must* have a folder named *exactly* the same thing in your home directory. Capitalization matters. If you use a cap letter in the fstab file, the folder has to have the same cap letter. And, in case it isn't obvious, replace [username] with your user name.

Hi ScottinSoCal

I edited my fstab and added the folders "Media" and "Secondry Data" to my home folder in the normal manner "right click>create folder" but i still cant copy things to them it still says I dont have the permissions. have i dont anything wrong in the fstab file?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=09df1a14-3d83-470e-9f21-871fce1fc692 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cb724627-26f8-4d34-875a-2269d2c96ac7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID="366c14d0-79f1-4fb1-9705-ce176b2c30de"/home/[myusername/Secondry Data ext3 defaults 0 0
UUID="649a3909-4d9f-4568-81c5-525dab57c0e8"/home/[myusername]/Media ext3 defaults 0 0 
```

---

### Post by Morbius1 on 2010-05-05
> UUID="366c14d0-79f1-4fb1-9705-ce176b2c30de"/home/[myusername/Secondry Data ext3 defaults 0 0
UUID="649a3909-4d9f-4568-81c5-525dab57c0e8"/home/[myusername]/Media ext3 defaults 0 0(1) Get rid of the quotes around the actual UUID number
(2) There needs to be a space between the actual uuid number and /home/[myusername]...
(3) Do yourself a favor and add a 2 at the end so your system does a filesystem check every now and then
[COLOR=Blue]EDIT: didn't work that right: Change the last "0" to a "2".[/COLOR]

You should end up with this:
```
UUID=366c14d0-79f1-4fb1-9705-ce176b2c30de /home/[myusername/Secondry Data ext3 defaults 0 2
UUID=649a3909-4d9f-4568-81c5-525dab57c0e8 /home/[myusername]/Media ext3 defaults 0 2
```NOTE: I assume you're using "myusername" as an alias because you don't want us to know what your real user name is. That needs to be a real username - you know that - right?

Now do a
```
sudo mount -a
```or reboot. 

You're still likely to need a chown or chmod but let's play along with the game and see where it goes.;)

---

### Post by Morbius1 on 2010-05-05
Just noticed something else:
> UUID=366c14d0-79f1-4fb1-9705-ce176b2c30de /home/[myusername/[COLOR=Blue]Secondry Data[/COLOR] ext3 defaults 0 2Can't have a space between [COLOR=Blue]Secondary[/COLOR] and [COLOR=Blue]Data[/COLOR]. You need to insert a "\040" there.
So that line should finally look like this:
```
UUID=366c14d0-79f1-4fb1-9705-ce176b2c30de /home/[myusername/Secondry\040Data ext3 defaults 0 2
```

---

### Post by ScottinSoCal on 2010-05-05
Um, yeah, what ^he^ said.
;)

Sorry I didn't respond earlier.

Just something to carry forward in your Ubuntu voyage - spaces aren't friendly. They're supported, kind of, but in general you should avoid them in directory and/or file names. If you use them, you'll wind up with situations like this, where you have to do some strange work-arounds. The situation is the same in Windows, but you're shielded from it most of the time by a heavy-handed OS that forces you to operate everything one or two steps removed.

---

### Post by Hans-Black on 2010-05-05
Thank you both for you help, the drives are now mounted as files in the home folder and on my desktop, but they are still only root accessible, the names "media" and "Secondry Data" are labels i added in the palimpsest Disk Utility could this be why its not giving me permissions? or do i need to run a  chown or chmod like Morbius1 says?

thanks

---

### Post by Morbius1 on 2010-05-05
Right now they should be owned by root with permissions set at 0755.
Root can read and write and everyone else ( that means you ) can only read.

The permissions are fine but I would suggest you change the ownership to you especially if you're the only user:

```
sudo chown myusername:myusername /home/[myusername]/Media
sudo chown myusername:myusername /home/[myusername]/"Secondry Data"
```Don't forget the quotes around [COLOR=Blue]Secondry Data

EDIT: If you have a problem after that then run: **sudo mount -a **in a terminal and if it gives you an error post it back here,
[/COLOR]

---

### Post by Hans-Black on 2010-05-05
> **Morbius1 said:**
> Right now they should be owned by root with permissions set at 0755.
Root can read and write and everyone else ( that means you ) can only read.

The permissions are fine but I would suggest you change the ownership to you especially if you're the only user:

```
sudo chown myusername:myusername /home/[myusername]/Media
sudo chown myusername:myusername /home/[myusername]/"Secondry Data"
```Don't forget the quotes around [COLOR=Blue]Secondry Data

EDIT: If you have a problem after that then run: **sudo mount -a **in a terminal and if it gives you an error post it back here,
[/COLOR]

thanks i tried the chown command bit i got the Error Message

```
chown: cannot access `/home/changed to my username/Media': No such file or directory 
```

but the Secondry Data one worked fine so i added tried /home/Username/"Media" and it worked fine, thank you for your help, 

Hans

---

### Post by Maringouin on 2010-05-06
Morbius,
My apologies for not starting a new thread; confusion and ignorance on my part.
Thank you for your prompt and complete reply.
I added a line to fstab as you indicated using "UUID=###" (obtained with the command you provided) and substituting tabs for the spaces, and the Data partition is now mounted and usable. 
Thanks again.
This forum is a really wonderful resource for people like me who have a lot to learn, and I'm very grateful to everyone who participates.

---

