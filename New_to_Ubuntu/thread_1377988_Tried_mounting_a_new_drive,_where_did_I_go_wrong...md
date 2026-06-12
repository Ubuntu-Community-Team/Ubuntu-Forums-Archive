---
title: "Tried mounting a new drive, where did I go wrong...?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by User X on 2010-01-10
fdisk -l  =


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x031d1d70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401   83  Linux

Disk /dev/sdb: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12b812b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4794    38507773+  83  Linux
/dev/sdb2            4795        5005     1694857+   5  Extended
/dev/sdb5            4795        5005     1694826   82  Linux swap / Solaris


I have formated sda1 as an ext4 file system and would like to mount it to /mnt/Media_Storage.  I opened terminal, ran: sudo gedit /etc/fstab, and entered: /dev/sda1 /mnt/Media_Storage ext4 default,umask=002 0 0.  See full fstab below:


# /etc/fstab: static file system information.
## Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=aa0085cf-a876-4287-8166-e021cbed5bc2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=92bc76bb-38d5-4d91-81ab-5dd020624d6a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /mnt/Media_Storage ext4 default,umask=002 0 0


The OS is Mythbuntu 9.10 running Xfce if that matters.  The boot device is ATA100, and the drive I am mounting is SATA.  I can tell its not working because If I check the available space in the /mnt/Media_Storage folder it is the size of the bootable partition (31Gb), and when I run:
sudo mount /dev/sda1 /mnt/Media_Storage, the available space jumps to 171Gb like it should.  I want it to mount on startup...

---

### Post by Ocxic on 2010-01-10
get rid of the umask option.

---

### Post by User X on 2010-01-11
Thats it?  Really?  I'll try it when I get home.  Thanks!

---

### Post by User X on 2010-01-13
I had to change the last line in the fstab file to:

/dev/sda1 /mnt/Media_Storage ext4 defaults 0 0

and then it worked.  Then I wanted to try this:

/dev/sda1/Videos /home/aaron/Videos ext4 defaults 0 0

but it didn't work...?  It seem that it is because I am mounting a path inside the drive, rather than the drive itself.  Is this not allowed, or how can I do this?  Thanks

---

### Post by Morbius1 on 2010-01-13
You've got two options I think. First is to make a symbolic link to the Videos directory. I always screw up symbolic links so I'll leave that to others.

There is another way:

I'm assuming the actual path to "Videos" is /mnt/Media_Storage/Videos and that you've already created the /home/aaron/Videos directory .

  Immediately after this line in fstab:
>  /dev/sda1 /mnt/Media_Storage ext4 defaults 0 0Add this line:
```
/mnt/Media_Storage/Videos /home/aaron/Videos auto bind 0 0
```Then from a Terminal issue a :

**sudo mount -a**

You'll immediately find out if it works or it does not  ;)

---

### Post by User X on 2010-01-15
So all of the mounting worked correctly, however, I can't create files/folders in the new drive using thunar?  Is this because I don't have permission?

---

### Post by Morbius1 on 2010-01-15
You will have to take ownership of the primary mount point. For example:

Open **Terminal**
Type [B]sudo chown -R morbius1:morbius1 /mnt/Media_Storage
[/B]
[I]This is just a storage partition right? This isn't holding some other linux os or your home folder or anything other than storage right. Because changing ownership in those cases will mess thing up.
[/I]

---

### Post by oldfred on 2010-01-15
Since my data partition had lots of folders I linked them.

I followed one of the comments here:
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

this becomes a mount that does not show in places except thru the links.
# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

I had about 14 entries like this in home since I could not get the little script to work from the above link.
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
ln -s /usr/local/fred/data/Pictures
ln -s /usr/local/fred/data/Videos

---

