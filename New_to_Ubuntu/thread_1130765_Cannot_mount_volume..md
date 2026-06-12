---
title: "Cannot mount volume."
date: 2009-04-20
forum: New to Ubuntu
---

### Post by cycle_mycle on 2009-04-20
I am using Jaunty Beta but this is not a bug - it's a mistake on my part. I entered some parameters in the properties of a USB external hard drive. I had formated it with windows and chose FAT32 as the file system. Turns out it was formated ntfs.

So my problem is that since I entered vfat in the properties dialog box that comes up after right clicking on the drive and choosing properties. 

Now I get this message:

Cannot mount volume.
Error org.freedesktop.Hal.Device.UnknownError.
Details:
libhal.c 1399 : wrong reply from hald. Expecting an array.
org.freedesktop.Hal.Device.Volume.InvalidMountOption

The reason I entered the info in the properties is because I was not allowed to copy to the drive because I didn't have permission so along with the fs type I put in the options: 

rw,user.exec,auto

Can anyone please help me fix this?

Thanks for any help.

---

### Post by muteXe on 2009-04-20
Can you try editing the fstab file by hand?  It's located at /etc/  Make sure you back it up first.
Find the line that describes the drive you want to mount and change vfat to ntfs.  Something like this maybe:

```

/dev/hda1 /media/hda1 ntfs defaults 0 0

```

Put your paths in rather than the ones i've used tho.

---

### Post by cycle_mycle on 2009-04-20
Thank you for your quick reply.

I don't know what the drive designation is, I've looked...

Here's my fstab you can see that the drives not there. I guess since it's a USB drive it mounts under proc or mtab or something...

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7b40eae1-a9d5-44a8-95ce-e0446662b384 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=86eb5b11-1f33-42c4-a7a1-096afa6e07e5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

if I knew what the drive is being seen as (sdb1. etc...) i could do this.

Thanks again.

---

### Post by muteXe on 2009-04-20
Ah sorry, I just assumed you wanted it automatically mounted when you boot up.  Sorry about that.  I'm not being much help am I? :(
You can find out what the drive's called by doing
```
 sudo fdisk -l 
```
in a terminal, and finding it in the resulting output.

Maybe see if it's in your mtab then (when it's plugged in).  You might be able to change it in there, but I dont know much about that sorry mate.

---

### Post by cycle_mycle on 2009-04-20
No actually your being a great help, at least now I know what the drive is being designated as:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS

I guess I can just make it mount in the fstab for now and see if I can write to it by giving it auto for fs type...???

I'll see, thanks again.

---

### Post by cycle_mycle on 2009-04-20
OK!!!!

Got it done - thanks muteXe for your help!

Since you gave me the info on how to find what the mount point is I was able to edit fstab and:

sudo mount -t ntfs-3g -o w /dev/sdc1 /media/disk 

and now I can write to it.

I'll reformat in Ubuntu as FAT32 this time and that should also solve the permissions problem.

Thanks a great deal once again.

---

### Post by muteXe on 2009-04-20
Nice one :)

---

