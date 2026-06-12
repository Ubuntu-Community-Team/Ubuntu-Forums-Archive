---
title: "Repository Indexes"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Mykewl on 2009-01-06
For some reason I cannot download all the repository indexes.
Here is my sources.list
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

See anything I need to change?

---

### Post by handydan918 on 2009-01-06
In my experience, this just happens from time to time. The load on the server is too high, or some other network anomaly hits you. Just try again in a few hours....

---

### Post by some_random_noob on 2009-01-06
What can't it update, and what exactly does it say? Maybe you could use a different server for now if the US one doesn't work.

---

### Post by Mykewl on 2009-01-06
This is an example. Sometimes there are many.
I have tried several servers over many days.
I'm trying to download the updates after installing.

---

### Post by Mykewl on 2009-01-06
The example

Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2](http://archive.linux.duke.edu/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/intrepid/universe/source/Sources.bz2](http://archive.linux.duke.edu/ubuntu/dists/intrepid/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Mykewl on 2009-01-06
Another example



GPG error: [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2](http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/source/Sources.bz2](http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead

---

### Post by kixome on 2009-01-06
Try re-installing bzip2

sudo apt-get autoremove bzip2

sudo apt-get install bzip2

---

### Post by Mykewl on 2009-01-06
mike@mike-desktop:~$ sudo apt-get autoremove bzip2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bzip2 file-roller ubuntu-desktop ubuntu-minimal
0 upgraded, 0 newly installed, 4 to remove and 212 not upgraded.
After this operation, 6242kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 99819 files and directories currently installed.)
Removing ubuntu-minimal ...
Removing ubuntu-desktop ...
Removing file-roller ...
Removing bzip2 ...
Processing triggers for man-db ...
mike@mike-desktop:~$ sudo apt-get install bzip2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  bzip2-doc
The following NEW packages will be installed:
  bzip2
0 upgraded, 1 newly installed, 0 to remove and 212 not upgraded.
Need to get 46.2kB of archives.
After this operation, 164kB of additional disk space will be used.
Get:1 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main bzip2 1.0.5-0.1ubuntu1 [46.2kB]
Fetched 46.2kB in 1s (35.6kB/s)
Selecting previously deselected package bzip2.
(Reading database ... 99609 files and directories currently installed.)
Unpacking bzip2 (from .../bzip2_1.0.5-0.1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up bzip2 (1.0.5-0.1ubuntu1) ...

mike@mike-desktop:~$ sudo apt-get update
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid Release.gpg
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/restricted Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/multiverse Translation-en_US
Get:1 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates Release.gpg [189B]
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/main Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/restricted Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/universe Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/multiverse Translation-en_US
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security Release.gpg
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/main Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/restricted Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/universe Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/multiverse Translation-en_US
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid Release
Get:2 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates Release [51.2kB]
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates Release
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security Release
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main Packages
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/restricted Packages
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main Sources
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/restricted Sources
Get:3 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Packages [4542kB]
Get:4 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Sources [1981kB]   
73% [3 Packages bzip2 17788928] [4 Sources 239800/1981kB 12%]      69.6kB/s 25s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Packages             
  Sub-process bzip2 returned an error code (2)
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/multiverse Packages           
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/multiverse Sources            
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/main Packages         
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/restricted Packages   
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/main Sources          
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/restricted Sources    
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/universe Packages     
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/universe Sources      
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/multiverse Packages   
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/multiverse Sources    
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/main Packages        
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/restricted Packages  
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/main Sources         
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/restricted Sources   
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/universe Packages    
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/universe Sources     
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/multiverse Packages  
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/multiverse Sources   
99% [4 Sources bzip2 7192576]                                       98.0kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Sources              
  Sub-process bzip2 returned an error code (2)
Fetched 6523kB in 57s (113kB/s)                                                
W: GPG error: [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2](http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/source/Sources.bz2](http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by zvacet on 2009-01-06
```
sudo apt-get install ubuntu-minimal ubuntu-desktop
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Mykewl on 2009-01-06
mike@mike-desktop:~$ sudo apt-get install ubuntu-minimal ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  file-roller
Suggested packages:
  lha unrar sharutils lzop rpm ncompress unace p7zip p7zip-full arj
The following NEW packages will be installed:
  file-roller ubuntu-desktop ubuntu-minimal
0 upgraded, 3 newly installed, 0 to remove and 212 not upgraded.
Need to get 768kB of archives.
After this operation, 6078kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main ubuntu-minimal 1.124 [26.5kB]
Get:2 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main file-roller 2.24.1-0ubuntu2 [714kB]
Get:3 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main ubuntu-desktop 1.124 [27.6kB]
Fetched 768kB in 14s (51.8kB/s)                                                
Selecting previously deselected package ubuntu-minimal.
(Reading database ... 99637 files and directories currently installed.)
Unpacking ubuntu-minimal (from .../ubuntu-minimal_1.124_i386.deb) ...
Selecting previously deselected package file-roller.
Unpacking file-roller (from .../file-roller_2.24.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.124_i386.deb) ...
Processing triggers for man-db ...
Setting up ubuntu-minimal (1.124) ...
Setting up file-roller (2.24.1-0ubuntu2) ...

Setting up ubuntu-desktop (1.124) ...
mike@mike-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid Release.gpg
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/restricted Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/multiverse Translation-en_US
Get:1 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates Release.gpg [189B]
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/main Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/restricted Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/universe Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/multiverse Translation-en_US
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security Release.gpg
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/main Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/restricted Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/universe Translation-en_US
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/multiverse Translation-en_US
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid Release
Get:2 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates Release [51.2kB]
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security Release
Ign [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates Release
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main Packages
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/restricted Packages
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/main Sources
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/restricted Sources
Get:3 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Packages [4542kB]
Get:4 [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Sources [1981kB]   
70% [3 Packages bzip2 1462272] [4 Sources 37512/1981kB 1%]         84.5kB/s 22s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Packages             
  Sub-process bzip2 returned an error code (2)
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/multiverse Packages           
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/multiverse Sources            
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/main Packages         
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/restricted Packages   
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/main Sources          
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/restricted Sources    
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/universe Packages     
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/universe Sources      
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/multiverse Packages   
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates/multiverse Sources    
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/main Packages        
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/restricted Packages  
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/main Sources         
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/restricted Sources   
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/universe Packages    
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/universe Sources     
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/multiverse Packages  
Hit [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-security/multiverse Sources   
99% [4 Sources bzip2 6291456]                                       38.3kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid/universe Sources              
  Sub-process bzip2 returned an error code (2)
Fetched 6523kB in 1min52s (58.0kB/s)                                           
W: GPG error: [http://ubuntu.positive-internet.com](http://ubuntu.positive-internet.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2](http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/source/Sources.bz2](http://ubuntu.positive-internet.com/ubuntu/dists/intrepid/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Mykewl on 2009-01-06
Thanks for the suggestions so far.

---

### Post by Mykewl on 2009-02-14
I am still having the same problem. I know the servers get busy but after months i would think I could get in. Are there any more ideas out there.

Thanks in advance.

---

### Post by Mykewl on 2009-02-15
Bump

---

### Post by Gannon8 on 2009-02-15
Perhaps its your internet. Maybe the network is causing errors in the file so that bzip2 cannot extract it.

Also try changing servers as someone else suggested.

---

### Post by Mykewl on 2009-02-20
Bump

---

### Post by Mykewl on 2009-02-20
Assuming I have a network problem where do I start troubleshooting. I did the things listed under System > Help and it checked fine. I have cable internet, cable modem, no router.
The modem is old so I am wondering if it is no longer compatable.
However I have no trouble going to websites. I can go to the repository servers but have not found one that will download everything.

---

### Post by Mykewl on 2009-02-23
I have tried many servers from many countries today.
The failures all seem to be between download 
file 19 and 24 and are bz2zip sub-process bz2 
returned an error code (2)

---

