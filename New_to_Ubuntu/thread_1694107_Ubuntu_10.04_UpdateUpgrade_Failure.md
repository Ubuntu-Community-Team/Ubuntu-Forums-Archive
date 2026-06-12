---
title: "Ubuntu 10.04 Update/Upgrade Failure"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by Malkhut on 2011-02-23
I have been getting some "failure to fetch" errors when I try to do updates in ubuntu 10.04.  I checked the forum threads, and this error seems to be a problem in the package sources list every time, but it seems different for everyone.  I haven't been able to see anything in my sources list that I can immediately identify as "wrong".  

I tried upgrading to 10.10, in the hopes that it would just get rid of unnecessary old packages, but that is failing too. 

Here is my sources list:

```
 # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
# deb http://deb.torproject.org/torproject.org karmic main
# deb http://ppa.launchpad.net/rvm/mplayer/ubuntu karmic main # mplayer + ***
# deb-src http://ppa.launchpad.net/rvm/msudo apt-get clean
sudo apt-get update && sudo apt-get upgradeplayer/ubuntu karmic main # mplayer + ***
```

Here is the 10.10 upgrade error message:

```
 Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'maverick.tar.gz'
authenticate 'maverick.tar.gz' against 'maverick.tar.gz.gpg' 
tar: Removing leading `/' from member names

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information
WARNING: Failed to read mirror file

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

100% [Working] 
Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report.
```

Any ideas?  Thanks.

---

### Post by Gixxy on 2011-02-23
I am interested in this question as well. 

Can you jump versions or do they need to be upgraded in order?

---

### Post by jeremyjjbrown on 2011-02-23
Just do a fresh install of the new version. It will save you a ton of headaches.

---

### Post by sandyd on 2011-02-24
> **Malkhut said:**
> I have been getting some "failure to fetch" errors when I try to do updates in ubuntu 10.04.  I checked the forum threads, and this error seems to be a problem in the package sources list every time, but it seems different for everyone.  I haven't been able to see anything in my sources list that I can immediately identify as "wrong".  

I tried upgrading to 10.10, in the hopes that it would just get rid of unnecessary old packages, but that is failing too. 

Here is my sources list:

```
 # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
# deb http://deb.torproject.org/torproject.org karmic main
# deb http://ppa.launchpad.net/rvm/mplayer/ubuntu karmic main # mplayer + ***
# deb-src http://ppa.launchpad.net/rvm/msudo apt-get clean
sudo apt-get update && sudo apt-get upgradeplayer/ubuntu karmic main # mplayer + ***
```Here is the 10.10 upgrade error message:

```
 Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'maverick.tar.gz'
authenticate 'maverick.tar.gz' against 'maverick.tar.gz.gpg' 
tar: Removing leading `/' from member names

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information
WARNING: Failed to read mirror file

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

100% [Working] 
Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report.
```Any ideas?  Thanks.
should be
```

 # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to # newer versions of the distribution.  deb http://archive.ubuntu.com/ubuntu/ lucid main restricted deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted  ## Major bug fix updates produced after the final release of the ## distribution. deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team. Also, please note that software in universe WILL NOT receive any ## review or updates from the Ubuntu security team. deb http://archive.ubuntu.com/ubuntu/ lucid universe deb-src http://archive.ubuntu.com/ubuntu/ lucid universe deb http://archive.ubuntu.com/ubuntu/ lucid-updates universe deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates universe  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  ## team, and may not be under a free licence. Please satisfy yourself as to  ## your rights to use the software. Also, please note that software in  ## multiverse WILL NOT receive any review or updates from the Ubuntu ## security team. deb http://archive.ubuntu.com/ubuntu/ lucid multiverse deb-src http://archive.ubuntu.com/ubuntu/ lucid multiverse deb http://archive.ubuntu.com/ubuntu/ lucid-updates multiverse deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates multiverse  ## Uncomment the following two lines to add software from the 'backports' ## repository. ## N.B. software from this repository may not have been tested as ## extensively as that contained in the main release, although it includes ## newer versions of some applications which may provide useful features. ## Also, please note that software in backports WILL NOT receive any review ## or updates from the Ubuntu security team. # deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse # deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse  ## Uncomment the following two lines to add software from Canonical's ## 'partner' repository. ## This software is not part of Ubuntu, but is offered by Canonical and the ## respective vendors as a service to Ubuntu users. # deb http://archive.canonical.com/ubuntu jaunty partner # deb-src http://archive.canonical.com/ubuntu jaunty partner  deb http://security.ubuntu.com/ubuntu lucid-security main restricted deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted deb http://security.ubuntu.com/ubuntu lucid-security universe deb-src http://security.ubuntu.com/ubuntu lucid-security universe deb http://security.ubuntu.com/ubuntu lucid-security multiverse deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse # deb http://deb.torproject.org/torproject.org karmic main # deb http://ppa.launchpad.net/rvm/mplayer/ubuntu karmic main # mplayer + *** 

```
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano /etc/apt/sources.list
#pasteabovestuff
#Press Control + X
sudo apt-get update

```

---

### Post by Malkhut on 2011-03-05
Thanks for the advice.  I will give it a try SD.  I am hoping to avoid a clean install, because I have a windows XP partition.  I am not sure if I would have to go through the giant headache of erasing them both, repartitioning, etc.  

That, and it's a pain to backup all my crap.  Yes, I know I should backup my stuff anyways, but it's a lot of stuff that wouldn't be the end of the world to lose, but it would be a pain.  (Famous last words)

Edit:  I'm still getting "failed to fetch" errors when I run the update.

```
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_CA                       
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                             
Ign [http://ppa.launchpad.net/freshwwa/pp/ubuntu/](http://ppa.launchpad.net/freshwwa/pp/ubuntu/) lucid/main Translation-en_CA              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                            
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA                         
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA         
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]                           
Ign [http://ppa.launchpad.net/freshwwa/ppa/ubuntu/](http://ppa.launchpad.net/freshwwa/ppa/ubuntu/) lucid/main Translation-en_CA                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                   
Ign [http://ppa.launchpad.net/freshwww/ppa/ubuntu/](http://ppa.launchpad.net/freshwww/ppa/ubuntu/) lucid/main Translation-en_CA                   
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg                                            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA                     
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                   
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,098B]                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [150kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                             
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages       
  404  Not Found
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [47.4kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [64.8kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [19.4kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,995B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [651B]
Fetched 331kB in 1s (208kB/s)                     
W: Failed to fetch [http://ppa.launchpad.net/freshwwa/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/freshwwa/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/freshwwa/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/freshwwa/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Kixtosh on 2011-03-05
> **Gixxy said:**
> I am interested in this question as well. 

Can you jump versions or do they need to be upgraded in order?It's not a good idea to jump into a thread with a different question. They mostly get ignored. But to answer your question a succinctly as possible:

You cannot jump versions using the Update Manager, except LTS (Long Term Support) release versions, so:

=> You can jump two years from 8.04 to 10.04 skipping 8.10, 9.04 and 9.10. 10.04 Lucid Lynx will remain the most current LTS release until 12.04.

=> You cannot jump one year from 8.10 to 9.10, skipping 9.04. Non LTS releases are available every six months.

To do this, you need to check the option in the Update Manager (it's in the System => Administration drop down menu) by navigating to the Settings menu, and find the Updates tab. There you can select Long term support releases only, instead of Normal releases (or Never, which is also an option).

This only applies if you wish to upgrade via the Update Manager. You still have the option to skip from any release to any other release by simply installing it manually (a complete fresh install). You'll frequently read forum members stating that this is the fastest and best way to upgrade anyway, but it requires backing up all your home folder documents.

---

### Post by Kixtosh on 2011-03-05
> **Malkhut said:**
> ... I am hoping to avoid a clean install, because I have a windows XP partition.  I am not sure if I would have to go through the giant headache of erasing them both, repartitioning, etc. ...I've done this before, and with a little care, it's not that daunting. There's always some risk involved though, especially since you don't want to back up your XP files. This may not be the best way there is to do this, but here is how I would proceed.

Using a LiveCD of whatever version you prefer to use:

1) Boot XP first and defragment everything visible to XP on the hard drive about three times. Each subsequent time defragments a little more than before, and faster too, especially on the last try, usually. If it's still taking a long time to complete, then the drive may still be too fragmented to proceed yet.

2) Boot into the LiveCD and use it to back up any information you left on the hard drive in your home folder to an external disk. You probably don't want to do this, I know, from what you wrote earlier.

3) From the LiveCD, look for GParted in the System Menu. Using GParted, format the existing Ubuntu partitions to wipe them clean. You may have to turn off swap for this (if you see a lock icon next to it), but you can do that with GParted.

4) To minimize the risk of errors, do NOT resize your XP partition. In fact, I wouldn't resize any partitions, since you don't want to back up your XP files.

5) Then install Ubuntu again, as you did before. It should set up new partitions exactly as before, to replace the ones you formated earlier.

Because of some changes in the installation procedures, it may be easier if you install the same version you were using before (when it was working), since that will be more familiar to you. Just make sure when you get to the partitions menu that you're not telling it to use the entire disk, which would wipe XP as well. It must be a side-by-side installation. XP is a lot more forgiving than Vista or Windows 7 by reputation so you should be fine, but it can only be stressed that there will always be some risk involved.

---

### Post by jeremyjjbrown on 2011-03-05
> I would have to go through the giant headache of erasing them both, repartitioning, etc. 

No you don't. It's not hard. Reinstall Ubuntu to / and leave everything else alone. If you have a /home partition (you probably do not) you will want to erase hidden folders that contain application info.

There are many guides online on how to do it. Tombuntu has a good one.

---

