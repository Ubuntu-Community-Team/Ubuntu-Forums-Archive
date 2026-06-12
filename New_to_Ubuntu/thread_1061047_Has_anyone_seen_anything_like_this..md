---
title: "Has anyone seen anything like this."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-05
root@ericeclifford:/# apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
  Could not resolve 'packages.medibuntu.org'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release.gpg](http://packages.medibuntu.org/dists/hardy/Release.gpg)  Could not resolve 'packages.medibuntu.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
root@ericeclifford:/#

---

### Post by ericeclifford on 2009-02-05
heres my stuff in the source.list 

# deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse #Added by software-properties
  
  
  
  
  
  
  
  
  
  
  
  
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy restricted main universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy restricted main universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates restricted main universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates restricted main universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted




AND HERES WHATS IN THE medibuntu.list

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

BTW I am chroot edit for my live cd customization, so the edit folder is chrooted and my main installation is on a external harddrive though ever since I copied my source.list from my external harddrive to my edit live cd customization folder it was working til I rebooted andI burned a iso image(it works ok after I do a update 2-3 times on the iso image I made) dont know what wrong with it now.

---

### Post by tubbygweilo on 2009-02-05
My first thought is that > Could not resolve 'archive.ubuntu.com' suggests that the internet connection is not functioning, iirc I have had this a couple of times when I had forgotten to connect my laptop to the cable from the modem:( Any chance of checking your internet connection be it wireless or cable then having another go?

---

### Post by ericeclifford on 2009-02-05
Perhaps ill try to reboot but its a cable and not wireless.

---

### Post by ericeclifford on 2009-02-05
forgot to copy the hosts files into the thing DUH I always forget a few lines of code every customization but I still get this error. 





root@ericeclifford:/# apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [8001B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [416kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages [163kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [903B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources [108kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources [36.2kB]
Fetched 791kB in 4s (189kB/s)                        
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
root@ericeclifford:/# ls
bin   dev  home    initrd.img  media  opt   root  srv  tmp  var
boot  etc  initrd  lib	       mnt    proc  sbin  sys  usr  vmlinuz
root@ericeclifford:/# 



Though when I run apt-get update again it fixes it, it does this on my root on my external harddrive too. it has same sources pretty much. but if I run apt-get update 2 times it fixes it, strange uh? any suggestions?

---

