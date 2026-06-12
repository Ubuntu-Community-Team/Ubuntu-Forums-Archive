---
title: "Can't Update"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Corinos on 2009-12-29
Hi all,

I am new to Linux (Clearly) and have been having trouble with my package manager (KPackageKit) telling me "A Package Dependancy could not be found." The details say "There are broken dependecies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this situation."

I tried this:

sudo apt-get install synaptic
[sudo] password for *****:                       
Reading package lists... Done                    
Building dependency tree                         
Reading state information... Done                
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  nxclient: Depends: libaudiofile0 but it is not going to be installed
  synaptic: Depends: libglade2-0 (>= 1:2.6.1) but it is not going to be installed
            Depends: libvte9 (>= 1:0.22.0) but it is not going to be installed
            Depends: scrollkeeper
            Recommends: libgnome2-perl but it is not going to be installed
            Recommends: software-properties-gtk but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I have 173 Notifications about this right now, and I don't know what to do about it.

I've done some searching to no avail, and if you need me to post something like a Log, please include how I find that log, heh.

Thanks!

Cor

---

### Post by snowpine on 2009-12-29
Hi Cor, can you post the output of:

```
sudo apt-get -f install
cat /etc/apt/sources.list
```

---

### Post by Corinos on 2009-12-29
sudo apt-get -f install
[sudo] password for *****:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  user-setup linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libaudiofile0
The following NEW packages will be installed:
  libaudiofile0
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
2 not fully installed or removed.
Need to get 0B/83.8kB of archives.
After this operation, 258kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Kubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1)'
in the drive '/cdrom/' and press enter
_____________________________________________________________

That doesn't seem to recognize the Kubuntu 64 disk in the drive.

This is the result of the Cat bit.

deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to                   
# newer versions of the distribution.                                                       

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe                   
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe               
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe           
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by Project PWNED on 2009-12-29
#deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1)]/ karmic main restricted

Try that instead ;-)

---

### Post by snowpine on 2009-12-29
It's always something simple, isn't it? :)

```
kdesu kate /etc/apt/sources.list
```

Type a # symbol at the beginning of this line:

```
deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1)]/ karmic main restricted
```

Save the file and:

```
sudo apt-get update
```

to refresh your package list. The # symbol comments out that particular line, so the package manager won't try to look for the CD any more. Hope that works!

---

### Post by Corinos on 2009-12-29
So I need to edit my sources.list?  Is that what I was just looking at?

Sweet.

I'll respond again when it's done.

---

### Post by Corinos on 2009-12-29
sudo apt-get update

Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                                                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US                                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US                                                                           
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                                                                                                    
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [873B]                                                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                                                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                                                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 3,602B in 1s (3,083B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Ideas?

---

### Post by snowpine on 2009-12-29
Make sure you don't have any other system-related apps running (Synaptic, Update Manager, etc.).

---

### Post by Corinos on 2009-12-29
Rebooted, did an apt-get update (what does that do, exactly?), installed symantic, did all updates and repaired packages!  W00t.  May have also fixed another problem I hadn't mentioned yet.

Thanks A LOT everyone!

cor

PS:  How do I mark this thread as Solved now?

---

