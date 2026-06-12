---
title: "What the  is FUSE"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by eddski on 2009-09-06
I still having problems using k3b as a regular user. I ran into some info about FUSE and .gvfs. It's my understanding that FUSE allows a regular to create a file system without editing the kernel code(wikipedia). It seems to me that I am trying to create a file system when burning a cd/dvd, but how do I get k3b to allow me to do that as a regular user?

---

### Post by nandemonai on 2009-09-06
Have you added yourself to the fuse group?

---

### Post by tgalati4 on 2009-09-06
File System User Space--FUSE does indeed allow you to easily mount drives as a regular user.  However, I don't see how it is related to k3b burning issues.  Perhaps /dev/cdrom is not writeable by you as a regular user.

What is the output of:

ls -la /dev/cdrom

In Linux Mint 7 (based on Jaunty)

tgalati4@tpad-Gloria7 ~ $ ls -la /dev/cdrom
lrwxrwxrwx 1 root root 3 2009-09-06 12:28 /dev/cdrom -> sr0

It's owned by root, but writeable by everyone.

To see if you have fuse running:

ps -ef | grep fuse

tgalati4@tpad-Gloria7 ~ $ ps -ef | grep fuse
tgalati4  3334     1  0 19:29 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/tgalati4/.gvfs
tgalati4  6280  6052  0 19:38 pts/0    00:00:00 grep --colour=auto fuse

It appears that the fuse daemon (background process) is part of the gnome virtual file system (gvfs).

Again, fuse is separate from cdrom burning, unless of course you are trying to burn a disk from an image that you mounted from across the network using fuse.  But that's another issue.  Latency on a network drive becomes an error-producing issue.

---

### Post by eddski on 2009-09-06
For nandemonai
I did not know there was a fuse group. I checked and for some reason the first user (me) was not added to the fuse group, that sounds strange, could that be because the first user created is added to the admin group?
 
For tgalati4
The output from ls -la /dev/cdrom is:

ls: cannot access /dev/cdrom: No such file or directory

---

### Post by pi.boy.travis on 2009-09-06
> **eddski said:**
> For nandemonai
I did not know there was a fuse group. I checked and for some reason the first user (me) was not added to the fuse group, that sounds strange, could that be because the first user created is added to the admin group?
 
For tgalati4
The output from ls -la /dev/cdrom is:

ls: cannot access /dev/cdrom: No such file or directory


On my computer it is called /dev/cdrom0.  Maybe give that a try?

Hope this helps. . .

---

### Post by eddski on 2009-09-06
got the same result with cdrom0

---

### Post by eddski on 2009-09-06
sorry, I thought my cd/dvd writer was recognized, but apparently it is not. Adding myself to the fuse group solved one problem(thanks). But how would I go about getting Ubuntu to recognize my cd/dvd writer?

---

### Post by nandemonai on 2009-09-07
Try /dev/sr0 ;)

---

### Post by pi.boy.travis on 2009-09-07
Could you post the output of:

sudo lshw

Just a warning, it's gonna be a big one, but it should let us know if your drive is detected.

---

### Post by tgalati4 on 2009-09-07
dmesg | grep sr

tgalati4@tpad-Gloria7 ~ $  dmesg | grep sr
[    3.267884] Driver 'sr' needs updating - please use bus_type methods
[    3.866460] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.866641] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.866724] sr 1:0:0:0: Attached scsi generic sg1 type 5

---

### Post by eddski on 2009-09-07
output for lshw( I just copied the ide stuff since my cd/dvd is the only ide hardware)

        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
           *-disk
                description: SCSI Disk
                product: DVD RW DRU-V202A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sdb
                version: 1.60
                serial: [SONY    DVD RW DRU-V202A1.60 Sep02,2008
                capabilities: removable
                configuration: ansiversion=5
              *-medium
                   physical id: 0
                   logical name: /dev/sdb

let me know if you want the rest

---

### Post by eddski on 2009-09-07
the output from ls -la /dev/sr0 are:

ls: cannot access /dev/sr0: No such file or directory

---

### Post by eddski on 2009-09-07
result of dmesg |grep sr :
[    1.221776] Driver 'sr' needs updating - please use bus_type methods
[   14.442852] type=1505 audit(1252370018.669:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2083
[   14.487696] type=1505 audit(1252370018.713:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2087
[   14.487737] type=1505 audit(1252370018.713:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2087
[   14.609516] type=1505 audit(1252370018.837:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2092
[   14.609700] type=1505 audit(1252370018.837:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2092
[   14.637410] type=1505 audit(1252370018.865:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2096

what does this command display?

---

### Post by tgalati4 on 2009-09-07
dmesg is simply a list of messages in seconds since boot.  The pipe command | simply pipes the output of dmesg into grep command.  Grep is gnu's regular expression parser.  In this case it is searching for instances of "sr" and prints out the entire line that contains at least one "sr".

According to lshw, which is simply a massive list (ls) of hardware (hw), your DVD-RW is detected as a Sony, so it should work.  Do DVD's play on it?  How about CD's.  First you need to determine if the drive is even working properly.

---

### Post by eddski on 2009-09-08
I put in a dvd with files burned to it and it says "unable to mount location no media in the drive". I also tried a movie and it came back with "AN ERROR OCURRED Could not open location; you might not have permission to open the file". I tried to open it with the movie player. The drive is working properly as I dual boot w/windows and can burn anything.

---

### Post by unutbu on 2009-09-08
eddski, I think the problem is that Ubuntu is associating your DVD drive with /dev/sdb. 
```

description: SCSI Disk
product: DVD RW DRU-V202A
vendor: SONY
physical id: 0.0.0
bus info: scsi@4:0.0.0
logical name: **/dev/sdb**
```

Usually /dev/sdb is reserved for hard drives, not DVD drives.
Fixing this the proper way may require altering a file in /etc/udev/rules.d so the DVD drive will get associated to /dev/sr0 rather than /dev/sdb. Unfortunately, I don't know exactly what needs to be changed there. I suggest you report this bug on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/udev](https://bugs.launchpad.net/ubuntu/+source/udev)

You may also want to read this guide on how to file bug reports:
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

In the mean time, I have an idea which *might* allow you to use the DVD drive as it is (still bound to /dev/sdb).

Please post the contents of /etc/fstab.

---

### Post by eddski on 2009-09-08
For unutbu the output of /etc/fstab :

# /etc/fstab: static file system information.

#

# Use 'vol_id --uuid' to print the universally unique identifier for a

# device; this may be used with UUID= as a more robust way to name devices

# that works even if disks are added and removed. See fstab(5).

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# / was on /dev/sda5 during installation

UUID=47f26ffe-858c-4012-b7f5-c8d9d3aea73c /               ext3    relatime,errors=remount-ro 0       1

# /boot was on /dev/sda3 during installation

UUID=7550dc2b-f9a4-4541-bc92-2f53c084ce82 /boot           ext3    relatime        0       2

# /home was on /dev/sda8 during installation

UUID=7fc419af-88c8-47d6-b566-b86ebc9bcacb /home           ext3    relatime        0       2

# /tmp was on /dev/sda9 during installation

UUID=3edd655a-1abd-40b9-8812-95d3c0fbcc3b /tmp            ext3    relatime        0       2

# /usr was on /dev/sda7 during installation

UUID=959aa2e7-6b7c-463c-91f7-0aaa0b971bb9 /usr            ext3    relatime        0       2

# /var was on /dev/sda10 during installation

UUID=e5868b2a-cda8-41ed-9179-478b3e5e8604 /var            ext3    relatime        0       2

# /windows was on /dev/sda11 during installation

UUID=5AA4-FF52  /windows        vfat    utf8,umask=007,gid=46 0       1

# swap was on /dev/sda6 during installation

UUID=cd901a66-554f-435c-8d21-ba01d732e76a none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I hope you can read this correctly..

---

### Post by unutbu on 2009-09-08
Again, I'm not entirely sure this will work, but how about try the following:

At a terminal prompt, run 
```

gksu gedit /etc/fstab        
```

Change
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```
to

```

# /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```
Save and exit the text editor.

Then pop in a CD or DVD and see if it works.

If it doesn't work, go to the terminal and type
```

ls -l /media
ls -l /dev/sdb /dev/scd* /dev/sr*
sudo mount /dev/cdrom0
```

and post the output.

---

### Post by eddski on 2009-09-09
Fro unutbu:
I thought my problems were solved. Everything worked(DVD movie and a DVD with files on it) until I restarted and then nothing. Below is the uotput you requested.
Output for      ls -l /media


total 4

lrwxrwxrwx 1 root root    6 2009-07-21 22:22 cdrom -> cdrom0

drwxr-xr-x 2 root root 4096 2009-07-21 22:22 cdrom0



Output for      ls -l /dev/sdb /dev/scd* /dev/sr*


ls: cannot access /dev/scd*: No such file or directory

ls: cannot access /dev/sr*: No such file or directory

brw-rw---- 1 root disk 8, 16 2009-09-08 14:50 /dev/sdb

Uotput for       sudo mount /dev/cdrom0


mount: can't find /dev/cdrom0 in /etc/fstab or /etc/mtab

---

### Post by unutbu on 2009-09-09
eddski, could you post the output of 
```

sudo lshw -C disk
```

again?

---

### Post by tgalati4 on 2009-09-09
Wouldn't a symbolic link be simpler:

Add to /etc/rc.local (before the "exit 0")

ln -s /dev/sdb /dev/sr0

Sometimes it's easier to give in than to fight what the system wants to do.

---

### Post by eddski on 2009-09-10
sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK1234GS
       vendor: Toshiba
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: AH00
       serial: X6VLF4HLS
       size: 111GiB (119GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a566923b
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-842S
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

### Post by unutbu on 2009-09-10
Well I'll be plum pudding in January. They do not look like the same hardware at all...
```

*-disk                                          *-cdrom							   
description: SCSI Disk				description: DVD-RAM writer				   
product: DVD RW DRU-V202A			product: DVD-RAM UJ-842S				   
vendor: SONY					vendor: MATSHITA					   
physical id: 0.0.0				physical id: 1						   
bus info: scsi@4:0.0.0				bus info: scsi@1:0.0.0					   
logical name: /dev/sdb				logical name: /dev/cdrom				   
version: 1.60					logical name: /dev/cdrw					   
serial: [SONY DVD RW DRU-V202A1.60 Sep02,2008	logical name: /dev/dvd					   
capabilities: removable				logical name: /dev/dvdrw				   
configuration: ansiversion=5			logical name: /dev/scd0					   
						logical name: /dev/sr0					   
						version: 1.01						   
						capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram 
						configuration: ansiversion=5 status=nodisc                 


```
The current DVD drive looks to be properly detected and should be 
accessible at /dev/scd0. In this case, you should edit /etc/fstab:
```

gksu gedit /etc/fstab
```

and change
```

# /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```
back to```


/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

---

### Post by eddski on 2009-09-11
So what does "ln -s /dev/sdb /dev/sr0" do? It looks like a soft link directly the cd. Will that affect everyone who logs in? It also seems to only work when I turn the machine on and there is a cd/dvd in the drive.

---

