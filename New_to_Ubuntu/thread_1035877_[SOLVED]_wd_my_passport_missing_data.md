---
title: "[SOLVED] wd my passport missing data"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by endofpage1 on 2009-01-10
let me preface this by saying i have only a very basic understand of ubuntu, as i have just started using it.  i have a wd my passport drive (new since the holidays) with all of my photos and music on it.  i've been using it regularly, as i listen to music using amarok configured to use my external hd's music folder as it's collection.  every time i plug in the hd, it is immediately recognized and an icon appears on the desktop.  starting yesterday, however, the data is inaccessible.  the folders in the drive appear, and any data which was not stored in a folder, but when the folders are opened, they are empty.  the space available on the drive (as calculated by ubuntu) indicates the data should still be present.  i had noticed previouslythat when i dismount the drive, if i leave it plugged in too long, it is re-mounted.  it is possible i disconnected it while this was happening.  i have a dual boot set up, so i checked the drive using windows (which i have not used with the external hd since ubuntu's install), and discovered the data seemed to be missing there as well.  back in ubuntu, i've run blkid, and fstab, and discovered that although the device icon is appearing on my desktop, it is not showing up in the file system table.  here is that data:

blkid

/dev/sda1: UUID="F888D49988D45828" TYPE="ntfs" 
/dev/sda3: UUID="1eef0cd0-62f4-40fd-810e-f713f171033d" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="427f86ba-0ed3-4cde-80b5-2bf3a8ad7f63" 
/dev/sda6: UUID="da459075-2bfb-4290-b8ba-6bee37dcd014" TYPE="ext3" 
/dev/sdb1: LABEL="My Passport" UUID="35C0-96B9" TYPE="vfat" 

fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1eef0cd0-62f4-40fd-810e-f713f171033d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=da459075-2bfb-4290-b8ba-6bee37dcd014 /home           ext3    relatime        0       2
# /dev/sda1
UUID=F888D49988D45828 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=427f86ba-0ed3-4cde-80b5-2bf3a8ad7f63 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


i'd really appreciate any help, and i'm really hoping there is a way to retrieve the data, as it would be in some cases impossible to replicate (photos).  if any other information is required, let me know.  thanks in advance.

---

### Post by blueridgedog on 2009-01-10
Can you post the output of the command ```
mount
```?

---

### Post by wolfen69 on 2009-01-10
i believe i heard these drives are not really linux compatible and will have problems. i don't have a link for it.

---

### Post by nhasian on 2009-01-10
your removeable drives are not going to show up in /etc/fstab unless you manually add them there.

it is possible that if you unplugged your drive without unmounting it,  you may have corrupted some data.  you should look into the programs [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec")

```
sudo apt-get install testdisk photorec
```

---

### Post by endofpage1 on 2009-01-11
> **blueridgedog said:**
> Can you post the output of the command ```
mount
```?

blueridgedog: here are the results of the mount command with the drive plugged in, and icon for the drive showing on desktop:

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda6 on /home type ext3 (rw,relatime)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kmm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kmm)
/dev/sdb1 on /media/My Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


thanks for the help.

---

### Post by endofpage1 on 2009-01-11
> **nhasian said:**
> your removeable drives are not going to show up in /etc/fstab unless you manually add them there.

it is possible that if you unplugged your drive without unmounting it,  you may have corrupted some data.  you should look into the programs [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec")

```
sudo apt-get install testdisk photorec
```


what are these programs for?  testdisk seems self explanatory, i suppose, but what is photorec's function?  actually, i should probably stop being lazy and just look them up.  thanks for the suggestion.

---

### Post by unutbu on 2009-01-11
What is the output of ```

ls -l "/media/My Passport/DIRNAME"
```
Change DIRNAME to an actual directory name.

It would be interesting to know if you can see any filenames inside, 
and if the listing looks normal, or if it is filled with funny question mark characters. 

If you can see the filenames using the terminal command ls, then your problem is probably not so bad. 

If you see nothing, or question marks then that is a sign that the filesystem needs to be checked with chkdsk. 

Do you have a Windows install CD? If so, boot it into Recovery Mode, and type
```
chkdsk /r
```
(See [http://vlaurie.com/computers2/Articles/chkdsk.htm](http://vlaurie.com/computers2/Articles/chkdsk.htm))
If you don't have a Windows install CD, you can download a Windows Repair CD here: [http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip](http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip)

----------------------------------------------------

Photorec is a recovery tool that comes along with the testdisk package. It reads partitions bit-by-bit and tries to recognize patches of bits as files. It can recognize many file formats: [http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

The problem is, it requires a recovery partition of equal size to the partition you are trying to recover, and secondly, when it finds a file, it does not know its proper filename, so it dumps it unceremoniously into one big folder with an unhelpful name,
like "f9826.jpg".

I would leave photorec as the option of last resort.

---

### Post by endofpage1 on 2009-01-11
thanks for all the help, i'm going to simply retrieve what data i can, format the drive, and start fresh.  i'm going to start a new thread for my dis-mount concerns with ubuntu.  thanks again.

---

