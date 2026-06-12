---
title: "Can't match cairo-dock public key."
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Confuseling on 2009-02-24
Can anyone tell me what I might be doing wrong? Ubuntu eee 8.04 distro updated to 8.10, so I think really it's now more like Ubuntu with the array kernel, and I'm in the right forum. Check the bold in the following.

```

mike@mikeee:~$ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/FD0C2C24 2008-06-12
uid                  Array.org APT Signing Key <archive@array.org>
sub   2048g/0B146E52 2008-06-12

pub   1024D/0C5A2783 2006-11-23
uid                  Medibuntu Packaging Team <admin@lists.medibuntu.org>
uid                  The Medibuntu Team <medibuntu@sos-sts.com>
sub   2048g/16C7105A 2006-11-23

pub   1024D/6A423791 2006-09-26 [expires: 2009-09-25]
uid                  Opera Software Archive Automatic Signing Key <hostmaster@opera.com>
sub   2048g/BEAEDCB7 2006-09-26 [expires: 2009-09-25]

[B]pub   1024D/41317877 2008-04-27
uid                  Cairo-Dock Team (Cairo-Dock Official Repository) <repository@cairo-dock.org>
sub   2048g/00836283 2008-04-27[/B]

pub   1024R/BF810CD5 2009-01-19
uid                  Launchpad PPA for Awn Testing Team


mike@mikeee:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb http://ppa.launchpad.net/netbook-remix-team/ubuntu intrepid main
deb http://deb.opera.com/opera/ stable non-free

deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu intrepid main
[B]deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock

[/B]
mike@mikeee:~$ sudo apt-get update && sudo apt-get install cairo-dock cairo-dock-plug-ins
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_GB                                                                           
Hit http://security.ubuntu.com intrepid-security Release.gpg                                                                                  
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB                                                                       
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB                                                                 
Hit http://ppa.launchpad.net intrepid Release.gpg                                                                                             
Ign http://ppa.launchpad.net intrepid/main Translation-en_GB                                                                                  
Hit http://archive.canonical.com intrepid Release                                                                                             
Hit http://gb.archive.ubuntu.com intrepid Release.gpg                                                                                         
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB                                                                              
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB                                                                        
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB                                                                          
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB                                                                        
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg                                                                                 
Hit http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB                                                                      
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB                                                                
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB                                                                  
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB                                                                
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB                                                                   
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB                                                                 
Hit http://security.ubuntu.com intrepid-security Release                                                                                      
Hit http://ppa.launchpad.net intrepid Release                                                                                                 
Ign http://repository.cairo-dock.org intrepid Release.gpg                                                                                     
Ign http://repository.cairo-dock.org intrepid/cairo-dock Translation-en_GB                                                                    
Hit http://gb.archive.ubuntu.com intrepid Release                                                                                             
Hit http://gb.archive.ubuntu.com intrepid-updates Release                                                                                     
Ign http://repository.cairo-dock.org intrepid Release                                                                                         
Hit http://packages.medibuntu.org intrepid Release.gpg                                                                                        
Hit http://deb.opera.com stable Release.gpg                                                                                                   
Ign http://deb.opera.com stable/non-free Translation-en_GB                                                                                    
Hit http://archive.canonical.com intrepid/partner Packages                                                                                    
Ign http://packages.medibuntu.org intrepid/free Translation-en_GB                                                                             
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_GB                                                    
Ign http://repository.cairo-dock.org intrepid/cairo-dock Packages                                                                             
Hit http://security.ubuntu.com intrepid-security/main Packages                                                                                
Hit http://deb.opera.com stable Release                                                                                                       
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                           
Hit http://packages.medibuntu.org intrepid Release                                                                                            
Hit http://gb.archive.ubuntu.com intrepid/main Packages                                                                                       
Hit http://repository.cairo-dock.org intrepid/cairo-dock Packages                                                                            
Ign http://ppa.launchpad.net intrepid/main Sources                                                                                            
Hit http://security.ubuntu.com intrepid-security/restricted Packages                                                                          
Hit http://security.ubuntu.com intrepid-security/main Sources                                                                          
Hit http://security.ubuntu.com intrepid-security/restricted Sources                                                                    
Hit http://security.ubuntu.com intrepid-security/universe Packages                                                                     
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages                                                                                 
Hit http://gb.archive.ubuntu.com intrepid/main Sources                                                                                        
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources                                                                                  
Hit http://gb.archive.ubuntu.com intrepid/universe Packages                                                                                   
Hit http://gb.archive.ubuntu.com intrepid/universe Sources                                                                                    
Hit http://security.ubuntu.com intrepid-security/universe Sources                                                                             
Hit http://security.ubuntu.com intrepid-security/multiverse Packages                                                                          
Hit http://security.ubuntu.com intrepid-security/multiverse Sources                                                                           
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                           
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages                                                                                 
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources                                
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages                             
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages                       
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources                              
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources                        
Ign http://deb.opera.com stable/non-free Packages                                                                                       
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages                                                                     
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources                                                
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages                                             
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources                                              
Hit http://ppa.launchpad.net intrepid/main Sources                                                                
Hit http://packages.medibuntu.org intrepid/free Packages                                                          
Hit http://packages.medibuntu.org intrepid/non-free Packages                                                      
Hit http://deb.opera.com stable/non-free Packages
Hit http://www.array.org intrepid Release.gpg  
Ign http://www.array.org intrepid/eeepc Translation-en_GB
Hit http://www.array.org intrepid Release
Hit http://www.array.org intrepid/eeepc Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  cairo-dock cairo-dock-plug-ins
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.4MB of archives.
After this operation, 2097kB of additional disk space will be used.
[B]WARNING: The following packages cannot be authenticated!
  cairo-dock cairo-dock-plug-ins
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated[/B]

```

Synaptic has the same result, and it's been like that for over a day. Any ideas? Thanks.

ETA - these are the instructions, by the way. [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

They don't seem substantially different to those on the cairo wiki.

---

### Post by Confuseling on 2009-02-24
Solution (ish)

Removed the repo from the sources list, and just used the version in the ubuntu repo. I don't think it's the same version number, so I won't mark this solved yet...

---

### Post by fabounet on 2009-02-24
"used the version in the ubuntu repo"
not a good idea since it's totally broken
don"t know how to solve that but it doesn't prevent you to install it does it ?

---

### Post by Confuseling on 2009-02-24
> **fabounet said:**
> ...not a good idea since it's totally broken
...

Still works better than AWN though doesn't it? :lolflag:

Yes, I may be reduced to ignoring the warning. I just hoped somebody might be able to banish - or at least explain - it.

---

