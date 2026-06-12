---
title: "what does it mean &quot;not authenticated&quot;"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by geltonas on 2009-03-24
Hi,I am about two things: not authenticated softwares and wrong keys for sources. First, I get notification up on the right side desktop, when I click it on, it brigs me update manager, witch gives me the warring massage that I am trying to install not authenticated software. Second, when I use command   [FONT="Arial Narrow"]sudo apt-get update[/FONT]this gives me some warning massages, please have a look down on the list:
```
lbox@lbox-laptop:~$ sudo apt-get update
[sudo] password for lbox: 
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_GB [27.0kB]
Get: 3 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg [189B]                
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Get: 4 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_GB [1135B] 
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_GB [8049B]
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_GB [46.0kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_GB              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_GB          
Get: 8 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]                 
Get: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg [189B]   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Get: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_GB [27.0kB]
Get: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB [1135B]
Get: 12 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_GB [8049B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Get: 13 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB [46.0kB]
Get: 14 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg [189B]         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_GB         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Get: 15 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release [65.9kB]
Get: 16 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release [51.2kB]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release                         
Get: 17 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release [51.2kB]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
Fetched 165kB in 0s (185kB/s)
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I changed the sources.list because I was looking for particular drives for my machine, after I tried to change servers for downloading ubuntu softs but it gave me nothing.

**How can I bring my ubutnu to trusted security level?**

---

### Post by philinux on 2009-03-24
Open a terminal and post back with ooutput of this.

```
cat /etc/apt/sources.list
```

Wrap code tags around when posting.

---

### Post by geltonas on 2009-03-24
> **philinux said:**
> Open a terminal and post back with ooutput of this.

```
cat /etc/apt/sources.list
```

Wrap code tags around when posting.
```
lbox@lbox-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://packages.medibuntu.org/ intrepid free non-free

```

---

### Post by philinux on 2009-03-24
Make sure you close all package managers ie add/remove and synaptic.

Click the medibuntu link below and follow the instructions to add the key.

Then

```
sudo apt-get update && sudo apt-get upgrade
```

---

