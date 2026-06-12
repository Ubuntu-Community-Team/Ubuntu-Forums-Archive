---
title: "I messed up my fstab! - can no longer access or have limited access to most drives!"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Jayjay402 on 2010-05-29
I'm currently running ubuntu 10.04
I only recently got into linux and was already having trouble with it playing nice with external hdd's and usb pens. Tried altering my fstab and now it's worse!

This is what I usually get when something is plugged in:
[http://www.flickr.com/photos/jayjay402/4649998046/sizes/o/](http://www.flickr.com/photos/jayjay402/4649998046/sizes/o/)

And this is my fstab file in its current state:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=9a36492c-e91d-4451-8d14-a1a1ae6952cb  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=dac210e2-945c-4d53-9355-a6a317dfc111  none            swap         defaults                    0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb1                                  /media/sdb1     ext4         defaults                    0  0  
/dev/sdc1                                  /media/sdc1     ntfs         defaults                    0  0  Any help would be greatly appreciated, thank-you. :)

---

### Post by wojox on 2010-05-29
Comment out this and see what happens:

```

/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/sdb1 ext4 defaults 0 0
/dev/sdc1 /media/sdc1 ntfs defaults 0 0 

```

---

### Post by bildr on 2010-05-29
don't install from usb unless you expect this kind of problem, that or use UUIDs for all hard drives and pen drives.

---

### Post by Jayjay402 on 2010-05-30
Ok, I've searched around a lot, and found a whole bunch of stuff. I can no longer edit my fstab in any way in my acount but logged onto root and did it.

it now looks like this:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>                    <dump>  <pass>
UUID=9a36492c-e91d-4451-8d14-a1a1ae6952cb / ext3 defaults,errors=remount-ro,noatime 0 1
UUID=dac210e2-945c-4d53-9355-a6a317dfc111   swap defaults 0 0
UUID=879a1989-2cd6-420a-bb76-088f89e20de6 /media/80GB ext4 defaults 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

On boot-up I'm told that swap couldn't be detected.
The 80GB drive now works fine.
However I have two 2.5" external USB HDD's, both with the same enclosure. One is 60Gb and one is 500Gb. They both mount automatically and both have the same properties and permissions and are owned by my user and are read & write. The 60Gb behaves well. The 500Gb however is weird because I *can't* create or delete files to it and I have no idea as to why.

I installed ubuntu from a disk.

Any help would be greatly appreciated, thank-you! :)

---

### Post by Bob Bertrands on 2010-05-30
First of all execute ```
blkid
``` and  check if the uuid form the swap partition matches.

Also you didn't put in a mountpoint for the swap partition:
change 
```
UUID=dac210e2-945c-4d53-9355-a6a317dfc111   swap defaults 0 0
```
to
```
UUID=dac210e2-945c-4d53-9355-a6a317dfc111 none    swap sw 0 0
```

---

### Post by Bob Bertrands on 2010-05-30
Can you post the output of

```
sudo fdisk -l
```

---

### Post by Jayjay402 on 2010-05-30
Yep, the uuid matches, it's the bit that says 'none' I didn't know had to be put in. I thought I could just leave a few spaces as I read somewhere that swap had no mount point. I will change that next time I boot-up as I'll have to go into root.

sudo fdisk -l gives me this:

> jayen@jayen-desktop:~$ sudo fdisk -l
[sudo] password for jayen: 

Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ed14ed0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4795    38515806   83  Linux
/dev/sda2            4796        5005     1686825    5  Extended
/dev/sda5            4796        5005     1686793+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7be43df1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

Disk /dev/sdc: 500.1 GB, 500107859968 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb56d5ccf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    b  W95 FAT32

Disk /dev/sdd: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bbfe1d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7295    58597056    7  HPFS/NTFS
jayen@jayen-desktop:~$ 


Thanx for the prompt reply. :)

---

### Post by Bob Bertrands on 2010-05-30
can you post the output of this as well:

```
dmesg | grep sdc
```

---

### Post by Bob Bertrands on 2010-05-30
You're probably best of just changing your 500g drive from fat 32 to ntfs

B

---

### Post by Jayjay402 on 2010-05-30
I put that code in and don't get anything, just a blank line.

I need it in fat32 as I want to use it between ubuntu and my ps3 console.
Do you think if I backed up all of the data onto my laptop and then re-formatted it as fat32 within linux it would help?:)

Thanx again for the help!

---

### Post by Bob Bertrands on 2010-05-30
I don't suppose reformating will solve your problem.

I can't remember if the auto-mount of fat32 file system includes r/rw permissions.

You can try adding this line to your /etc/fstab file:

```
UUID= [uuid of filesystem, use command blkid]   [mountpoint]    vfat   rw,uid=[the output of command id -u jayen]  0    0 
```

---

### Post by Bob Bertrands on 2010-05-30
I remember having to set this uid= parameter as well when dealing with fat32 some time ago.
This will probably do the trick

---

### Post by formaldehyde_spoon on 2010-05-30
> **Jayjay402 said:**
> Ok, I've searched around a lot, and found a whole bunch of stuff. I can no longer edit my fstab in any way in my acount but logged onto root and did it.

it now looks like this:



On boot-up I'm told that swap couldn't be detected.
The 80GB drive now works fine.
However I have two 2.5&quot; external USB HDD's, both with the same enclosure. One is 60Gb and one is 500Gb. They both mount automatically and both have the same properties and permissions and are owned by my user and are read & write. The 60Gb behaves well. The 500Gb however is weird because I *can't* create or delete files to it and I have no idea as to why.

I installed ubuntu from a disk.

Any help would be greatly appreciated, thank-you! :)

You need to specify permissions or ownership in fstab for the FAT disk, else it will be listed as owned by root, and you will have read only permissions.

Put 'umask=000' in fstab to give full permissions for that disk to everyone,
and/or (probably a better option) 'uid'=1000' to set the ownership of that partition (and all the files in it) to you - assuming you are user 1000, the first user account (use ''grep yourUserName /etc/passwd'' to check)

---

### Post by Jayjay402 on 2010-06-01
My fstab is now like this:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>                    <dump>  <pass>
# File System - Partition 1 - (C: Drive)
UUID=9a36492c-e91d-4451-8d14-a1a1ae6952cb / ext3 defaults,errors=remount-ro,noatime 0 1
# Swap Space - Partition 2
UUID=dac210e2-945c-4d53-9355-a6a317dfc111 none swap defaults 0 0
#80GB ext4 Internal HDD
UUID=879a1989-2cd6-420a-bb76-088f89e20de6 /media/80GB ext4 defaults 0 0
# One of the Disc Drives (Not sure which though)
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Floppy Disk Drive
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
# 500GB External USB HDD - FAT32
UUID=10D8-132E /media/500GB Vfat rw,uid=1000 0 0

I added more comment lines to make it easier to see what's what.
I don't always have the drive plugged in at boot, so it tells me some error if I don't have it plugged in and says 's' to skip.
I plugged it in after and it didn't automount. I tried clicking on it in 'places' and it gave me this:

[http://www.flickr.com/photos/jayjay402/4658976777/sizes/o/](http://www.flickr.com/photos/jayjay402/4658976777/sizes/o/)

I'm sure everything looks right but am completely confused as to why it's still not working!
Thanx for the continued help guys!:)

---

### Post by formaldehyde_spoon on 2010-06-01
Try this:

# 500GB External USB HDD - FAT32 
UUID=10D8-132E /media/500GB vfat user,exec,suid,auto,relatime,dev,async,rw,uid=1000 0 0 

Note the lowercase v in vfat.

---

### Post by Jayjay402 on 2010-06-01
I realized about the capital V thing and already changed it.

I've put in the entry you've given me and when I go into permissions now the owner has at least changed to jayen, me.

The permissions now look like this:

[http://www.flickr.com/photos/jayjay402/4660144677/sizes/o/](http://www.flickr.com/photos/jayjay402/4660144677/sizes/o/)

For some reason the file access won't change, or will change but then changes straight back to as it is in the screenshot.

I still can't create or delete files on it.

The fact that the ownership of the drive has changed however makes me feel as if I'm getting somewhere. Thanx for the help and advice.:)

---

### Post by formaldehyde_spoon on 2010-06-01
> **Jayjay402 said:**
> I realized about the capital V thing and already changed it.

I've put in the entry you've given me and when I go into permissions now the owner has at least changed to jayen, me.

The permissions now look like this:

[http://www.flickr.com/photos/jayjay402/4660144677/sizes/o/](http://www.flickr.com/photos/jayjay402/4660144677/sizes/o/)

For some reason the file access won't change, or will change but then changes straight back to as it is in the screenshot.

I still can't create or delete files on it.

The fact that the ownership of the drive has changed however makes me feel as if I'm getting somewhere. Thanx for the help and advice.:) Add 'umask=022' to the options.

---

### Post by Bob Bertrands on 2010-06-02
you can try running id -g and using this output to set the gid parameter like this:

```
UUID=10D8-132E /media/500GB Vfat rw,uid=1000,gid=[output of id -g] 0 0                      
```

[formaldehyde_spoon]("http://ubuntuforums.org/member.php?u=1051636"),

Why these parameters: exec,relatime,dev & async ??

B

---

### Post by Jayjay402 on 2010-06-02
Ok, I've added both of your suggestions to my fstab and the permissions now look like this:

[http://www.flickr.com/photos/jayjay402/4662962194/sizes/o/](http://www.flickr.com/photos/jayjay402/4662962194/sizes/o/)

and when I change the file access under owner it changes back again. If I change anything else I get this:

[http://www.flickr.com/photos/jayjay402/4662340539/sizes/o/](http://www.flickr.com/photos/jayjay402/4662340539/sizes/o/)

Is it possible that I could permanently change these permissions through reformatting it. Or is there a drive manager of some sort that will let me do this?

---

### Post by Bob Bertrands on 2010-06-02
Fat32 filesystems don't have permissions. It's linux which handles the permissions so you'll need to specify those at boot, which you did.

So can you delete files/folder's without using root?

---

### Post by formaldehyde_spoon on 2010-06-02
> **Bob Bertrands said:**
> you can try running id -g and using this output to set the gid parameter like this:

```
UUID=10D8-132E /media/500GB Vfat rw,uid=1000,gid=[output of id -g] 0 0                      
```

gid is redundant if uid is already set.  > **Bob Bertrands said:**
>  
Why these parameters: exec, relatime, dev, async ??

B

relatime because there's no need to record every read access time (actually this is probably not necessary, because I think it's now become default)
async because otherwise the kernel won't buffer data being written, and system performance will suffer (included in 'defaults')
exec and dev because I am anticipating and heading off further posts in this thread! ;)  (these two also included in 'defaults')  > **Jayjay402 said:**
> Ok, I've added both of your suggestions to my fstab and the permissions now look like this:

[http://www.flickr.com/photos/jayjay402/4662962194/sizes/o/](http://www.flickr.com/photos/jayjay402/4662962194/sizes/o/)

and when I change the file access under owner it changes back again. If I change anything else I get this:

[http://www.flickr.com/photos/jayjay402/4662340539/sizes/o/](http://www.flickr.com/photos/jayjay402/4662340539/sizes/o/)

Is it possible that I could permanently change these permissions through reformatting it. Or is there a drive manager of some sort that will let me do this?

The screenshots are not particularly informative.  Post /etc/fstab, and the output from ''mount'' and ''sudo fdisk -l'' from after you boot, and before you do anything else.

It won't hurt to change the ownership/permissions of the mount point, either. That is, 'chown jayen /media/500GB' and/or  'chmod 755 /media/500GB'.

---

### Post by Jayjay402 on 2010-06-03
Well my fstab:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>                    <dump>  <pass>
# File System - Partition 1 - (C: Drive)
UUID=9a36492c-e91d-4451-8d14-a1a1ae6952cb  /                   ext3         defaults,errors=remount-ro,noatime  0  1  
# Swap Space - Partition 2
UUID=dac210e2-945c-4d53-9355-a6a317dfc111  none                swap         defaults                            0  0  
#80GB ext4 Internal HDD
UUID=879a1989-2cd6-420a-bb76-088f89e20de6  /media/80GB         ext4         defaults                            0  0  
# One of the Disc Drives (Not sure which though)
/dev/scd1                                  /media/cdrom0       udf,iso9660  user,noauto,exec,utf8               0  0  
# Floppy Disk Drive
/dev/fd0                                   /media/floppy0      auto         rw,user,noauto,exec,utf8            0  0  
# 500GB External USB HDD - FAT32
UUID=10D8-132E                             /media/500GB        vfat         user,exec,suid,auto,relatime,dev,async,rw,uid=1000,umask=022,gid=1000  0  0  

Output from mount:

> jayen@jayen-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,noatime,errors=remount-ro)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/80GB type ext4 (rw)
/dev/sdc1 on /media/500GB type vfat (rw,relatime,uid=1000,umask=022,gid=1000)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jayen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jayen)
jayen@jayen-desktop:~$ 


sudo fdisk -l :

> jayen@jayen-desktop:~$ sudo fdisk -l

Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ed14ed0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4795    38515806   83  Linux
/dev/sda2            4796        5005     1686825    5  Extended
/dev/sda5            4796        5005     1686793+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7be43df1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

Disk /dev/sdc: 500.1 GB, 500107859968 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb56d5ccf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    b  W95 FAT32
jayen@jayen-desktop:~$ 


Tried that last bit you said and got this back:

> jayen@jayen-desktop:~$ chown jayen /media/500GB
chown: changing ownership of `/media/500GB': Read-only file system
jayen@jayen-desktop:~$ chmod 755 /media/500GB
chmod: changing permissions of `/media/500GB': Read-only file system
jayen@jayen-desktop:~$ 


Hope this helps you to help me. Thanx!:)

---

### Post by formaldehyde_spoon on 2010-06-03
> **Jayjay402 said:**
> Well my fstab:



Output from mount:



sudo fdisk -l :



Tried that last bit you said and got this back:



Hope this helps you to help me. Thanx!:)

Sorry, I forgot to put 'sudo' in front of chown and chmod...
Also before you do those two, do this: sudo umount /dev/sdc1

Do you have a space after uid=1000??

If you umount, chown, chmod, and then reboot and it still isn't right, post the output from :
cd /media
ls -la
cd 500GB
ls -la

---

### Post by Jayjay402 on 2010-06-03
Ok, I did the Sudo umount, chown and chmod and rebooted, no changes though.

I'm not sure what is supposed to happen but this is what I got:

> jayen@jayen-desktop:~$ sudo umount /dev/sdc1
[sudo] password for jayen: 
jayen@jayen-desktop:~$ sudo chown jayen /media/500GB
jayen@jayen-desktop:~$ sudo chmod 755 /media/500GB
jayen@jayen-desktop:~$ I assume that's how it was supposed to work?

It appears I do have a space after uid=1000 in the earlier thread post but not in the real fstab, I just checked. It must have been some weird accidental typo or something.

I did those other commands at the end and got this:

```
jayen@jayen-desktop:~$ cd /media
jayen@jayen-desktop:/media$ ls -la
total 72
drwxr-xr-x  11 root  root   4096 2010-06-02 11:23 .
drwxr-xr-x  22 root  root   4096 2010-05-30 13:07 ..
drwxr-xr-x 121 jayen jayen 32768 1970-01-01 01:00 500GB
drwxr-xr-x   6 jayen jayen  4096 2010-06-01 13:50 80GB
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 AMIT
drwxr-xr-x   2 root  root   4096 2010-05-30 13:08 cdrom0
drwxr-xr-x   2 root  root   4096 2010-05-30 13:08 floppy0
-rw-r--r--   1 root  root      0 2010-06-02 10:37 .hal-mtab
-rw-------   1 root  root      0 2010-06-02 10:45 .hal-mtab-lock
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 JAYEN8GB
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 KINGSTON4GB
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 RESHETA_ZZZ
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 sdd1
jayen@jayen-desktop:/media$ cd 500GB
jayen@jayen-desktop:/media/500GB$ ls -la 
ls: cannot access &#65533;?&#65533;OU&#65533;?.}o?: Input/output error
ls: cannot access &#65533;&#65533;s&#65533;/w`r.Z&#65533;?: No such file or directory
&#65533;.a&#65533;?: Input/output error&#65533;?
ls: cannot access 0?z?n|.?&#65533;?: Input/output error
ls: cannot access .&#65533;: Input/output error
ls: cannot access &#480;,?&#65533;?.??: Input/output error
ls: cannot access &#65533;(d:??|.
a5: Input/output error
ls: cannot access 
                   &#65533;/U.k&#65533;: No such file or directory
ls: cannot access _`?&#65533;?..C&#65533;: Input/output error
ls: cannot access ?@&#65533;&#65533;q&#65533;.b&#65533;?: Input/output error
ls: cannot access ?    P&#65533;&#65533;&#65533;.1x4: Input/output error
{&#65533;w&#65533;?.7?: Input/output error
ls: cannot access t
&#65533;g.i]: Input/output error
ls: cannot access &#65533;&#65533;??{??.&#65533;t#: Input/output error
ls: cannot access `

x&#65533; &#65533;?.&#65533;: Input/output error
ls: cannot access ?9?b?A.?(?: Input/output error
ls: cannot access &#65533;q'&#65533;?&#65533;?.s!: Input/output error
ls: cannot access &#65533;s$&#65533;1&#65533;?.&#65533;O: Input/output error
ls: cannot access y?n._q&#65533;: Input/output error
ls: cannot access =?CpI/L.z?
                             : No such file or directory
ls: cannot access ?bq&#65533;?&#65533;`.`K?: Input/output error
ls: cannot access _
                     r&#65533;.??: Input/output error
ls: cannot access x>&#65533;m.??M: Input/output error
ls: cannot access ????\&#65533;..: Input/output error
ls: cannot access )?N?&#65533;?.?: Input/output error
ls: cannot access kx?/|<;K.?0&#65533;: No such file or directory
ls: cannot access &#65533;&#65533;?&#65533;???o.&#65533;&#65533;?: Input/output error
ls: cannot access &#65533;z?&#65533;Ycd&#65533;: Input/output error
ls: cannot access ?
                   &#65533;?&#65533;&#65533;&#65533;Y.?M
: Input/output error
ls: cannot access c^gC9&#65533;.s&#65533;&#65533;: Input/output error
ls: cannot access ??f??&#65533;&#65533;.?P?: Input/output error
ls: cannot access &#65533;m?&#65533;F
                        .&#65533;?d: Input/output error
ls: cannot access ??Ye??&#65533;&#65533;.???: Input/output error
?.???: Input/output error
ls: cannot access ??&#65533;&#65533;r,&#65533;i.-&#65533;?: Input/output error
ls: cannot access ?&#65533;<&#65533;&#65533;%q.ahy: Input/output error
ls: cannot access ??&#65533;&#65533;?Q?.Y&#65533;=: Input/output error
ls: cannot access &#65533;???Q?&#65533;?.&#65533;a: Input/output error
ls: cannot access 
                  ~&#65533;?j?.&#65533;p&#65533;: Input/output error
ls: cannot access &?ay&#65533;?: Input/output error
ls: cannot access P???L.?&#65533;&#65533;: Input/output error
ls: cannot access &#65533;?u1??.???: Input/output error
&#65533;&#65533;: Input/output error0<%4.
ls: cannot access ??P?
                      ???.&#65533;: Input/output error
ls: cannot access 8|
bA?&#65533;.&#65533;0&#65533;: Input/output error
ls: cannot access@5??!.*??: Input/output error
ls: cannot access ??[??v?.c??: Input/output error
ls: cannot access mf4r??s.&#65533;$]: Input/output error
: Input/output error&#65533;`J.
ls: cannot access ??r8?.?&#65533;: Input/output error
ls: cannot access ?P??>?&#65533;a.??: Input/output error
ls: cannot access t&#65533;&#65533;7qkj=.*/G: No such file or directory
ls: cannot access ?d?
&#65533;~&#65533;.
&#65533;: Input/output error
ls: cannot access &#65533;&#65533;?&#65533;?.;/: No such file or directory
ls: cannot access 
                  b?`

 .?=&#65533;: Input/output error
ls: cannot access ;p5?b}&#65533;.-i?: Input/output error
ls: cannot access x&#65533;N?l?.&#65533;m&#65533;: Input/output error
ls: cannot access &#65533;
&#65533;?&#65533;`=..&#65533;: Input/output error
ls: cannot access &#65533;;?V
                       &#65533;Y.?9?: Input/output error
ls: cannot access y?&#65533;??|&#65533;.&#65533;?q: Input/output error
ls: cannot access ~\%??.&#65533;&?: Input/output error
ls: cannot access &#65533;?&#65533;?~?f?.&#65533;fG: Input/output error
ls: cannot access .&#65533;?.?&#65533;: Input/output error
ls: cannot access &#65533;qv&#65533;&#65533;}$1.?: Input/output error
ls: cannot access !(?}?&#65533;./: No such file or directory
ls: cannot access ?K
                   `&#65533;?!.&#65533;: Input/output error
ls: cannot access ?~#?dd&#65533;i.?: Input/output error
ls: cannot access &#65533;&#65533;0&#65533;?
                        &#65533;.??a: Input/output error
ls: cannot access ?    ?S???i.?j&#65533;: Input/output error
ls: cannot access ?v6].??&#65533;: Input/output error
ls: cannot access ?&#65533;&#65533;&#65533;&#65533;?.??q: Input/output error
ls: cannot access ??&#65533;?&#65533;?: Input/output error
ls: cannot access &#65533;?&#65533;?mut.&#65533;&#65533;?: Input/output error
ls: cannot access &#65533;?&#65533;&#65533;.&#65533;??: Input/output error
ls: cannot access ?vl/d??y.??&#65533;: No such file or directory
ls: cannot access ?\\?.?&#65533;\.&#65533;|_: Input/output error
ls: cannot access ?&#65533;&#65533;?&#65533;x.\?: Input/output error
ls: cannot access 3??&#65533;?.??&#65533;: Input/output error
ls: cannot access ?&#65533;kx?N{&#65533;.???: Input/output error
ls: cannot access     &#65533;&#65533;n."?s: Input/output error
ls: cannot access ??x&#65533;HJ&#65533;._/.: No such file or directory
ls: cannot access 0b?2?&#65533;?.!&#65533;: Input/output error
ls: cannot access &#65533;_u?&#65533;?n.&#65533;&#65533;: Input/output error
ls: cannot access &#65533; c,Y    &#65533;.&#65533;&#65533;
                            : Input/output error
ls: cannot access &?&#65533;???..&#65533;&#65533;?: Input/output error
ls: cannot access ?p&#65533;<!&#65533;&#65533;.???: Input/output error
ls: cannot access ??y,3?c?.&#65533;y: Input/output error
ls: cannot access ?%qR
.?v?: Input/output error
ls: cannot access m?&#65533;d&#65533;?&#65533;.&#65533;&: Input/output error
ls: cannot access ^2??(-.???: Input/output error
ls: cannot access ?}T&#65533;|F?;.'.: No such file or directory
ls: cannot access l/u&#65533;    _j.&#65533;m&#65533;: No such file or directory
ls: cannot access |l

?&#65533;&#65533;??: Input/output error
ls: cannot access &#65533;>&#65533;.\&#65533;.p?: Input/output error
ls: cannot access ??>&#65533;??G.&#65533;\
                             : Input/output error
ls: cannot access ?
&#65533; &#65533;t.^%&#65533;: Input/output error
ls: cannot access ?p?h/. ?: No such file or directory
ls: cannot access ??&#65533;'&#65533;p&#65533;?.?7?: Input/output error
ls: cannot access ?/??&#65533;&#65533; : No such file or directory
ls: cannot access V>Df??.?&#65533;<: Input/output error
ls: cannot access ?A&#65533;?&#65533;|?&#65533;.Du&#65533;: Input/output error
ls: cannot access &#65533;?&#65533;???2.&#65533;&#65533;?: Input/output error
ls: cannot access ?&#65533;&#65533;m?&#65533;?.a0: Input/output error
ls: cannot access ??&#65533;&#65533;&#65533;d?.&#65533;?I: Input/output error
ls: cannot access &#65533;&#65533;j?&#65533;-.?y: Input/output error
ls: cannot access ?&#65533;???g.@u&#65533;: Input/output error
ls: cannot access 
                  ?D&#65533;jw&#65533;.??_: Input/output error
ls: cannot access &#65533;&#65533;_&#65533;???.???: Input/output error
ls: cannot access e?&#65533;&#65533;&#65533;?.ong: Input/output error
ls: cannot access &#65533;&#65533;r+<&#65533;?.'j8: Input/output error
ls: cannot access &#65533;&#65533;&#65533;&#65533;&#65533;?.?: Input/output error
ls: cannot access &#65533;??P
&#65533;??.??&#65533;: Input/output error
ls: cannot access x??i&#65533;s&#65533;?./?: No such file or directory
ls: cannot access G?2:&#65533;?R.v?: Input/output error
ls: cannot access &#65533;&#65533;??&#65533;/?.f`?: No such file or directory
ls: cannot access ?&#65533;&#65533;.x?: Input/output error
ls: cannot access &#65533;&#65533;on2o
                        x.?: Input/output error
ls: cannot access B?&#65533;<??.&#65533;?&#65533;: Input/output error
ls: cannot access  &#65533;$&#65533;1?&#65533;~.$    C: Input/output error
ls: cannot access `2?x8?4.: Input/output error
total 292880996
-rwxr-xr-x   1 jayen jayen 4030524432 2017-11-24 20:33 >?? ????.???
d?????????   ? ?     ?              ?                ? !(?}????.??/
-rwxr-xr-x   1 jayen jayen   69210305 1944-02-25 08:21 ?`@??`??.??@
d?????????   ? ?     ?              ?                ? ????\???.?.?
-rwxr-xr-x   1 jayen jayen 1109574925 2017-12-20 23:00 ????????.???
-r-xr-xr-x   1 jayen jayen 3226129265 1992-01-06 11:33 ?)??????.???
d?????????   ? ?     ?              ?                ? ?\\?.??\.?|_
-r-xr-xr-x   1 jayen jayen 4225063786 1906-06-08 13:45 ????????.???
-r-xr-xr-x   1 jayen jayen  679526819 1967-12-25 23:35 ?????!??.!??
drwxr-xr-x 121 jayen jayen      32768 1970-01-01 01:00 .
drwxr-xr-x  11 root  root        4096 2010-06-02 11:23 ..
-rwxr-xr-x   1 jayen jayen 2833983776 2007-12-01 18:24 ????????.??`
-rwxr-xr-x   1 jayen jayen  329450851 1943-02-18 19:32 ????????.??)
-r-xr-xr-x   1 jayen jayen 2696970793 2022-12-14 06:59 ???< ??=.?{?
d?????????   ? ?     ?              ?                ? ????????.???
-r-xr-xr-x   1 jayen jayen 3593104305 1966-08-05 17:57 ?.??+
-?????????   ? ?     ?              ?                ? ???????.;?/
-rwxr-xr-x   1 jayen jayen  174125056 1904-03-15 01:31 ??)?>???.???
d?????????   ? ?     ?              ?                ? ???_????.???
d?????????   ? ?     ?              ?                ? ??????`=..??
d?????????   ? ?     ?              ?                ? ?&?????..???
-rwxr-xr-x   1 jayen jayen 4030795852 1983-10-01 07:00 ?.?)?
d?????????   ? ?     ?              ?                ? ?.??????.???
d?????????   ? ?     ?              ?                ? ???.???
-r-xr-xr-x   1 jayen jayen 2942439610 1957-06-25 03:35 ????<??.???
d?????????   ? ?     ?              ?                ? ????????
d?????????   ? ?     ?              ?                ? ????????.???
d?????????   ? ?     ?              ?                ? ?~\>?%??.?&?
-rwxr-xr-x   1 jayen jayen 1817994962 2001-01-16 20:40 ???
-rwxr-xr-x   1 jayen jayen 2074925693 1950-10-21 21:29 *????0??.??5
d?????????   ? ?     ?              ?                ? ??0?????.??a
d?????????   ? ?     ?              ?                ? 0b??2???.!?
-r-xr-xr-x   1 jayen jayen   56907496 1983-02-09 10:00 ?????0D?.H?*
-rwxr-xr-x   1 jayen jayen 1292127250 1916-07-05 20:40 0hC???K@.,??
-rwxr-xr-x   1 jayen jayen    8586800 1986-08-26 16:02 <?!?`??0.?u?
d?????????   ? ?     ?              ?                ? ??0?z?n|.???
-r-xr-xr-x   1 jayen jayen 3690523862 1939-12-05 13:55 ???1??8?.?s?
d?????????   ? ?     ?              ?                ?  ?$?1??~.$?C
-r-xr-xr-x   1 jayen jayen  737161348 1968-05-24 18:10 ??$1?g??.???
-r-xr-xr-x   1 jayen jayen 3596600715 2011-03-15 18:48 1?t?????.z??
-rwxr-xr-x   1 jayen jayen 3245055613 1969-11-26 19:00 =?|?.?1x
-rwxr-xr-x   1 jayen jayen 4199614024 1985-02-02 00:48 (??1?x??.?+
d?????????   ? ?     ?              ?                ? ^2[???(-.???
d?????????   ? ?     ?              ?                ? ???????2.???
d?????????   ? ?     ?              ?                ? `2?x8??4.???
d?????????   ? ?     ?              ?                ? ?3??????.???
-rwxr-xr-x   1 jayen jayen 2043855317 2037-12-09 14:20 3???? ?_.???
-rwxr-xr-x   1 jayen jayen 1113405957 1942-11-28 05:07 ????????.)?4
d?????????   ? ?     ?              ?                ? ??@5???!.*??
-rwxr-xr-x   1 jayen jayen 1017139938 1984-03-13 15:05 5'?&#498;???.?p`
drwxr-xr-x   7 jayen jayen      32768 2010-04-24 10:57 60GB - Documents & Media - Backup
-r-xr-xr-x   1 jayen jayen 2138624075 1998-06-18 05:49 ??~?6?@?.??m
-rwxr-xr-x   1 jayen jayen  536355014 2020-02-28 11:21  @7??0^?..??
-r-xr-xr-x   1 jayen jayen 1019336519 1902-04-14 17:30 ?_??????.8??
-r-xr-xr-x   1 jayen jayen 2740994288 2016-01-16 03:03 ?8)???9?.?4?
d?????????   ? ?     ?              ?                ? 8|?b?A??.?0?
-r-xr-xr-x   1 jayen jayen  619811524 1954-12-23 06:28 .???8??.B?W
-rwxr-xr-x   1 jayen jayen  204015150 2036-07-03 22:00 8!?+.{G?
d?????????   ? ?     ?              ?                ? ?9???b?A.?(?
d?????????   ? ?     ?              ?                ? 9?{?w???.?7?
d?????????   ? ?     ?              ?                ? ????????.a??
d?????????   ? ?     ?              ?                ? &#480;,?????.???
-rwxr-xr-x   1 jayen jayen 2975671760 2001-03-02 07:19 a???????.??0
-r-xr-xr-x   1 jayen jayen 1345201027 2024-01-15 00:01 A?8~?>?V.?^?
drwxr-xr-x  11 jayen jayen      32768 2010-02-25 18:00 AA-Shows
-r-xr-xr-x   1 jayen jayen 1339621262 1934-04-08 23:25 ?A??A??.x??
d?????????   ? ?     ?              ?                ? ?A???|??.Du?
-r-xr-xr-x   1 jayen jayen 2736999861 1920-04-25 21:34 ?am?????.`??
-rwxr-xr-x   1 jayen jayen  793866512 1992-06-02 02:03 ??a ???p.???
-rwxr-xr-x   1 jayen jayen   88014256 2020-01-14 00:23 +??a??~?.??u
-r-xr-xr-x   1 jayen jayen 3341552469 2017-07-21 15:19 ???`av??.?X?
d?????????   ? ?     ?              ?                ? &?a?y???
-rwxr-xr-x   1 jayen jayen 3426822728 1923-07-21 22:08 A?}Z???o.???
d?????????   ? ?     ?              ?                ? ?b??`???.?=?
d?????????   ? ?     ?              ?                ? B????<??.???
d?????????   ? ?     ?              ?                ? ??B?0<%4.???
d?????????   ? ?     ?              ?                ? ?bq????`.`K?
-rwxr-xr-x   1 jayen jayen 2599636932 1962-09-28 00:22 ?b&??.??.-?t
-rwxr-xr-x   1 jayen jayen  806030499 1948-12-07 04:56 ????.C??
-rwxr-xr-x   1 jayen jayen   62813196 1961-02-25 09:04 ?????C??.???
d?????????   ? ?     ?              ?                ? ?_`????..C??
-r-xr-xr-x   1 jayen jayen 3128889807 2015-08-01 08:04 ????C???.?>2
-r-xr-xr-x   1 jayen jayen 3308779198 2009-01-18 03:52 ?????c??.8??
-r-xr-xr-x   1 jayen jayen 1744010782 1939-10-21 23:45 <?ca?a?u.?&%
d?????????   ? ?     ?              ?                ? c?^gC9??.s??
-?????????   ? ?     ?              ?                ? =??CpI/L.z??
-r-xr-xr-x   1 jayen jayen 1572777746 1995-02-01 00:19 ?C??)p?{.j??
d?????????   ? ?     ?              ?                ? ? c,?Y??.???
-r-xr-xr-x   1 jayen jayen 4095698967 1940-03-02 09:34 =d>?????.???
d?????????   ? ?     ?              ?                ? ?d????~?.???
-rwxr-xr-x   1 jayen jayen 3306712746 1963-08-06 20:26 )+?!d??_.??^
d?????????   ? ?     ?              ?                ? ??(d:??|.?a5
d?????????   ? ?     ?              ?                ? ?~#?dd?i.???
d?????????   ? ?     ?              ?                ? ??????d?.??I
d?????????   ? ?     ?              ?                ? ???D?jw?.??_
-rwxr-xr-x   1 jayen jayen 3172412529 1917-12-04 18:03 ??%#?+d%.??p
-rwxr-xr-x   1 jayen jayen 1463749660 1988-03-06 04:23 e???????.???
-r-xr-xr-x   1 jayen jayen 1429845025 1930-07-14 18:52 ??>??E?*.??{
-r-xr-xr-x   1 jayen jayen 4025668096 1940-04-25 22:55 E??????@.???
d?????????   ? ?     ?              ?                ? e???????.ong
-?????????   ? ?     ?              ?                ? ?????/??.f`?
-r-xr-xr-x   1 jayen jayen 4211863723 1980-12-23 03:01 ?????F??.???
d?????????   ? ?     ?              ?                ? ????~?f?.?fG
d?????????   ? ?     ?              ?                ? ???f????.?P?
-r-xr-xr-x   1 jayen jayen 3692023032 1986-01-15 07:04 F??;?^=U.???
-r-xr-xr-x   1 jayen jayen 4232738847 1955-03-02 08:40 f???X<??. ??
d?????????   ? ?     ?              ?                ? ??>????G.?\?
-rwxr-xr-x   1 jayen jayen 2013924320 1984-12-19 03:10 g???00dc.'?
d?????????   ? ?     ?              ?                ? G?2:???R.v??
-rwxr-xr-x   1 jayen jayen 1456428186 1909-12-01 21:41 ?g?d?0?f.???
-r-xr-xr-x   1 jayen jayen 4008270641 1921-03-20 23:55 ???g?g??.???
d?????????   ? ?     ?              ?                ? ???????g.@u?
-rwxr-xr-x   1 jayen jayen 1453279404 2026-10-28 06:53 ???@?.??.??h
-rwxr-xr-x   1 jayen jayen 4013944928 1971-07-20 21:34 ?+??'??h.???
-rwxr-xr-x   1 jayen jayen 2930408473 1990-05-05 05:06 ??h ????.???
-rwxr-xr-x   1 jayen jayen  102621428 1934-10-20 18:43 |???H???.`0c
-r-xr-xr-x   1 jayen jayen 3485510268 1943-12-18 23:49 ???<\?.?h6
-r-xr-xr-x   1 jayen jayen 1086301500 1934-12-02 10:28 ??H?&#480;,?.H
-r-xr-xr-x   1 jayen jayen 1278900565 1953-04-13 23:12 ??:??h??.?cx
-r-xr-xr-x   1 jayen jayen 2794532949 1924-01-04 20:11 h????`)?..?E
-rwxr-xr-x   1 jayen jayen  815333249 1986-01-01 07:55 ??H???K'.b??
-rwxr-xr-x   1 jayen jayen 1279030270 1998-10-31 06:19 ??h???.v??
-rwxr-xr-x   1 jayen jayen 3984818719 2012-09-01 10:33 ??h?(w"?.?>?
-r-xr-xr-x   1 jayen jayen 2333230764 1904-07-27 00:23 h?z?0???.?VM
-r-xr-xr-x   1 jayen jayen 2871297680 2006-02-01 01:05 $???????.??I
-rwxr-xr-x   1 jayen jayen  494534367 1962-12-05 23:06 ?I?? ???
-r-xr-xr-x   1 jayen jayen 1610812476 1911-03-12 00:03 ????????.I??
-rwxr-xr-x   1 jayen jayen 3222528553 2023-04-30 00:29 ? ??i?0?.!??
d?????????   ? ?     ?              ?                ? ????`J??.???
-rwxr-xr-x   1 jayen jayen 1610390525 1941-05-19 14:44 ?j.??|,?.?*A
-r-xr-xr-x   1 jayen jayen 3592879503 1959-12-22 16:35  ?j??!?.o?(
d?????????   ? ?     ?              ?                ? ?~????j?.?p?
-r-xr-xr-x   1 jayen jayen 2438860549 1961-03-20 16:17 (j??????.]s?
-r-xr-xr-x   1 jayen jayen  121532508 1959-12-02 21:39 ??j?S?T?.??0
d?????????   ? ?     ?              ?                ? ??j??-??.??y
d?????????   ? ?     ?              ?                ? ?K??`??!.???
-r-xr-xr-x   1 jayen jayen 2348982127 1939-12-16 21:51 ????????.K??
-rwxr-xr-x   1 jayen jayen 1029341107 1953-04-30 18:12 ??`?K?K?.bv?
d?????????   ? ?     ?              ?                ? kx?/|<;K.?0?
d?????????   ? ?     ?              ?                ? ??kx?N{?.???
d?????????   ? ?     ?              ?                ? |l??????.???
-rwxr-xr-x   1 jayen jayen  170401414 1985-01-24 16:03 l??????.?+?
d?????????   ? ?     ?              ?                ? l/u??_?j.?m?
d?????????   ? ?     ?              ?                ? ???m????.?a0
d?????????   ? ?     ?              ?                ? m???d???.??&
-r-xr-xr-x   1 jayen jayen  948040091 1998-04-03 01:01 {m?:'???.?E?
d?????????   ? ?     ?              ?                ? m?f4r??s.?$]
d?????????   ? ?     ?              ?                ? ??m???F?.??d
-rwxr-xr-x   1 jayen jayen 1228499799 1902-06-30 00:08 m?h8?88?.??3
drwxr-xr-x   5 jayen jayen      32768 2010-02-24 19:17 Movies
-rwxr-xr-x   1 jayen jayen      54784 2002-01-05 02:38 msvci70.dll
d?????????   ? ?     ?              ?                ? ????mut?.???
-rwxr-xr-x   1 jayen jayen 2364751844 2012-12-28 18:10 ??@?mx?w.h?$
d?????????   ? ?     ?              ?                ? )?N?????.???
-rwxr-xr-x   1 jayen jayen 3223677168 2022-01-21 03:07 ??N???'?.?c9
d?????????   ? ?     ?              ?                ? ????n?#?."?s
d?????????   ? ?     ?              ?                ? ???????o.???
-rwxr-xr-x   1 jayen jayen   84891203 1971-06-26 19:33 ???o????
-r-xr-xr-x   1 jayen jayen 1437302295 1990-08-10 11:52 o???>???.?"?
d?????????   ? ?     ?              ?                ? ??on2o?x.???
-r-xr-xr-x   1 jayen jayen  697334003 1980-10-08 02:19 ??oo????.???
d?????????   ? ?     ?              ?                ? ???OU???.}o?
d?????????   ? ?     ?              ?                ? ?p??<!??.???
d?????????   ? ?     ?              ?                ? ?>???.\?.p??
-rwxr-xr-x   1 jayen jayen 3289550241 1962-12-05 13:59 ?????(p?.???
-r-xr-xr-x   1 jayen jayen  353029478 2021-07-07 05:29 ??????_?.?p?
-rwxr-xr-x   1 jayen jayen 2199720176 1981-09-01 03:00 ?p(????:.#??
-r-xr-xr-x   1 jayen jayen 1341363721 2005-07-01 18:46 ????p?|%.{??
d?????????   ? ?     ?              ?                ? ??P?????.???
d?????????   ? ?     ?              ?                ? ???P????.???
-rwxr-xr-x   1 jayen jayen  550631939 1971-02-22 18:34 ????P???.???
d?????????   ? ?     ?              ?                ? ??P?????.1x4
d?????????   ? ?     ?              ?                ? ;p5??b}?.-i?
d?????????   ? ?     ?              ?                ? ???'?p??.?7?
d?????????   ? ?     ?              ?                ? ?P??>??a.???
-?????????   ? ?     ?              ?                ? ???p?h/?.? ?
d?????????   ? ?     ?              ?                ? P?????L?.???
-r-xr-xr-x   1 jayen jayen 2167914520 1937-12-20 14:36 P??;??pP.???
d?????????   ? ?     ?              ?                ? ????????.??q
-rwxr-xr-x   1 jayen jayen 2017164159 1912-12-09 00:25 *&#624;!?Q$!.?:?
d?????????   ? ?     ?              ?                ? ????Q???.??a
d?????????   ? ?     ?              ?                ? ???<??%q.ahy
d?????????   ? ?     ?              ?                ? ?@???q?.b??
-rwxr-xr-x   1 jayen jayen 3750439527 2025-01-22 05:37 qb?k.???
d?????????   ? ?     ?              ?                ? ???%qR??.?v?
d?????????   ? ?     ?              ?                ? ?q'?????.s!?
d?????????   ? ?     ?              ?                ? ?qv??}$1.???
-r-xr-xr-x   1 jayen jayen 2793927922 1936-11-26 23:11 ????q?y?.???
d?????????   ? ?     ?              ?                ? ?????Q??.Y?=
d?????????   ? ?     ?              ?                ? ??r?????.???
-r-xr-xr-x   1 jayen jayen 2865006425 1954-12-05 14:13 ????r???.???
-rwxr-xr-x   1 jayen jayen  557613185 1983-01-13 11:01 ???????r.???
d?????????   ? ?     ?              ?                ? ?_????r?.???
-r-xr-xr-x   1 jayen jayen 1063952379 2002-01-30 19:15 ?R????=?.???
-r-xr-xr-x   1 jayen jayen 3573528486 1926-11-25 22:46 ?`????R?.???
d?????????   ? ?     ?              ?                ? ???r8???.???
drwxr-xr-x   2 jayen jayen      32768 2010-02-24 17:45 Recycled
d?????????   ? ?     ?              ?                ? ????r,?i.-??
d?????????   ? ?     ?              ?                ? ??r?+<??.'j8
-r-xr-xr-x   1 jayen jayen  551633155 1913-08-25 16:57 ????R?$?.&#490;1
-rwxr-xr-x   1 jayen jayen 1932236224 1924-12-12 21:31 ????%???.r?t
-r-xr-xr-x   1 jayen jayen 4279075544 1968-01-26 12:35 ?R"??ug?.??+
-rwxr-xr-x   1 jayen jayen  528325982 1922-12-09 04:58 ?r??????.??v
-rwxr-xr-x   1 jayen jayen 1630433364 2008-08-11 03:00 ????????.?s?
-r-xr-xr-x   1 jayen jayen   19423344 2027-11-22 23:40 s???%???.?%?
d?????????   ? ?     ?              ?                ? ?s$??1??.?O?
-r-xr-xr-x   1 jayen jayen 3243289009 2031-08-27 14:10 sa?????h.K??
-rwxr-xr-x   1 jayen jayen 3137305365 1964-12-02 12:42 s???g??q.?!]
drwxr-xr-x   2 jayen jayen      32768 2010-02-24 19:18 Shows
d?????????   ? ?     ?              ?                ? ???S???i.?j?
-r-xr-xr-x   1 jayen jayen 1081086210 1936-06-06 15:26 ?!??s???.?q?
-rwxr-xr-x   1 jayen jayen   22328404 2012-02-24 05:14 ??s?????.U??
d?????????   ? ?     ?              ?                ? ??s?/w`r.Z??
drwxr-xr-x   7 jayen jayen      32768 2010-02-24 17:45 System Volume Information
d?????????   ? ?     ?              ?                ? ???? ?t?.^%?
d?????????   ? ?     ?              ?                ? ????{???.?t#
-r-xr-xr-x   1 jayen jayen  121053408 1937-11-25 16:41 t$?2????.?^\
-?????????   ? ?     ?              ?                ? t??7qkj=.*/G
-rwxr-xr-x   1 jayen jayen 1402669637 1939-10-15 23:39 T?b????B.?z?
-r-xr-xr-x   1 jayen jayen 2062469733 1982-09-29 15:32 ?t???@cu.??v
d?????????   ? ?     ?              ?                ? ?}T?|F?;.'?.
-rwxr-xr-x   1 jayen jayen 2147681876 2027-03-24 12:51 .T?????*.?F?
d?????????   ? ?     ?              ?                ? t?????g?.i?]
-rwxr-xr-x   1 jayen jayen      18432 2010-04-18 17:37 Thumbs.db
-rwxr-xr-x   1 jayen jayen 4179621984 1943-12-18 08:18 t??|????.Xm?
-r-xr-xr-x   1 jayen jayen 3668304150 1956-11-15 05:32 ?t ??x?q.??s
-r-xr-xr-x   1 jayen jayen 3125040457 2004-07-24 16:06 ?u??$??0.??^
d?????????   ? ?     ?              ?                ? ??u1d???.???
-r-xr-xr-x   1 jayen jayen 1936685029 2034-09-06 13:27 u??g:N+?.+??
-rwxr-xr-x   1 jayen jayen  664702391 1997-12-20 06:16 uh^:r?-?.???
-rwxr-xr-x   1 jayen jayen 4041308092 1913-02-23 18:20 ????uj@?.???
-?????????   ? ?     ?              ?                ? ?????/?U.?k?
d?????????   ? ?     ?              ?                ? ?_u????n.???
-r-xr-xr-x   1 jayen jayen 2561849105 1964-12-17 20:50 !$??Uo??.0?
drwxr-xr-x   6 jayen jayen      32768 2010-04-24 12:03 USB Backup
-rwxr-xr-x   1 jayen jayen 1210118626 2006-07-31 16:00 ?~+us??h.?t-
-rwxr-xr-x   1 jayen jayen 1017190512 2029-03-12 21:48 ?u???{??.v?g
-rwxr-xr-x   1 jayen jayen 2443957346 1970-12-24 12:48 u???;??y.?x?
d?????????   ? ?     ?              ?                ? ?v6].???
d?????????   ? ?     ?              ?                ? ??[??v??.c??
d?????????   ? ?     ?              ?                ? V>??Df??.??<
d?????????   ? ?     ?              ?                ? ?vl/d??y.???
-r-xr-xr-x   1 jayen jayen 1370002502 1943-01-10 02:14 ?Vqv??R?.?dh
-rwxr-xr-x   1 jayen jayen  506374935 1994-08-02 23:25 ??v???t?.???
d?????????   ? ?     ?              ?                ? ?;?V???Y.?9?
-r-xr-xr-x   1 jayen jayen 1511081398 1962-06-07 02:32 ??w+~???.???
-r-xr-xr-x   1 jayen jayen 2098726081 1950-04-08 16:39 ????w???.???
-?????????   ? ?     ?              ?                ? ?/?W????.? ?
-rwxr-xr-x   1 jayen jayen 3625201712 1956-12-06 04:30 w@c?????.?-?
-rwxr-xr-x   1 jayen jayen 1995596765 1954-11-08 18:46 ??w?*??C.???
d?????????   ? ?     ?              ?                ? `??x? ??.???
-rwxr-xr-x   1 jayen jayen 1315708931 1983-10-08 16:13 <<?????.x??
d?????????   ? ?     ?              ?                ? ???????x.\??
-rwxr-xr-x   1 jayen jayen 1266797327 2035-07-01 16:11 ???????x.???
d?????????   ? ?     ?              ?                ? ????????.x??
-r-xr-xr-x   1 jayen jayen 1023733587 1948-04-26 16:57 ??X????<.???
-rwxr-xr-x   1 jayen jayen 3017355066 1969-12-28 01:27 ?x0??h0(.???
-rwxr-xr-x   1 jayen jayen 2071969923 1963-12-27 03:03 ??x????.9
-rwxr-xr-x   1 jayen jayen 1073931715 1907-01-20 03:05 &\????xb.???
-rwxr-xr-x   1 jayen jayen  523513862 1948-07-27 18:14 ????x??C.?+?
-r-xr-xr-x   1 jayen jayen 3103283394 2000-07-17 00:24 ??{?!xd?.<??
-?????????   ? ?     ?              ?                ? ??x?HJ??._/.
d?????????   ? ?     ?              ?                ? x??i?s??./??
-r-xr-xr-x   1 jayen jayen 3174930551 1918-10-11 23:41 xJ?B.?z?
d?????????   ? ?     ?              ?                ? ?x??N?l?.?m?
d?????????   ? ?     ?              ?                ? x>???O?m.??M
-rwxr-xr-x   1 jayen jayen   90591437 1983-09-10 12:01 ??`???>?.xs?
-rwxr-xr-x   1 jayen jayen  947945735 2020-06-14 07:54 ?x??u??f.???
-rwxr-xr-x   1 jayen jayen 2672995676 2003-01-14 06:36 ????????.?y_
-rwxr-xr-x   1 jayen jayen 3962534331 1934-10-25 14:51 ??????y?.1??
d?????????   ? ?     ?              ?                ? ??y,3?c?.?y?
d?????????   ? ?     ?              ?                ? ??Ye????.???
d?????????   ? ?     ?              ?                ? ???????Y.?M?
d?????????   ? ?     ?              ?                ? y???n???._q?
-r-xr-xr-x   1 jayen jayen 1953499425 1980-12-04 02:51 ?_~^Y}?p.???
d?????????   ? ?     ?              ?                ? y?????|?.??q
-rwxr-xr-x   1 jayen jayen  490703180 2017-01-17 06:31 ???z?:??.???
-r-xr-xr-x   1 jayen jayen 1466274671 2032-07-21 11:52 ??z???2e.???
-rwxr-xr-x   1 jayen jayen 2212376146 1998-09-18 00:32 ??zg?i??.:??
d?????????   ? ?     ?              ?                ? ?z??Ycd?
-r-xr-xr-x   1 jayen jayen 1372675932 2015-05-09 21:36 ??z??z;9.?
jayen@jayen-desktop:/media/500GB$ 

```Not sure if this will help or not but in 'Computer' it shows two of the drive for some reason.

[http://www.flickr.com/photos/jayjay402/4666079179/sizes/o/](http://www.flickr.com/photos/jayjay402/4666079179/sizes/o/)

The left one I can go into and simply see or copy my files. Clicking on the right one gives me this:

[http://www.flickr.com/photos/jayjay402/4666079363/sizes/o/](http://www.flickr.com/photos/jayjay402/4666079363/sizes/o/)

I don't really get what this means but you might. :)

---

### Post by formaldehyde_spoon on 2010-06-03
> **Jayjay402 said:**
> Ok, I did the Sudo umount, chown and chmod and rebooted, no changes though.

I'm not sure what is supposed to happen but this is what I got:

I assume that's how it was supposed to work?

It appears I do have a space after uid=1000 in the earlier thread post but not in the real fstab, I just checked. It must have been some weird accidental typo or something.

I did those other commands at the end and got this:

```
jayen@jayen-desktop:~$ cd /media
jayen@jayen-desktop:/media$ ls -la
total 72
drwxr-xr-x  11 root  root   4096 2010-06-02 11:23 .
drwxr-xr-x  22 root  root   4096 2010-05-30 13:07 ..
drwxr-xr-x 121 jayen jayen 32768 1970-01-01 01:00 500GB
drwxr-xr-x   6 jayen jayen  4096 2010-06-01 13:50 80GB
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 AMIT
drwxr-xr-x   2 root  root   4096 2010-05-30 13:08 cdrom0
drwxr-xr-x   2 root  root   4096 2010-05-30 13:08 floppy0
-rw-r--r--   1 root  root      0 2010-06-02 10:37 .hal-mtab
-rw-------   1 root  root      0 2010-06-02 10:45 .hal-mtab-lock
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 JAYEN8GB
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 KINGSTON4GB
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 RESHETA_ZZZ
drwxr-xr-x   2 root  root   4096 2010-06-01 12:04 sdd1
jayen@jayen-desktop:/media$ cd 500GB
jayen@jayen-desktop:/media/500GB$ ls -la 
ls: cannot access &#65533;?&#65533;OU&#65533;?.}o?: Input/output error
ls: cannot access &#65533;&#65533;s&#65533;/w`r.Z&#65533;?: No such file or directory
&#65533;.a&#65533;?: Input/output error&#65533;?
ls: cannot access 0?z?n|.?&#65533;?: Input/output error
ls: cannot access .&#65533;: Input/output error
ls: cannot access &#480;,?&#65533;?.??: Input/output error
ls: cannot access &#65533;(d:??|.
a5: Input/output error
ls: cannot access 
                   &#65533;/U.k&#65533;: No such file or directory
ls: cannot access _`?&#65533;?..C&#65533;: Input/output error
ls: cannot access ?@&#65533;&#65533;q&#65533;.b&#65533;?: Input/output error
ls: cannot access ?    P&#65533;&#65533;&#65533;.1x4: Input/output error
{&#65533;w&#65533;?.7?: Input/output error
ls: cannot access t
&#65533;g.i]: Input/output error
ls: cannot access &#65533;&#65533;??{??.&#65533;t#: Input/output error
ls: cannot access `

x&#65533; &#65533;?.&#65533;: Input/output error
ls: cannot access ?9?b?A.?(?: Input/output error
ls: cannot access &#65533;q'&#65533;?&#65533;?.s!: Input/output error
ls: cannot access &#65533;s$&#65533;1&#65533;?.&#65533;O: Input/output error
ls: cannot access y?n._q&#65533;: Input/output error
ls: cannot access =?CpI/L.z?
                             : No such file or directory
ls: cannot access ?bq&#65533;?&#65533;`.`K?: Input/output error
ls: cannot access _
                     r&#65533;.??: Input/output error
ls: cannot access x>&#65533;m.??M: Input/output error
ls: cannot access ????\&#65533;..: Input/output error
ls: cannot access )?N?&#65533;?.?: Input/output error
ls: cannot access kx?/|<;K.?0&#65533;: No such file or directory
ls: cannot access &#65533;&#65533;?&#65533;???o.&#65533;&#65533;?: Input/output error
ls: cannot access &#65533;z?&#65533;Ycd&#65533;: Input/output error
ls: cannot access ?
                   &#65533;?&#65533;&#65533;&#65533;Y.?M
: Input/output error
ls: cannot access c^gC9&#65533;.s&#65533;&#65533;: Input/output error
ls: cannot access ??f??&#65533;&#65533;.?P?: Input/output error
ls: cannot access &#65533;m?&#65533;F
                        .&#65533;?d: Input/output error
ls: cannot access ??Ye??&#65533;&#65533;.???: Input/output error
?.???: Input/output error
ls: cannot access ??&#65533;&#65533;r,&#65533;i.-&#65533;?: Input/output error
ls: cannot access ?&#65533;<&#65533;&#65533;%q.ahy: Input/output error
ls: cannot access ??&#65533;&#65533;?Q?.Y&#65533;=: Input/output error
ls: cannot access &#65533;???Q?&#65533;?.&#65533;a: Input/output error
ls: cannot access 
                  ~&#65533;?j?.&#65533;p&#65533;: Input/output error
ls: cannot access &?ay&#65533;?: Input/output error
ls: cannot access P???L.?&#65533;&#65533;: Input/output error
ls: cannot access &#65533;?u1??.???: Input/output error
&#65533;&#65533;: Input/output error0<%4.
ls: cannot access ??P?
                      ???.&#65533;: Input/output error
ls: cannot access 8|
bA?&#65533;.&#65533;0&#65533;: Input/output error
ls: cannot access@5??!.*??: Input/output error
ls: cannot access ??[??v?.c??: Input/output error
ls: cannot access mf4r??s.&#65533;$]: Input/output error
: Input/output error&#65533;`J.
ls: cannot access ??r8?.?&#65533;: Input/output error
ls: cannot access ?P??>?&#65533;a.??: Input/output error
ls: cannot access t&#65533;&#65533;7qkj=.*/G: No such file or directory
ls: cannot access ?d?
&#65533;~&#65533;.
&#65533;: Input/output error
ls: cannot access &#65533;&#65533;?&#65533;?.;/: No such file or directory
ls: cannot access 
                  b?`

 .?=&#65533;: Input/output error
ls: cannot access ;p5?b}&#65533;.-i?: Input/output error
ls: cannot access x&#65533;N?l?.&#65533;m&#65533;: Input/output error
ls: cannot access &#65533;
&#65533;?&#65533;`=..&#65533;: Input/output error
ls: cannot access &#65533;;?V
                       &#65533;Y.?9?: Input/output error
ls: cannot access y?&#65533;??|&#65533;.&#65533;?q: Input/output error
ls: cannot access ~\%??.&#65533;&?: Input/output error
ls: cannot access &#65533;?&#65533;?~?f?.&#65533;fG: Input/output error
ls: cannot access .&#65533;?.?&#65533;: Input/output error
ls: cannot access &#65533;qv&#65533;&#65533;}$1.?: Input/output error
ls: cannot access !(?}?&#65533;./: No such file or directory
ls: cannot access ?K
                   `&#65533;?!.&#65533;: Input/output error
ls: cannot access ?~#?dd&#65533;i.?: Input/output error
ls: cannot access &#65533;&#65533;0&#65533;?
                        &#65533;.??a: Input/output error
ls: cannot access ?    ?S???i.?j&#65533;: Input/output error
ls: cannot access ?v6].??&#65533;: Input/output error
ls: cannot access ?&#65533;&#65533;&#65533;&#65533;?.??q: Input/output error
ls: cannot access ??&#65533;?&#65533;?: Input/output error
ls: cannot access &#65533;?&#65533;?mut.&#65533;&#65533;?: Input/output error
ls: cannot access &#65533;?&#65533;&#65533;.&#65533;??: Input/output error
ls: cannot access ?vl/d??y.??&#65533;: No such file or directory
ls: cannot access ?\\?.?&#65533;\.&#65533;|_: Input/output error
ls: cannot access ?&#65533;&#65533;?&#65533;x.\?: Input/output error
ls: cannot access 3??&#65533;?.??&#65533;: Input/output error
ls: cannot access ?&#65533;kx?N{&#65533;.???: Input/output error
ls: cannot access     &#65533;&#65533;n.&quot;?s: Input/output error
ls: cannot access ??x&#65533;HJ&#65533;._/.: No such file or directory
ls: cannot access 0b?2?&#65533;?.!&#65533;: Input/output error
ls: cannot access &#65533;_u?&#65533;?n.&#65533;&#65533;: Input/output error
ls: cannot access &#65533; c,Y    &#65533;.&#65533;&#65533;
                            : Input/output error
ls: cannot access &?&#65533;???..&#65533;&#65533;?: Input/output error
ls: cannot access ?p&#65533;<!&#65533;&#65533;.???: Input/output error
ls: cannot access ??y,3?c?.&#65533;y: Input/output error
ls: cannot access ?%qR
.?v?: Input/output error
ls: cannot access m?&#65533;d&#65533;?&#65533;.&#65533;&: Input/output error
ls: cannot access ^2??(-.???: Input/output error
ls: cannot access ?}T&#65533;|F?;.'.: No such file or directory
ls: cannot access l/u&#65533;    _j.&#65533;m&#65533;: No such file or directory
ls: cannot access |l

?&#65533;&#65533;??: Input/output error
ls: cannot access &#65533;>&#65533;.\&#65533;.p?: Input/output error
ls: cannot access ??>&#65533;??G.&#65533;\
                             : Input/output error
ls: cannot access ?
&#65533; &#65533;t.^%&#65533;: Input/output error
ls: cannot access ?p?h/. ?: No such file or directory
ls: cannot access ??&#65533;'&#65533;p&#65533;?.?7?: Input/output error
ls: cannot access ?/??&#65533;&#65533; : No such file or directory
ls: cannot access V>Df??.?&#65533;<: Input/output error
ls: cannot access ?A&#65533;?&#65533;|?&#65533;.Du&#65533;: Input/output error
ls: cannot access &#65533;?&#65533;???2.&#65533;&#65533;?: Input/output error
ls: cannot access ?&#65533;&#65533;m?&#65533;?.a0: Input/output error
ls: cannot access ??&#65533;&#65533;&#65533;d?.&#65533;?I: Input/output error
ls: cannot access &#65533;&#65533;j?&#65533;-.?y: Input/output error
ls: cannot access ?&#65533;???g.@u&#65533;: Input/output error
ls: cannot access 
                  ?D&#65533;jw&#65533;.??_: Input/output error
ls: cannot access &#65533;&#65533;_&#65533;???.???: Input/output error
ls: cannot access e?&#65533;&#65533;&#65533;?.ong: Input/output error
ls: cannot access &#65533;&#65533;r+<&#65533;?.'j8: Input/output error
ls: cannot access &#65533;&#65533;&#65533;&#65533;&#65533;?.?: Input/output error
ls: cannot access &#65533;??P
&#65533;??.??&#65533;: Input/output error
ls: cannot access x??i&#65533;s&#65533;?./?: No such file or directory
ls: cannot access G?2:&#65533;?R.v?: Input/output error
ls: cannot access &#65533;&#65533;??&#65533;/?.f`?: No such file or directory
ls: cannot access ?&#65533;&#65533;.x?: Input/output error
ls: cannot access &#65533;&#65533;on2o
                        x.?: Input/output error
ls: cannot access B?&#65533;<??.&#65533;?&#65533;: Input/output error
ls: cannot access  &#65533;$&#65533;1?&#65533;~.$    C: Input/output error
ls: cannot access `2?x8?4.: Input/output error
total 292880996
-rwxr-xr-x   1 jayen jayen 4030524432 2017-11-24 20:33 >?? ????.???
d?????????   ? ?     ?              ?                ? !(?}????.??/
-rwxr-xr-x   1 jayen jayen   69210305 1944-02-25 08:21 ?`@??`??.??@
d?????????   ? ?     ?              ?                ? ????\???.?.?
-rwxr-xr-x   1 jayen jayen 1109574925 2017-12-20 23:00 ????????.???
-r-xr-xr-x   1 jayen jayen 3226129265 1992-01-06 11:33 ?)??????.???
d?????????   ? ?     ?              ?                ? ?\\?.??\.?|_
-r-xr-xr-x   1 jayen jayen 4225063786 1906-06-08 13:45 ????????.???
-r-xr-xr-x   1 jayen jayen  679526819 1967-12-25 23:35 ?????!??.!??
drwxr-xr-x 121 jayen jayen      32768 1970-01-01 01:00 .
drwxr-xr-x  11 root  root        4096 2010-06-02 11:23 ..
-rwxr-xr-x   1 jayen jayen 2833983776 2007-12-01 18:24 ????????.??`
-rwxr-xr-x   1 jayen jayen  329450851 1943-02-18 19:32 ????????.??)
-r-xr-xr-x   1 jayen jayen 2696970793 2022-12-14 06:59 ???< ??=.?{?
d?????????   ? ?     ?              ?                ? ????????.???
-r-xr-xr-x   1 jayen jayen 3593104305 1966-08-05 17:57 ?.??+
-?????????   ? ?     ?              ?                ? ???????.;?/
-rwxr-xr-x   1 jayen jayen  174125056 1904-03-15 01:31 ??)?>???.???
d?????????   ? ?     ?              ?                ? ???_????.???
d?????????   ? ?     ?              ?                ? ??????`=..??
d?????????   ? ?     ?              ?                ? ?&?????..???
-rwxr-xr-x   1 jayen jayen 4030795852 1983-10-01 07:00 ?.?)?
d?????????   ? ?     ?              ?                ? ?.??????.???
d?????????   ? ?     ?              ?                ? ???.???
-r-xr-xr-x   1 jayen jayen 2942439610 1957-06-25 03:35 ????<??.???
d?????????   ? ?     ?              ?                ? ????????
d?????????   ? ?     ?              ?                ? ????????.???
d?????????   ? ?     ?              ?                ? ?~\>?%??.?&?
-rwxr-xr-x   1 jayen jayen 1817994962 2001-01-16 20:40 ???
-rwxr-xr-x   1 jayen jayen 2074925693 1950-10-21 21:29 *????0??.??5
d?????????   ? ?     ?              ?                ? ??0?????.??a
d?????????   ? ?     ?              ?                ? 0b??2???.!?
-r-xr-xr-x   1 jayen jayen   56907496 1983-02-09 10:00 ?????0D?.H?*
-rwxr-xr-x   1 jayen jayen 1292127250 1916-07-05 20:40 0hC???K@.,??
-rwxr-xr-x   1 jayen jayen    8586800 1986-08-26 16:02 <?!?`??0.?u?
d?????????   ? ?     ?              ?                ? ??0?z?n|.???
-r-xr-xr-x   1 jayen jayen 3690523862 1939-12-05 13:55 ???1??8?.?s?
d?????????   ? ?     ?              ?                ?  ?$?1??~.$?C
-r-xr-xr-x   1 jayen jayen  737161348 1968-05-24 18:10 ??$1?g??.???
-r-xr-xr-x   1 jayen jayen 3596600715 2011-03-15 18:48 1?t?????.z??
-rwxr-xr-x   1 jayen jayen 3245055613 1969-11-26 19:00 =?|?.?1x
-rwxr-xr-x   1 jayen jayen 4199614024 1985-02-02 00:48 (??1?x??.?+
d?????????   ? ?     ?              ?                ? ^2[???(-.???
d?????????   ? ?     ?              ?                ? ???????2.???
d?????????   ? ?     ?              ?                ? `2?x8??4.???
d?????????   ? ?     ?              ?                ? ?3??????.???
-rwxr-xr-x   1 jayen jayen 2043855317 2037-12-09 14:20 3???? ?_.???
-rwxr-xr-x   1 jayen jayen 1113405957 1942-11-28 05:07 ????????.)?4
d?????????   ? ?     ?              ?                ? ??@5???!.*??
-rwxr-xr-x   1 jayen jayen 1017139938 1984-03-13 15:05 5'?&#498;???.?p`
drwxr-xr-x   7 jayen jayen      32768 2010-04-24 10:57 60GB - Documents & Media - Backup
-r-xr-xr-x   1 jayen jayen 2138624075 1998-06-18 05:49 ??~?6?@?.??m
-rwxr-xr-x   1 jayen jayen  536355014 2020-02-28 11:21  @7??0^?..??
-r-xr-xr-x   1 jayen jayen 1019336519 1902-04-14 17:30 ?_??????.8??
-r-xr-xr-x   1 jayen jayen 2740994288 2016-01-16 03:03 ?8)???9?.?4?
d?????????   ? ?     ?              ?                ? 8|?b?A??.?0?
-r-xr-xr-x   1 jayen jayen  619811524 1954-12-23 06:28 .???8??.B?W
-rwxr-xr-x   1 jayen jayen  204015150 2036-07-03 22:00 8!?+.{G?
d?????????   ? ?     ?              ?                ? ?9???b?A.?(?
d?????????   ? ?     ?              ?                ? 9?{?w???.?7?
d?????????   ? ?     ?              ?                ? ????????.a??
d?????????   ? ?     ?              ?                ? &#480;,?????.???
-rwxr-xr-x   1 jayen jayen 2975671760 2001-03-02 07:19 a???????.??0
-r-xr-xr-x   1 jayen jayen 1345201027 2024-01-15 00:01 A?8~?>?V.?^?
drwxr-xr-x  11 jayen jayen      32768 2010-02-25 18:00 AA-Shows
-r-xr-xr-x   1 jayen jayen 1339621262 1934-04-08 23:25 ?A??A??.x??
d?????????   ? ?     ?              ?                ? ?A???|??.Du?
-r-xr-xr-x   1 jayen jayen 2736999861 1920-04-25 21:34 ?am?????.`??
-rwxr-xr-x   1 jayen jayen  793866512 1992-06-02 02:03 ??a ???p.???
-rwxr-xr-x   1 jayen jayen   88014256 2020-01-14 00:23 +??a??~?.??u
-r-xr-xr-x   1 jayen jayen 3341552469 2017-07-21 15:19 ???`av??.?X?
d?????????   ? ?     ?              ?                ? &?a?y???
-rwxr-xr-x   1 jayen jayen 3426822728 1923-07-21 22:08 A?}Z???o.???
d?????????   ? ?     ?              ?                ? ?b??`???.?=?
d?????????   ? ?     ?              ?                ? B????<??.???
d?????????   ? ?     ?              ?                ? ??B?0<%4.???
d?????????   ? ?     ?              ?                ? ?bq????`.`K?
-rwxr-xr-x   1 jayen jayen 2599636932 1962-09-28 00:22 ?b&??.??.-?t
-rwxr-xr-x   1 jayen jayen  806030499 1948-12-07 04:56 ????.C??
-rwxr-xr-x   1 jayen jayen   62813196 1961-02-25 09:04 ?????C??.???
d?????????   ? ?     ?              ?                ? ?_`????..C??
-r-xr-xr-x   1 jayen jayen 3128889807 2015-08-01 08:04 ????C???.?>2
-r-xr-xr-x   1 jayen jayen 3308779198 2009-01-18 03:52 ?????c??.8??
-r-xr-xr-x   1 jayen jayen 1744010782 1939-10-21 23:45 <?ca?a?u.?&%
d?????????   ? ?     ?              ?                ? c?^gC9??.s??
-?????????   ? ?     ?              ?                ? =??CpI/L.z??
-r-xr-xr-x   1 jayen jayen 1572777746 1995-02-01 00:19 ?C??)p?{.j??
d?????????   ? ?     ?              ?                ? ? c,?Y??.???
-r-xr-xr-x   1 jayen jayen 4095698967 1940-03-02 09:34 =d>?????.???
d?????????   ? ?     ?              ?                ? ?d????~?.???
-rwxr-xr-x   1 jayen jayen 3306712746 1963-08-06 20:26 )+?!d??_.??^
d?????????   ? ?     ?              ?                ? ??(d:??|.?a5
d?????????   ? ?     ?              ?                ? ?~#?dd?i.???
d?????????   ? ?     ?              ?                ? ??????d?.??I
d?????????   ? ?     ?              ?                ? ???D?jw?.??_
-rwxr-xr-x   1 jayen jayen 3172412529 1917-12-04 18:03 ??%#?+d%.??p
-rwxr-xr-x   1 jayen jayen 1463749660 1988-03-06 04:23 e???????.???
-r-xr-xr-x   1 jayen jayen 1429845025 1930-07-14 18:52 ??>??E?*.??{
-r-xr-xr-x   1 jayen jayen 4025668096 1940-04-25 22:55 E??????@.???
d?????????   ? ?     ?              ?                ? e???????.ong
-?????????   ? ?     ?              ?                ? ?????/??.f`?
-r-xr-xr-x   1 jayen jayen 4211863723 1980-12-23 03:01 ?????F??.???
d?????????   ? ?     ?              ?                ? ????~?f?.?fG
d?????????   ? ?     ?              ?                ? ???f????.?P?
-r-xr-xr-x   1 jayen jayen 3692023032 1986-01-15 07:04 F??;?^=U.???
-r-xr-xr-x   1 jayen jayen 4232738847 1955-03-02 08:40 f???X<??. ??
d?????????   ? ?     ?              ?                ? ??>????G.?\?
-rwxr-xr-x   1 jayen jayen 2013924320 1984-12-19 03:10 g???00dc.'?
d?????????   ? ?     ?              ?                ? G?2:???R.v??
-rwxr-xr-x   1 jayen jayen 1456428186 1909-12-01 21:41 ?g?d?0?f.???
-r-xr-xr-x   1 jayen jayen 4008270641 1921-03-20 23:55 ???g?g??.???
d?????????   ? ?     ?              ?                ? ???????g.@u?
-rwxr-xr-x   1 jayen jayen 1453279404 2026-10-28 06:53 ???@?.??.??h
-rwxr-xr-x   1 jayen jayen 4013944928 1971-07-20 21:34 ?+??'??h.???
-rwxr-xr-x   1 jayen jayen 2930408473 1990-05-05 05:06 ??h ????.???
-rwxr-xr-x   1 jayen jayen  102621428 1934-10-20 18:43 |???H???.`0c
-r-xr-xr-x   1 jayen jayen 3485510268 1943-12-18 23:49 ???<\?.?h6
-r-xr-xr-x   1 jayen jayen 1086301500 1934-12-02 10:28 ??H?&#480;,?.H
-r-xr-xr-x   1 jayen jayen 1278900565 1953-04-13 23:12 ??:??h??.?cx
-r-xr-xr-x   1 jayen jayen 2794532949 1924-01-04 20:11 h????`)?..?E
-rwxr-xr-x   1 jayen jayen  815333249 1986-01-01 07:55 ??H???K'.b??
-rwxr-xr-x   1 jayen jayen 1279030270 1998-10-31 06:19 ??h???.v??
-rwxr-xr-x   1 jayen jayen 3984818719 2012-09-01 10:33 ??h?(w&quot;?.?>?
-r-xr-xr-x   1 jayen jayen 2333230764 1904-07-27 00:23 h?z?0???.?VM
-r-xr-xr-x   1 jayen jayen 2871297680 2006-02-01 01:05 $???????.??I
-rwxr-xr-x   1 jayen jayen  494534367 1962-12-05 23:06 ?I?? ???
-r-xr-xr-x   1 jayen jayen 1610812476 1911-03-12 00:03 ????????.I??
-rwxr-xr-x   1 jayen jayen 3222528553 2023-04-30 00:29 ? ??i?0?.!??
d?????????   ? ?     ?              ?                ? ????`J??.???
-rwxr-xr-x   1 jayen jayen 1610390525 1941-05-19 14:44 ?j.??|,?.?*A
-r-xr-xr-x   1 jayen jayen 3592879503 1959-12-22 16:35  ?j??!?.o?(
d?????????   ? ?     ?              ?                ? ?~????j?.?p?
-r-xr-xr-x   1 jayen jayen 2438860549 1961-03-20 16:17 (j??????.]s?
-r-xr-xr-x   1 jayen jayen  121532508 1959-12-02 21:39 ??j?S?T?.??0
d?????????   ? ?     ?              ?                ? ??j??-??.??y
d?????????   ? ?     ?              ?                ? ?K??`??!.???
-r-xr-xr-x   1 jayen jayen 2348982127 1939-12-16 21:51 ????????.K??
-rwxr-xr-x   1 jayen jayen 1029341107 1953-04-30 18:12 ??`?K?K?.bv?
d?????????   ? ?     ?              ?                ? kx?/|<;K.?0?
d?????????   ? ?     ?              ?                ? ??kx?N{?.???
d?????????   ? ?     ?              ?                ? |l??????.???
-rwxr-xr-x   1 jayen jayen  170401414 1985-01-24 16:03 l??????.?+?
d?????????   ? ?     ?              ?                ? l/u??_?j.?m?
d?????????   ? ?     ?              ?                ? ???m????.?a0
d?????????   ? ?     ?              ?                ? m???d???.??&
-r-xr-xr-x   1 jayen jayen  948040091 1998-04-03 01:01 {m?:'???.?E?
d?????????   ? ?     ?              ?                ? m?f4r??s.?$]
d?????????   ? ?     ?              ?                ? ??m???F?.??d
-rwxr-xr-x   1 jayen jayen 1228499799 1902-06-30 00:08 m?h8?88?.??3
drwxr-xr-x   5 jayen jayen      32768 2010-02-24 19:17 Movies
-rwxr-xr-x   1 jayen jayen      54784 2002-01-05 02:38 msvci70.dll
d?????????   ? ?     ?              ?                ? ????mut?.???
-rwxr-xr-x   1 jayen jayen 2364751844 2012-12-28 18:10 ??@?mx?w.h?$
d?????????   ? ?     ?              ?                ? )?N?????.???
-rwxr-xr-x   1 jayen jayen 3223677168 2022-01-21 03:07 ??N???'?.?c9
d?????????   ? ?     ?              ?                ? ????n?#?.&quot;?s
d?????????   ? ?     ?              ?                ? ???????o.???
-rwxr-xr-x   1 jayen jayen   84891203 1971-06-26 19:33 ???o????
-r-xr-xr-x   1 jayen jayen 1437302295 1990-08-10 11:52 o???>???.?&quot;?
d?????????   ? ?     ?              ?                ? ??on2o?x.???
-r-xr-xr-x   1 jayen jayen  697334003 1980-10-08 02:19 ??oo????.???
d?????????   ? ?     ?              ?                ? ???OU???.}o?
d?????????   ? ?     ?              ?                ? ?p??<!??.???
d?????????   ? ?     ?              ?                ? ?>???.\?.p??
-rwxr-xr-x   1 jayen jayen 3289550241 1962-12-05 13:59 ?????(p?.???
-r-xr-xr-x   1 jayen jayen  353029478 2021-07-07 05:29 ??????_?.?p?
-rwxr-xr-x   1 jayen jayen 2199720176 1981-09-01 03:00 ?p(????:.#??
-r-xr-xr-x   1 jayen jayen 1341363721 2005-07-01 18:46 ????p?|%.{??
d?????????   ? ?     ?              ?                ? ??P?????.???
d?????????   ? ?     ?              ?                ? ???P????.???
-rwxr-xr-x   1 jayen jayen  550631939 1971-02-22 18:34 ????P???.???
d?????????   ? ?     ?              ?                ? ??P?????.1x4
d?????????   ? ?     ?              ?                ? ;p5??b}?.-i?
d?????????   ? ?     ?              ?                ? ???'?p??.?7?
d?????????   ? ?     ?              ?                ? ?P??>??a.???
-?????????   ? ?     ?              ?                ? ???p?h/?.? ?
d?????????   ? ?     ?              ?                ? P?????L?.???
-r-xr-xr-x   1 jayen jayen 2167914520 1937-12-20 14:36 P??;??pP.???
d?????????   ? ?     ?              ?                ? ????????.??q
-rwxr-xr-x   1 jayen jayen 2017164159 1912-12-09 00:25 *&#624;!?Q$!.?:?
d?????????   ? ?     ?              ?                ? ????Q???.??a
d?????????   ? ?     ?              ?                ? ???<??%q.ahy
d?????????   ? ?     ?              ?                ? ?@???q?.b??
-rwxr-xr-x   1 jayen jayen 3750439527 2025-01-22 05:37 qb?k.???
d?????????   ? ?     ?              ?                ? ???%qR??.?v?
d?????????   ? ?     ?              ?                ? ?q'?????.s!?
d?????????   ? ?     ?              ?                ? ?qv??}$1.???
-r-xr-xr-x   1 jayen jayen 2793927922 1936-11-26 23:11 ????q?y?.???
d?????????   ? ?     ?              ?                ? ?????Q??.Y?=
d?????????   ? ?     ?              ?                ? ??r?????.???
-r-xr-xr-x   1 jayen jayen 2865006425 1954-12-05 14:13 ????r???.???
-rwxr-xr-x   1 jayen jayen  557613185 1983-01-13 11:01 ???????r.???
d?????????   ? ?     ?              ?                ? ?_????r?.???
-r-xr-xr-x   1 jayen jayen 1063952379 2002-01-30 19:15 ?R????=?.???
-r-xr-xr-x   1 jayen jayen 3573528486 1926-11-25 22:46 ?`????R?.???
d?????????   ? ?     ?              ?                ? ???r8???.???
drwxr-xr-x   2 jayen jayen      32768 2010-02-24 17:45 Recycled
d?????????   ? ?     ?              ?                ? ????r,?i.-??
d?????????   ? ?     ?              ?                ? ??r?+<??.'j8
-r-xr-xr-x   1 jayen jayen  551633155 1913-08-25 16:57 ????R?$?.&#490;1
-rwxr-xr-x   1 jayen jayen 1932236224 1924-12-12 21:31 ????%???.r?t
-r-xr-xr-x   1 jayen jayen 4279075544 1968-01-26 12:35 ?R&quot;??ug?.??+
-rwxr-xr-x   1 jayen jayen  528325982 1922-12-09 04:58 ?r??????.??v
-rwxr-xr-x   1 jayen jayen 1630433364 2008-08-11 03:00 ????????.?s?
-r-xr-xr-x   1 jayen jayen   19423344 2027-11-22 23:40 s???%???.?%?
d?????????   ? ?     ?              ?                ? ?s$??1??.?O?
-r-xr-xr-x   1 jayen jayen 3243289009 2031-08-27 14:10 sa?????h.K??
-rwxr-xr-x   1 jayen jayen 3137305365 1964-12-02 12:42 s???g??q.?!]
drwxr-xr-x   2 jayen jayen      32768 2010-02-24 19:18 Shows
d?????????   ? ?     ?              ?                ? ???S???i.?j?
-r-xr-xr-x   1 jayen jayen 1081086210 1936-06-06 15:26 ?!??s???.?q?
-rwxr-xr-x   1 jayen jayen   22328404 2012-02-24 05:14 ??s?????.U??
d?????????   ? ?     ?              ?                ? ??s?/w`r.Z??
drwxr-xr-x   7 jayen jayen      32768 2010-02-24 17:45 System Volume Information
d?????????   ? ?     ?              ?                ? ???? ?t?.^%?
d?????????   ? ?     ?              ?                ? ????{???.?t#
-r-xr-xr-x   1 jayen jayen  121053408 1937-11-25 16:41 t$?2????.?^\
-?????????   ? ?     ?              ?                ? t??7qkj=.*/G
-rwxr-xr-x   1 jayen jayen 1402669637 1939-10-15 23:39 T?b????B.?z?
-r-xr-xr-x   1 jayen jayen 2062469733 1982-09-29 15:32 ?t???@cu.??v
d?????????   ? ?     ?              ?                ? ?}T?|F?;.'?.
-rwxr-xr-x   1 jayen jayen 2147681876 2027-03-24 12:51 .T?????*.?F?
d?????????   ? ?     ?              ?                ? t?????g?.i?]
-rwxr-xr-x   1 jayen jayen      18432 2010-04-18 17:37 Thumbs.db
-rwxr-xr-x   1 jayen jayen 4179621984 1943-12-18 08:18 t??|????.Xm?
-r-xr-xr-x   1 jayen jayen 3668304150 1956-11-15 05:32 ?t ??x?q.??s
-r-xr-xr-x   1 jayen jayen 3125040457 2004-07-24 16:06 ?u??$??0.??^
d?????????   ? ?     ?              ?                ? ??u1d???.???
-r-xr-xr-x   1 jayen jayen 1936685029 2034-09-06 13:27 u??g:N+?.+??
-rwxr-xr-x   1 jayen jayen  664702391 1997-12-20 06:16 uh^:r?-?.???
-rwxr-xr-x   1 jayen jayen 4041308092 1913-02-23 18:20 ????uj@?.???
-?????????   ? ?     ?              ?                ? ?????/?U.?k?
d?????????   ? ?     ?              ?                ? ?_u????n.???
-r-xr-xr-x   1 jayen jayen 2561849105 1964-12-17 20:50 !$??Uo??.0?
drwxr-xr-x   6 jayen jayen      32768 2010-04-24 12:03 USB Backup
-rwxr-xr-x   1 jayen jayen 1210118626 2006-07-31 16:00 ?~+us??h.?t-
-rwxr-xr-x   1 jayen jayen 1017190512 2029-03-12 21:48 ?u???{??.v?g
-rwxr-xr-x   1 jayen jayen 2443957346 1970-12-24 12:48 u???;??y.?x?
d?????????   ? ?     ?              ?                ? ?v6].???
d?????????   ? ?     ?              ?                ? ??[??v??.c??
d?????????   ? ?     ?              ?                ? V>??Df??.??<
d?????????   ? ?     ?              ?                ? ?vl/d??y.???
-r-xr-xr-x   1 jayen jayen 1370002502 1943-01-10 02:14 ?Vqv??R?.?dh
-rwxr-xr-x   1 jayen jayen  506374935 1994-08-02 23:25 ??v???t?.???
d?????????   ? ?     ?              ?                ? ?;?V???Y.?9?
-r-xr-xr-x   1 jayen jayen 1511081398 1962-06-07 02:32 ??w+~???.???
-r-xr-xr-x   1 jayen jayen 2098726081 1950-04-08 16:39 ????w???.???
-?????????   ? ?     ?              ?                ? ?/?W????.? ?
-rwxr-xr-x   1 jayen jayen 3625201712 1956-12-06 04:30 w@c?????.?-?
-rwxr-xr-x   1 jayen jayen 1995596765 1954-11-08 18:46 ??w?*??C.???
d?????????   ? ?     ?              ?                ? `??x? ??.???
-rwxr-xr-x   1 jayen jayen 1315708931 1983-10-08 16:13 <<?????.x??
d?????????   ? ?     ?              ?                ? ???????x.\??
-rwxr-xr-x   1 jayen jayen 1266797327 2035-07-01 16:11 ???????x.???
d?????????   ? ?     ?              ?                ? ????????.x??
-r-xr-xr-x   1 jayen jayen 1023733587 1948-04-26 16:57 ??X????<.???
-rwxr-xr-x   1 jayen jayen 3017355066 1969-12-28 01:27 ?x0??h0(.???
-rwxr-xr-x   1 jayen jayen 2071969923 1963-12-27 03:03 ??x????.9
-rwxr-xr-x   1 jayen jayen 1073931715 1907-01-20 03:05 &\????xb.???
-rwxr-xr-x   1 jayen jayen  523513862 1948-07-27 18:14 ????x??C.?+?
-r-xr-xr-x   1 jayen jayen 3103283394 2000-07-17 00:24 ??{?!xd?.<??
-?????????   ? ?     ?              ?                ? ??x?HJ??._/.
d?????????   ? ?     ?              ?                ? x??i?s??./??
-r-xr-xr-x   1 jayen jayen 3174930551 1918-10-11 23:41 xJ?B.?z?
d?????????   ? ?     ?              ?                ? ?x??N?l?.?m?
d?????????   ? ?     ?              ?                ? x>???O?m.??M
-rwxr-xr-x   1 jayen jayen   90591437 1983-09-10 12:01 ??`???>?.xs?
-rwxr-xr-x   1 jayen jayen  947945735 2020-06-14 07:54 ?x??u??f.???
-rwxr-xr-x   1 jayen jayen 2672995676 2003-01-14 06:36 ????????.?y_
-rwxr-xr-x   1 jayen jayen 3962534331 1934-10-25 14:51 ??????y?.1??
d?????????   ? ?     ?              ?                ? ??y,3?c?.?y?
d?????????   ? ?     ?              ?                ? ??Ye????.???
d?????????   ? ?     ?              ?                ? ???????Y.?M?
d?????????   ? ?     ?              ?                ? y???n???._q?
-r-xr-xr-x   1 jayen jayen 1953499425 1980-12-04 02:51 ?_~^Y}?p.???
d?????????   ? ?     ?              ?                ? y?????|?.??q
-rwxr-xr-x   1 jayen jayen  490703180 2017-01-17 06:31 ???z?:??.???
-r-xr-xr-x   1 jayen jayen 1466274671 2032-07-21 11:52 ??z???2e.???
-rwxr-xr-x   1 jayen jayen 2212376146 1998-09-18 00:32 ??zg?i??.:??
d?????????   ? ?     ?              ?                ? ?z??Ycd?
-r-xr-xr-x   1 jayen jayen 1372675932 2015-05-09 21:36 ??z??z;9.?
jayen@jayen-desktop:/media/500GB$ 

```Not sure if this will help or not but in 'Computer' it shows two of the drive for some reason.

[http://www.flickr.com/photos/jayjay402/4666079179/sizes/o/](http://www.flickr.com/photos/jayjay402/4666079179/sizes/o/)

The left one I can go into and simply see or copy my files. Clicking on the right one gives me this:

[http://www.flickr.com/photos/jayjay402/4666079363/sizes/o/](http://www.flickr.com/photos/jayjay402/4666079363/sizes/o/)

I don't really get what this means but you might. :)

Weird.  Are you certain that the disk is actually formatted as FAT32?

*goes back and checks whole thread* 

At the start of the thread you listed it as ntfs, but fdisk is reporting W95 FAT32.  If it's actually ntfs that could explain the strangeness above.

Try changing the fstab line to 
UUID=10D8-132E /media/500GB **ntfs-3g** user,exec,suid,auto,relatime,dev,async,rw,uid=1000,umask=022,gid=1000 0 0   

and rebooting.  Then try the cd, ls commands from last post to see if you still get garbage for the second cd.

Hopefully that will fix it, but if not, see below.

 If that doesn't help, my best guess is that the file system on the disk is damaged. I would recreate the partition with gparted ('sudo apt-get install gparted' , System > Admin > Gparted).  Choose any filesystem type you like when you do this, FAT32 or NTFS is probably a good idea if you also use the disk with Windows, just make sure you have the correctly matching type in fstab.  If you only use it for Linux you could choose ext3 (or ext4).
This is kind of like a more severe format of the disk.  It also means you will lose, or have to backup first, the data on the disk.

After recreating the partition in gparted, and making sure fstab has the correct type listed, reboot. 

If this doesn't help then I'm stumped, I'm sorry. Try posting a new thread.  Include the data from fstab, sudo fdisk -l, mount, cd /media, ls -la, cd 500GB, ls -la, in the post, and hope that someone else can help. 

EDIT: you might have to do the 'umount' command from last post before gparted will let you do anything to the disk (I can't remember, just try).
Tell me what happens, btw, I'm not saying I won't keep posting here ;)

---

### Post by Jayjay402 on 2010-06-04
I am 100% sure it's fat32, it's the ONLY format PS3 and many other media players will read, and it's mainly what I use it for and it works with my PS3.
I did a quick google search and PS3 definitely doesn't read ntfs. (Gparted also reports the hdd as fat32)

However I will try what you've said anyway. It could be that the file system is damaged, lucky I only actually have around 70GB of data on it, it's a lot easier than backing up than if it were almost full.:)

Anyways, I try all of that stuff, and then post back here soon.
Thanx for the all the help and advice you've given!:)

---

### Post by ScottinSoCal on 2010-06-04
I realize this has been an ongoing saga for a few days, but did you know that if you change the mount point to somewhere in your /home/[username] directory, you don't have to mess with all these permissions issues? You'll own it by default, with full access. The only downside, if it is one, is that no other user accounts on the computer will be able to use it. I'm the only one who logs in to my laptop, so it isn't a problem for me, and mine works great.

---

### Post by formaldehyde_spoon on 2010-06-04
> **ScottinSoCal said:**
> I realize this has been an ongoing saga for a few days, but did you know that if you change the mount point to somewhere in your /home/[username] directory, you don't have to mess with all these permissions issues? You'll own it by default, with full access. The only downside, if it is one, is that no other user accounts on the computer will be able to use it. I'm the only one who logs in to my laptop, so it isn't a problem for me, and mine works great.

He's already changed the ownership and permissions of the mount point, so that wouldn't make any difference now.

Anyway, if you look at the output he printed two posts ago, it's apparent that permissions aren't his real problem, something else is wrong...

---

### Post by Jayjay402 on 2010-06-07
Well thanx for the help guys. It looks like it's going to be a while before I have the time to back up the hdd first, before I re-format it and this thread will probably be dated by then. I'll let you know how it goes via pm, formaldehyde_spoon.:)

---

### Post by formaldehyde_spoon on 2010-06-07
Ok, do that.

---

