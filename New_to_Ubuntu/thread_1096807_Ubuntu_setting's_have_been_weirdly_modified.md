---
title: "Ubuntu setting's have been weirdly modified"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by stukpixel on 2009-03-15
After a normal boot up of ubuntu I was surprised to see that it changed my theme from human to a custom blue theme that was present previously yet not changed to before the boot. I changed it back, but I encountered two other issues.

Right now my Synaptic package manager is not functioning (keeps giving me the "failed to check"), and I think its because the sources.list file is corrupted among other things, since I've tried accessing it (its corrupted), I've tried deleting it (does not change anything), and so far every sudo command ends with this message 

[I]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.[/I]

How can I repair this?

Also, my file explorer windows have been reduced to a minimalist look. Its functional, but how do I get the default look back for file exploring?

---

### Post by taurus on 2009-03-15
Post the outputs of these commands from a terminal to see what's wrong with your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
ls -la /etc/apt
cat /etc/apt/sources.list
```

---

### Post by stukpixel on 2009-03-15
ubuntu@ubuntu:~$ ls -la /etc/apt
total 36
drwxr-xr-x   4 root root 4096 2009-03-15 14:52 .
drwxr-xr-x 158 root root 4096 2009-03-15 15:02 ..
drwxr-xr-x   2 root root  167 2008-10-29 23:08 apt.conf.d
-rw-------   1 root root    0 2008-10-29 22:54 secring.gpg
-rw-r--r--   1 root root 2747 2009-03-15 14:52 sources.list
-rw-r--r--   1 root root 2055 2009-03-15 13:37 sources.list~
drwxr-xr-x   2 root root    3 2008-08-14 16:55 sources.list.d
-rw-------   1 root root 2057 2009-03-15 14:38 sources.list.save
-rw-------   1 root root 1200 2008-10-29 22:54 trustdb.gpg
-rw-r--r--   1 root root 6713 2008-10-29 22:54 trusted.gpg
-rw-r--r--   1 root root 6713 2008-10-29 22:54 trusted.gpg~
ubuntu@ubuntu:~$ cat /etc/apt/sources.list
## a “general” sources.list for Hardy Heron; all sources are uncommented.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the ‘backports’
## repository.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical’s
## ‘partner’ repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-03-15
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by stukpixel on 2009-03-15
ubuntu@ubuntu:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Sources
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-03-15
What's the output of this command?

```
ls -la /var/lib/dpkg
```

---

### Post by stukpixel on 2009-03-15
total 5206
drwxr-xr-x 11 root root    4096 2009-03-15 10:04 .
drwxr-xr-x 71 root root    4096 2009-03-15 13:08 ..
drwxr-xr-x  2 root root    4096 2009-03-15 10:04 alternatives
-rw-r--r--  1 root root 1262670 2009-03-15 10:04 available
-rw-r--r--  1 root root 1262670 2009-03-15 13:50 available-old
-rw-r--r--  1 root root       8 2008-10-29 22:53 cmethopt
-rw-r--r--  1 root root     376 2009-03-14 21:03 diversions
-rw-r--r--  1 root root     312 2009-03-14 21:03 diversions-old
drwxr-xr-x  2 root root   24576 2009-03-15 13:50 info
-rw-r-----  1 root root       0 2009-03-15 14:34 lock
drwxr-xr-x  2 root root       3 2008-09-03 12:03 parts
-rw-r--r--  1 root root      65 2008-10-29 23:06 statoverride
-rw-r--r--  1 root root      30 2008-10-29 23:04 statoverride-old
-rw-r--r--  1 root root 1362342 2009-03-15 10:04 status
-rw-r--r--  1 root root 1362342 2009-03-15 13:50 status-old
drwxr-xr-x  2 root root    4096 2009-03-15 13:40 triggers
drwxr-xr-x  2 root root    4096 2009-03-15 10:04 updates
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-03-15
Are you running it from Ubuntu LiveCD?

---

### Post by stukpixel on 2009-03-15
running it from an ubuntu live usb, made via the "usb startup disk" option of 8.10 live cd.

---

### Post by taurus on 2009-03-15
But the LiveCD is for hardy.  Why not use the intrepid LiveCD then?

---

### Post by stukpixel on 2009-03-15
I used the intrepid live cd to make the installation on the usb that I am now running. what did you mean exactly?

---

### Post by taurus on 2009-03-15
But your /etc/apt/sources.list is for hardy.

---

### Post by stukpixel on 2009-03-15
ah. I originally tried replacing sources.lst with something I found online after deleting failed to do anything.It was unreadable beforehand.

---

### Post by taurus on 2009-03-15
If you are running intrepid, should stick with intrepid in /etc/apt/sources.list instead of another release.  Otherwise, you are only asking for trouble.

---

### Post by stukpixel on 2009-03-15
okay. how do you suppose I correct that mistake/fix this problem?

---

### Post by taurus on 2009-03-15
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and change the word **hardy** to **intrepid**.  Then save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by stukpixel on 2009-03-15
still not working. Did as you said and this is the output:

```
ubuntu@ubuntu:~$ gksudo gedit /etc/apt/sources.list
ubuntu@ubuntu:~$ sudo apt-get update
Get:1 http://archive.canonical.com intrepid Release.gpg [189B]
Ign http://archive.canonical.com intrepid/partner Translation-en_US  
Get:2 http://security.ubuntu.com intrepid-security Release.gpg [189B]
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Get:3 http://archive.ubuntu.com intrepid Release.gpg [189B]          
Ign http://archive.ubuntu.com intrepid/main Translation-en_US        
Get:4 http://archive.canonical.com intrepid Release [7007B]          
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Get:5 http://security.ubuntu.com intrepid-security Release [51.2kB]       
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US           
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US             
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US           
Get:6 http://archive.ubuntu.com intrepid-updates Release.gpg [189B]           
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Get:7 http://archive.ubuntu.com intrepid-backports Release.gpg [189B]
Ign http://archive.ubuntu.com intrepid-backports/main Translation-en_US        
Ign http://archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-backports/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Get:8 http://archive.ubuntu.com intrepid Release [65.9kB]                  
Get:9 http://archive.canonical.com intrepid/partner Packages [2199B]           
Get:10 http://archive.canonical.com intrepid/partner Sources [846B]            
Get:11 http://security.ubuntu.com intrepid-security/main Packages [84.2kB]     
Get:12 http://archive.ubuntu.com intrepid-updates Release [51.2kB]
Get:13 http://archive.ubuntu.com intrepid-backports Release [44.0kB]           
Get:14 http://archive.ubuntu.com intrepid/main Packages [1256kB]               
Get:15 http://security.ubuntu.com intrepid-security/restricted Packages [3491B]
Get:16 http://security.ubuntu.com intrepid-security/main Sources [24.3kB]
Get:17 http://security.ubuntu.com intrepid-security/restricted Sources [1154B] 
Get:18 http://archive.ubuntu.com intrepid/restricted Packages [8408B]          
Get:19 http://archive.ubuntu.com intrepid/main Sources [505kB]
Get:20 http://archive.ubuntu.com intrepid/restricted Sources [3113B]
Get:21 http://archive.ubuntu.com intrepid/universe Packages [4542kB]
Get:22 http://archive.ubuntu.com intrepid/universe Sources [1981kB]            
Get:23 http://archive.ubuntu.com intrepid/multiverse Packages [199kB]          
Get:24 http://archive.ubuntu.com intrepid/multiverse Sources [95.8kB]          
Get:25 http://archive.ubuntu.com intrepid-updates/main Packages [307kB]        
Get:26 http://archive.ubuntu.com intrepid-updates/restricted Packages [8097B]  
Get:27 http://archive.ubuntu.com intrepid-updates/main Sources [97.7kB]        
Get:28 http://archive.ubuntu.com intrepid-updates/restricted Sources [2474B]   
Get:29 http://archive.ubuntu.com intrepid-updates/universe Packages [75.1kB]   
Get:30 http://archive.ubuntu.com intrepid-updates/universe Sources [18.6kB]    
Get:31 http://archive.ubuntu.com intrepid-updates/multiverse Packages [10.9kB] 
Get:32 http://archive.ubuntu.com intrepid-updates/multiverse Sources [4118B]   
Get:33 http://archive.ubuntu.com intrepid-backports/main Packages [80.0kB]     
Get:34 http://archive.ubuntu.com intrepid-backports/restricted Packages [14B]  
Get:35 http://archive.ubuntu.com intrepid-backports/universe Packages [37.5kB] 
Get:36 http://archive.ubuntu.com intrepid-backports/multiverse Packages [14B]  
Get:37 http://archive.ubuntu.com intrepid-backports/main Sources [15.8kB]      
Get:38 http://archive.ubuntu.com intrepid-backports/restricted Sources [14B]   
Get:39 http://archive.ubuntu.com intrepid-backports/universe Sources [12.5kB]  
Get:40 http://archive.ubuntu.com intrepid-backports/multiverse Sources [14B]   
Fetched 9597kB in 12s (751kB/s)                                                
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$ sudo apt-upgrade
sudo: apt-upgrade: command not found
ubuntu@ubuntu:~$ 


```

---

### Post by taurus on 2009-03-15
What are the outputs of these commands?

```
sudo fdisk -l
cat /etc/fstab
df -h
uname -a
lsb_release -a
```

---

### Post by stukpixel on 2009-03-15
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b8ca827

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1557    12506564    7  HPFS/NTFS
/dev/sda2   *        1558       18820   138662768    7  HPFS/NTFS
/dev/sda3           18821       19457     5116702+   5  Extended
/dev/sda5           18821       19422     4835533+  83  Linux
/dev/sda6           19423       19457      281106   82  Linux swap / Solaris

Disk /dev/sdb: 4041 MB, 4041211392 bytes
81 heads, 36 sectors/track, 2706 cylinders
Units = cylinders of 2916 * 512 = 1492992 bytes
Disk identifier: 0x00018046

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2707     3946495    c  W95 FAT32 (LBA)

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  216K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.9M  1.5G   1% /dev
tmpfs                 1.5G   60K  1.5G   1% /dev/shm
rootfs                3.1G  1.4G  1.6G  47% /
/dev/sdd1             3.8G  3.8G   11M 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 3.1G  1.4G  1.6G  47% /tmp
/dev/sdb1             299G  131G  168G  44% /media/My Passport
tmpfs                 1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdd1             299G  131G  168G  44% /media/My Passport
tmpfs                 1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             299G  131G  168G  44% /media/My Passport
/dev/sdd1             299G  131G  168G  44% /media/My Passport
tmpfs                 1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdc1             299G  131G  168G  44% /media/My Passport
/dev/sda2             133G   89G   44G  67% /media/Partition_1
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
ubuntu@ubuntu:~$ 

```

---

### Post by taurus on 2009-03-15
So you run intrepid from USB Live.  Don't you have another Linux on /dev/sda5?

---

### Post by stukpixel on 2009-03-15
that is a linux that I can't access/use due to multiple bad sectors on my hard drive.

Thus my reason for using flash drive linux.

---

### Post by taurus on 2009-03-15
Have you tried to mount it?

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda5 /media/ubuntu
df -h
```

---

### Post by stukpixel on 2009-03-15
Well I can mount it, but I can't boot from it.

I am pretty sure this isn't the cause of whatever is wrong with the package manager. I think its because when linux was booting up, maybe due to a wrong key hit, it started giving me an "installing"" status, which If I recall correctly, dealt with some drivers. Fearing further damage I had shut my computer down halfway and then proceeded to restart. The error in the package manager occured right after this.

---

### Post by taurus on 2009-03-15
So you just plan to run Ubuntu from the USB Live then?

---

### Post by stukpixel on 2009-03-15
yes I do.

is there any way to correct this issue?
if there isn't (aside from redoing my entire linux installation; which would make ubuntu not worth it) is there another way to get apps in ubuntu?

---

### Post by taurus on 2009-03-15
You probably screwed up the whole repo table when you switched to hardy in /etc/apt/sources.list.  Maybe recreate a new USB Live again.

---

### Post by stukpixel on 2009-03-15
okay. when I recreate it, will it erase all my current apps as well as some non setting data that I have?

---

### Post by taurus on 2009-03-15
On the USB!  Yes.

---

