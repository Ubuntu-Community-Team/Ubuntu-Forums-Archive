---
title: "Converting dual boot W7/Ubuntu to single boot  Ubuntu"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by jpt85 on 2010-04-15
I just bought a new Gateway netbook computer (LT2119u) with 32bit Windows 7 Starter pre-installed on the hard drive.  I have a 250GB HDD and 2 GB of RAM.  I have nothing at all on the Hard Drive (no personal files).  I downloaded the Netbook Remix of 9.10 (Karmic Koala) as an ISO image and burned that to CD.  I then ran the ISO image from an external USB optical drive connected to my new Gateway netbook.  It successfully installed Ubuntu 9.10 on my hard drive, alongside the pre-installed Windows 7 Starter OS. Everything works on Ubuntu, including Grub 2, my wi-fi card, all the USB ports, etc.  

Now that I know it works I wish to make Ubuntu 9.10 my default and ONLY operating system and wish to permanently delete the Windows 7 files from my hard drive.  How do I do this?  

When I look at the properties of the computer under 9.10, it lists most of the hard drive as "system reserved".  I assume that this is the protected portion which holds all of the Windows files.  

I have some experience with the Ubuntu 8.XXX series (about 6 months) on a previous computer, but my mastery of the Terminal and CLI is extremely limited.  

A few questions:

1) On the previous Ubuntu 8.XXX series that I installed, it asked whether I wanted to do a Dual Boot installation or permanently overwrite and make Ubuntu the default OS.  I don't remember this latest Ubuntu 9.10 doing that?  Did I miss something?  The only way it would install was via a dual-boot set up.

2) I saw in other parts of this site, that it mentioned that Ubuntu 9.04 must be installed prior to installing 9.10.  I assumed that was for the desktop version only.  Should I have done that here with my netbook remix version?  I installed 9.10 directly first.  Did I mess up?

3) Everything seems to be working just fine with 9.10.  I now wish to completely rid Windows 7 and all of it's associated files from my Hard Drive.  Would it be easier to uninstall 9.10 and start fresh, rather than trying to move partitions around?  If so, how would I do that?

Thank you very much to whoever helps for this newbie.  Ubuntu must have done something right, because this new computer will be my 2nd with Ubuntu on it!

---

### Post by ttshivers on 2010-04-15
Wait. Are you running Ubuntu 9.10 Netbook remix or just plain Ubuntu 9.10

---

### Post by jpt85 on 2010-04-15
> **ttshivers said:**
> Wait. Are you running Ubuntu 9.10 Netbook remix or just plain Ubuntu 9.10

I'm running Ubuntu 9.10 Netbook remix.

---

### Post by ttshivers on 2010-04-15
Right now, I am downloading the Ubuntu Netbook Remix CD so I can help you.  What you need to so is just to resize your Ubuntu partition so it takes up the entire drive and wipes out Windows.  I will include instructions about how to do that in my next post.

---

### Post by jpt85 on 2010-04-15
> **ttshivers said:**
> Right now, I am downloading the Ubuntu Netbook Remix CD so I can help you.  What you need to so is just to resize your Ubuntu partition so it takes up the entire drive and wipes out Windows.  I will include instructions about how to do that in my next post.

Awesome, thanks, I'm waiting with baited breath! :P

---

### Post by ttshivers on 2010-04-15
Sorry.  The computer that I used the live CD on didn't work with my mouse, so I had to use another computer.  I found out how to do it though.  Remember to BACK UP YOU HARD DRIVE before you do this because it could mess up, although that is very unlikely.  I recommend using [clonezilla]("http://www.clonezilla.org/") because it makes an image of your entire hard drive so you can restore it to exactly how it was before you did this.  If you need help using clonezilla, please contact me.  Please take backup seriously.  I also included screen shots that go along with the step numbers so you can visualize it easier.  I have not included screen shots for every step because some of the steps really don't need any more explaining.

Here are the instructions:


[LIST=1]
[*]Open the menu
[*]Click on the system tab
[*]Click on GParted
[*]Right click on your windows partition (it won't always be called Windows)
[*]Select Delete
[*]Right click on the biggest partition left (besides unallocated space)
[*]Click Resize/Move
[*]Drag the white space until you cant drag it any more
[*]Click the button "resize/move"
[*]Click on the check mark on the tool-bar
[*]Click apply
[*]It should now start resizing your drive
[*]YOU FINISHED!!!
[/LIST]
Since I can't include all the screenshots in this post, I will include some more in another post.  If this doesn't work, try doing it on the live disk of Ubuntu.

---

### Post by ttshivers on 2010-04-15
More screenshots.

---

### Post by jpt85 on 2010-04-15
Thanks for all of that Travis.  It looks pretty straightforward and easy to do.  Two quick questions before I commit and take the plunge:

1) On the screen shot I provided, which files do I keep and which do I resize.  I'm not sure which are Linux, which are Windows and which I don't want to mess with.  

2) After I do this and assuming everything is kosher, will this make a nice clean install, or will there be any fragments or any inefficient Ubuntu installation.  In other words, will this be a nice, "clean" install?

Thanks again! 

[http://i931.photobucket.com/albums/ad153/JPT85_photo/Screenshot.png](http://i931.photobucket.com/albums/ad153/JPT85_photo/Screenshot.png)

---

### Post by ttshivers on 2010-04-15
Lets check.  Open computer, and right click on File System.  Send me a screenshot of what that looks like.  I need this to see what partition Linux is on.

Also, if everything goes well, then yes, this will make a "clean install"

---

### Post by perham on 2010-04-15
> **jpt85 said:**
> Thanks for all of that Travis.  It looks pretty straightforward and easy to do.  Two quick questions before I commit and take the plunge:

1) On the screen shot I provided, which files do I keep and which do I resize.  I'm not sure which are Linux, which are Windows and which I don't want to mess with.  

2) After I do this and assuming everything is kosher, will this make a nice clean install, or will there be any fragments or any inefficient Ubuntu installation.  In other words, will this be a nice, "clean" install?

Thanks again! 

[http://i931.photobucket.com/albums/ad153/JPT85_photo/Screenshot.png](http://i931.photobucket.com/albums/ad153/JPT85_photo/Screenshot.png)

you don't have linux partitions. have you installed ubuntu on your disk, or you're running from livecd?

---

### Post by jpt85 on 2010-04-15
> **ttshivers said:**
> Lets check.  Open computer, and right click on File System.  Send me a screenshot of what that looks like.  I need this to see what partition Linux is on.

Also, if everything goes well, then yes, this will make a "clean install"

Is this what you are looking for or a different screen capture?

[http://i931.photobucket.com/albums/ad153/JPT85_photo/Screenshot-1.png](http://i931.photobucket.com/albums/ad153/JPT85_photo/Screenshot-1.png)

---

### Post by ttshivers on 2010-04-15
It doesn't look like he is running a live CD from the screenshot because he has his own username.  Mabey he has it is on a different drive.

---

### Post by jpt85 on 2010-04-15
> **perham said:**
> you don't have linux partitions. have you installed ubuntu on your disk, or you're running from livecd?

I have installed Linux on my hard drive.  I am not using a livecd.

---

### Post by ttshivers on 2010-04-15
To see if linux is on a different drive, where it says /dev/sda on the top right corner, click on that and it should show another drive.  Click on the different drives and send me screen-shots of those so I can see if Linux is on any of those drives.

Do you know if you have more than one hard drive in your computer?

---

### Post by perham on 2010-04-15
> **jpt85 said:**
> I have installed Linux on my hard drive.  I am not using a livecd.

post the outputs of these commands:

```

mount
sudo fdisk -l
cat /etc/fstab


```

---

### Post by jpt85 on 2010-04-15
> **ttshivers said:**
> To see if linux is on a different drive, where it says /dev/sda on the top right corner, click on that and it should show another drive.  Click on the different drives and send me screen-shots of those so I can see if Linux is on any of those drives.

Do you know if you have more than one hard drive in your computer?

I'm assuming you mean where it shows "/dev/sda", you mean on Gparted, right?

If so, I clicked on it and it does nothing but change to a brown color, so no other drives.  FWIW, my computer only has the one 250 GB hard drive.  Everything is partitiioned on that one drive.  The one "cdrom0" from the computer file browser screen shot was from the external USB optical drive that I used to put Ubuntu on my hard drive.  It is currently not connected.   So, only one hard drive - nothing else on my netbook.

---

### Post by jpt85 on 2010-04-15
> **perham said:**
> post the outputs of these commands:

```

mount
sudo fdisk -l
cat /etc/fstab


```

jamie@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda3 on /host type fuseblk (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jamie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jamie)
jamie@ubuntu:~$ sudo fdisk -1
[sudo] password for jamie: 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
jamie@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jamie@ubuntu:~$

---

### Post by ttshivers on 2010-04-15
Ah.  You may have linux installed inside of windows.

How did you install linux?  Did you have Windows running when you installed it? Did you boot from the liveCD when you installed it?

---

### Post by perham on 2010-04-15
> **jpt85 said:**
> jamie@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda3 on /host type fuseblk (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jamie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jamie)
jamie@ubuntu:~$ sudo fdisk -1
[sudo] password for jamie: 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
jamie@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jamie@ubuntu:~$

that's sudo fdisk -l (lowercase L), not -1 

your ubuntu is installed on a loop device (on two files in your ntfs disk). I guess you used wubi to install ubuntu. you need to make a partition and the copy the contents to that partition bit by bit. it can be done, but it's a little hard to do if you're not so familiar with command line. instead, if you haven't configured your ubuntu installation that much, and if you can do a clean install, I suggest that you boot from the livecd, wipe your hdd, and then do a clean install on your hdd, and this time, be sure to make 2 primary partitions (one for root and one for swap) and install ubuntu on them.

---

### Post by ttshivers on 2010-04-15
Yes, with your situation, it would be easier to just do a clean install.  Before you reinsall it, run the live CD and use GParted to delete all the partitions on the hard drive so Ubuntu will take up the entire hard drive.

> **perham said:**
> that's sudo fdisk -l (lowercase L), not -1 

your ubuntu is installed on a loop device (on two files in your ntfs disk). I guess you used wubi to install ubuntu. you need to make a partition and the copy the contents to that partition bit by bit. it can be done, but it's a little hard to do if you're not so familiar with command line. instead, if you haven't configured your ubuntu installation that much, and if you can do a clean install, I suggest that you boot from the livecd, wipe your hdd, and then do a clean install on your hdd, and this time, be sure to make 2 primary partitions (one for root and one for swap) and install ubuntu on them.

---

### Post by jpt85 on 2010-04-15
Ah yes, I did install Ubuntu via wubi and inside Windows.  Thanks Travis and perham, both of you have been tremendously helpful.  I will now do a clean install and take your advice.  

Thanks!  Case closed!  :P

---

### Post by ttshivers on 2010-04-15
Remember to mark this thread as solved.

---

