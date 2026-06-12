---
title: "Ubuntu Noob w/Stoopid Question.  Ubuntu Hiding Data Files"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by ZekeMenuar on 2009-01-07
Installed Ubuntu 8.10 yesterday.  

Running on a Enpower EN660 (MSI) laptop.
1.8gb Duo core 2
3gb RAM
Vista/XP dual boot.

So far I'm underwhelmed with Ubuntu.  But I'm determined to be rid of this guy.  I'm going to make this work.

[IMG]http://img.photobucket.com/albums/v145/ZekeMenuar1/BillBorg2.jpg[/IMG]

I played with the Cd then decided to install Ubuntu.  My box has two partitions.  One 12gb partiton for XP and a 100+gb partition for Vista.  The Vista partiton has all my music, pics etc (yes, it's backed up on another box).  FWIW, I like Vista and run the Vista side 99% of the time.  I've been running dual-boot systems since 2000.  I still don't trust Windoze to be 100% all the time.  That philosophy has saved me a lot of grief over the years.

Back on topic.

One of the issues I wasn't able to solve, started before the installation of Ubuntu.  I tried to erase the XP partition.  Vista wasn't having any of it.  The XP side is the system/boot partiton.  That means I probably installed XP first, then Vista.  My bad.  I'm getting a new HD later in the year. I'll install the OS properly then.

I went ahead and installed Ubuntu.  The Ubuntu installer put the OS on the Vista side.

No biggie right?  

Wrong.  The Vista partiton has all my music on it almost 60 gigs.  
When I'm in Ubuntu, Ubuntu doesn't see any files on the partiton other than Ubuntu files.  

I went through some of the stickys and did some Googling to no avail.

If someone has a fix or some links to help solve this problem, I'd appreciate the help.  Using traditional Windoze problem solving methods isn't working.

I'm posting from the Vista side right now.  I'm booting into Ubuntu to fix some of the nagging little problems.

Thanks in Advance

ZM

---

### Post by Elfy on 2009-01-07
Open a terminal - in Applications > Accessories.

Paste this, or type it

```
sudo apt-get install ntfs-config
```

Once it has installed - look in the System Tools menu for the NTFS Tool, using that you can get access to your ntfs drives. 

Now run

```
sudo mount -a
```

If your drives are now visible in the file manager - Places that is it done, if they aren't reboot.

Any command in a terminal using sudo will require your password - enter it when prompted, it will not show when you type it - this is normal.

If you get any errors with the commands, please paste the error here so we can see.

---

### Post by Vantrax on 2009-01-07
So you installed it in windows with WUBI?

Or as its own partition?

The output of sudo fdisk -l will give a us a better idea.

---

### Post by Elfy on 2009-01-07
aah yes wubi - if you did install it with wubi then oprn nautilus and navigate in filesystem to /host - they should be there.

If you have trouble with the file manager then run this in a terminal

```
nautilus /host
```

---

### Post by ZekeMenuar on 2009-01-07
> **Vantrax said:**
> So you installed it in windows with WUBI?

Or as its own partition?

The output of sudo fdisk -l will give a us a better idea.

Tried the other suggestions.  No luck

Installed with Windoze.  

sudo fdisk -1 as requested

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1440326c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         128     1028128+  27  Unknown
/dev/sda2   *         129        1658    12289725    7  HPFS/NTFS
/dev/sda3            1659       14593   103900387+   7  HPFS/NTFS

Disk /dev/sdb: 2006 MB, 2006974464 bytes
16 heads, 32 sectors/track, 7656 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xb23c895e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16        7656     1955904    e  W95 FAT16 (LBA)
zekemenuar@ubuntu:~$

Thanks

ZM

---

### Post by Elfy on 2009-01-07
Please run these commands and paste the outputs 

```
cat /etc/fstab
mount
blkid
```

Can you please surround each with code tags - makes it easier to read in a code box :)
Put [noparse]```
[/noparse] at the beginning of the paste and then [noparse]
```[/noparse] at the end.

---

### Post by Paqman on 2009-01-07
> **ZekeMenuar said:**
> 
I went ahead and installed Ubuntu.  The Ubuntu installer put the OS on the Vista side.

No biggie right?  

Wrong.  The Vista partiton has all my music on it almost 60 gigs.  
When I'm in Ubuntu, Ubuntu doesn't see any files on the partiton other than Ubuntu files.  


If you've installed using Wubi all the files on that partition should be available at /host, which should also be on your Places menu.

---

### Post by Elfy on 2009-01-07
> **Paqman said:**
> If you've installed using Wubi all the files on that partition should be available at /host, which should also be on your Places menu.

whoops - changed it now

---

### Post by ZekeMenuar on 2009-01-07
> **forestpixie said:**
> Please run these commands and paste the outputs 

```
cat /etc/fstab
mount
blkid
```

Can you please surround each with code tags - makes it easier to read in a code box :)
Put [noparse]```
[/noparse] at the beginning of the paste and then [noparse]
```[/noparse] at the end.

God Gawd! You really want to see all that code?  OK, you asked for it.

```

zekemenuar@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
/dev/sda3	/host	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	00
/dev/sda2	/media/Windoze\040XP	ntfs-3g	defaults,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8	0	0
/dev/loop0	/media/loop0_	ext3	defaults	0	2
/dev/sda1	/media/recovery	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/host/ubuntu/disks/root.disk	/	ext3	loop,errors=remount-ro	0	1
/host/ubuntu/disks/boot	/boot	none	bind	0	0
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0


zekemenuar@ubuntu:~$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /media/Windoze XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/loop0 on /media/loop0_ type ext3 (rw)
/dev/sda1 on /media/recovery type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zekemenuar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zekemenuar)
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
zekemenuar@ubuntu:~$ blkid 
```

The partition shows up in the device manager.  99gigs and is labeled the "/host"

It is not listed in "Places"

Thanks

ZM

---

### Post by Elfy on 2009-01-07
No I don't,  I realised after that I didn't need to see it as I had made a typo which paqman picked up.

So your files are there in /host - just not showing places. You can bookmark them - open nautilus and navigate to the file system. Now drag /host formt he right pane down onto the bottom left and it will make a shortcut to it

---

### Post by Paqman on 2009-01-07
> **ZekeMenuar said:**
> 
The partition shows up in the device manager.  99gigs and is labeled the "/host"


So you can browse to it in Nautilus? Try Places > Computer > Filesystem > Host.

You can make a shortcut for your desktop if you like, or bookmark it into the Places menu. For any apps (such as music players that want to index your collection) then you can just feed them the path: /host/path/to/files.

---

### Post by ZekeMenuar on 2009-01-07
SOLVED!

I located this command

```

mount -t ntfs [partition name] /mnt 

```

It makes the /host file visible.  I found it in "file system"

At any rate, most of my music is available now.  Listening to BB King.  AIC and Zappa coming up

Thanks for helping

ZM

Any idea how to mark the title as SOLVED?

---

### Post by Paqman on 2009-01-07
What happens if you reboot? Is the drive still visible under /host?

The file /etc/fstab that you posted before lists everything that should be mounted automatically at boot. It showed that the partition sda3 should be automatically mounted at /host, so there shouldn't be any need to use a manual mount command.

---

### Post by ZekeMenuar on 2009-01-07
> **Paqman said:**
> What happens if you reboot? Is the drive still visible under /host?

The file /etc/fstab that you posted before lists everything that should be mounted automatically at boot. It showed that the partition sda3 should be automatically mounted at /host, so there shouldn't be any need to use a manual mount command.

I guess we'll find out

Back in 5

---

### Post by ZekeMenuar on 2009-01-07
> **ZekeMenuar said:**
> I guess we'll find out

Back in 5

Rebooted.  Files are still on the desktop and working.

Found more issues.  A Googling we go!

Thanks again

ZM

---

### Post by Paqman on 2009-01-07
> **ZekeMenuar said:**
> Rebooted.  Files are still on the desktop and working.

Found more issues.  A Googling we go!

Thanks again

ZM

No problems, glad you got it sorted. Feel free to open another thread for help with your other issues if you want it.

---

### Post by slibuntu on 2009-01-07
Thats strange behaviour though. it should have popped up automatically. Hmm...

Oh well, so long as all's ok now

---

### Post by ZekeMenuar on 2009-01-07
> **Paqman said:**
> No problems, glad you got it sorted. Feel free to open another thread for help with your other issues if you want it.

Trust me.  I've found several.

Windoze has made me lazy.  I haven't had to do this much manual stuff since I first started messing around with W2K in 2000.

ZM

---

