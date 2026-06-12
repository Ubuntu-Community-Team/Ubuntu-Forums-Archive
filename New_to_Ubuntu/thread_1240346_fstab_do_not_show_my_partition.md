---
title: "fstab do not show my partition"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by andres-bracho on 2009-08-14
Hi,

I use Ubuntu 9.04 in double boot with Windows 7.

I have a third (FAT32) partition with my documents, I have to mount it every time and I want to make it permanent.

Every instruction I find say that I have to change some settings in the fstab file, but I can't find this partition on fstab, even with the partition mounted all that I can see there is the main ext3 partition with ubuntu and the fat32 partition. None of the other two.

What can I do to permanently mount the fat32 partition?

---

### Post by berthiggins on 2009-08-14
If the fat32 partition is not mounting automatically you will need to add its details to the fstab file.
This needs to be done very carefully as if you get it wrong you may bork your system.
so first make a backup with the command "sudo cp /etc/fstab /etc/fstabbackup"
Then sudo gedit /etc/fstab this will open the file which will look something like this 

 # / was on /dev/sdb1 during installation
UUID=72d85f2e-070e-4a69-878f-066d72635de7 /              ext2    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
The uuid part is a unique identifier for the hard disk in my laptop the slash is where it will mount into the system the ext2 is the filesystem on it and the rest are mounting options 
The /dev/scd0 is my cd/dvd drive
you need to add a line something like 

/dev/sdX /media/fatdisk vfat    defaults,   0    2 
Where the x is the correct drive letter 
you also need to create a folder for the disk to mount into ( in this case /media/fatdisk but you can call it whatever you like)

---

### Post by swerdna on 2009-08-14
For a full background and options, read here: [HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubufat32.html")

---

### Post by andres-bracho on 2009-08-18
It took a lot to find my own post... it's the first time I write on this forum...   ; )

Thanks for your answers but I can't find my partition's name... I know is something like sd4 or 5... but fdisk -l does not give me anything...

This if my current fstab:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=c2dc6f7c-18a0-4721-a5a8-7409edb88c14 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=16b4bc69-9ccf-4358-b693-7f38fb1b6d20 none            swap    sw              0       0

---

### Post by swerdna on 2009-08-18
Read the segment [Identifying your Partitions]("http://ubuntu.swerdna.org/ubufat32.html#blkid") in the tutorial I listed for you. You will find the UUID (like e.g. AD74-85CA) for your FAT32 partition by running this command:```
sudo blkid -L
```.Then make a mount directory with a command like this:```
sudo mkdir /path_to/mount_point
```Then put this line in the bottom of fstab:```
UUID=AD74-85CA     /path_to/mount_point     vfat     umask=0000,utf8     0 0
```(replace AD74-85CA with your real UUID).

First read the segment [Mounting a FAT32 partition permanently (with an entry in fstab)]("http://ubuntu.swerdna.org/ubufat32.html#permanent")in the tutorial that I listed for you.

---

### Post by andres-bracho on 2009-08-18
I followed this instructions step by step... after sudo mount -t vfat -o umask=0027,utf8 /dev/sda4 /media/documentos    I can't access the partition, it is not in "places"...   : (

Ok... I found what I did (umask=0027) and corrected it (open it as root with a right click script from gedit, unmounted, and mounted again with umask=0000)

Thank you very much...

Question, How can I make it read/write by me only?

---

### Post by PunkLV on 2009-08-18
**chmod 700 *folder***
Also, check out **man chmod** and **man chown**
Useful stuff this would be: [http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

---

### Post by swerdna on 2009-08-18
Change this:```
sudo mount -t vfat -o umask=0000,utf8 /dev/sda4 /media/documentos
```to this```
sudo mount -t vfat -o uid=your_username,gid=your_username,umask=0027,utf8 /dev/sda4 /media/documentos
```This time 0027 is correct.

---

### Post by swerdna on 2009-08-18
> **PunkLV said:**
> **chmod 700 *folder***
Also, check out **man chmod** and **man chown**
Useful stuff this would be: [http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

The FAT32 filesystem does not support Linux permissions or ownership. You can't successfully change ownership with the Linux command chown and you can't successfully change permissions with the Linux command chmod. Ownership and permissions are set only in the mount command.

The permissions and ownership properties that are available for FAT32 under Linux are not written into the individual files to be retained when the filesystem is unmounted or the computer is turned off. Permissions and ownership obtained under Linux are temporary artifices imposed via the mount command and maintained temporarily by the operating system. They are transient properties that last only until the filesystem is unmounted.

---

### Post by PunkLV on 2009-08-18
Guess now I have some reading to do. 
So setting up permissions for the mountpoint dir actually has no effect at all? If not to take root into account

---

### Post by swerdna on 2009-08-18
> **PunkLV said:**
> Guess now I have some reading to do. 
So setting up permissions for the mountpoint dir actually has no effect at all? If not to take root into account
None at all. The mountpoint automagically changes ownership and permissions during the instant of mounting -- to the ownership and permissions specified in the mount command -- if none are specisifed, the default ownership and permissions are applied, regardless of the pre-mount properties of the mountpoint. This is true for both NTFS and FAT/Vfat.
[FFI Fat32 here]("http://ubuntu.swerdna.org/ubufat32.html")
[FFI Ntfs here]("http://ubuntu.swerdna.org/ubuntfs.html")

---

### Post by andres-bracho on 2009-08-20
Thank you very much. I solved my question...

Now, how can I add a [solved] tag to the thread's tittle?

Regards.-

---

### Post by swerdna on 2009-08-20
Edit the first post and change the title

---

### Post by andres-bracho on 2009-08-20
Thanks for all swerda...

I found it... edit and then Advanced to change the title...   ; )

---

