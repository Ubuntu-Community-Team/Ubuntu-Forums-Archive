---
title: "&quot;Run apt-get update to correct these problems&quot;?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by nachos99 on 2009-05-07
I think I need help with my apt-get update (and cleaning up my software archive or software manager).  

Long story short, my mic stopped working with Skype after a kernal update several weeks ago.  So I thought I'd reinstall skype and followed some post where it recommended the commands below which I ran a few days ago. 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo aptitude install skype
```

This didn't fix my Skype mic problem, but I now have a new problem where my update manager says,

"Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
-A previous upgrade which didn't complete
-Problems with some of the installed software
-Unofficial software packages not provided by Ubuntu
-Normal changes of pre-lease version of Ubuntu"

In addition, when I try to add a new language in the language support, it now says, 

"Could not install the full laguage support

Usually this is related to an error in your software archive or software manager.  Check your software preferences in the menu "Administration".  "


So here's what i get when i try sudo apt-get update...


```
desktop:~$ sudo apt-get update
Ign http://download.skype.com stable Release.gpg                               
Ign http://getswiftfox.com unstable Release.gpg                                
Ign http://getswiftfox.com unstable/non-free Translation-en_US                 
Ign http://getswiftfox.com unstable Release                                    
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://getswiftfox.com unstable/non-free Packages                          
Hit http://archive.ubuntulinux.jp hardy/ Release.gpg                           
Ign http://archive.ubuntulinux.jp hardy/ Translation-en_US                     
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Hit http://getswiftfox.com unstable/non-free Packages                          
Ign http://download.skype.com stable Release                                   
Hit http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Hit http://archive.canonical.com hardy Release                                 
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Hit http://archive.ubuntulinux.jp hardy/ Release                               
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://packages.medibuntu.org hardy Release                                
Hit http://download.skype.com stable/non-free Packages                         
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://ppa.launchpad.net hardy Release                                     
Hit http://wine.budgetdedicated.com hardy Release                              
Ign http://archive.ubuntulinux.jp hardy/ Packages                              
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Ign http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://ppa.launchpad.net hardy Release                                     
Hit http://archive.ubuntulinux.jp hardy/ Packages                              
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Ign http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/restricted Sources                      
Hit http://us.archive.ubuntu.com hardy/main Sources                            
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://download.tuxfamily.org hardy Release.gpg                            
Hit http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://us.archive.ubuntu.com hardy/universe Packages                       
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://us.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://us.archive.ubuntu.com hardy-updates/main Sources                    
Ign http://download.tuxfamily.org hardy/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages   
Get:1 http://download.tuxfamily.org hardy Release [1040B]
Ign http://download.tuxfamily.org hardy/multiverse Packages
Get:2 http://download.tuxfamily.org hardy/multiverse Packages [1794B]
Fetched 2834B in 6s (420B/s)   
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com hardy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

and here's my source.list

```
# deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://us.archive.ubuntu.com/ubuntu hardy universe
deb http://wine.budgetdedicated.com/apt hardy main
deb http://ppa.launchpad.net/rvm/ppa/ubuntu hardy main
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
deb http://getswiftfox.com/builds/debian unstable non-free
deb http://download.tuxfamily.org/swiftweasel hardy multiverse 
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/
```

Thanks in advance for any suggestions.

---

### Post by llamabr on 2009-05-07
Here's your problem:

```
W: Duplicate sources.list entry http://us.archive.ubuntu.com hardy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

Try commenting out that canonical one, and running update and upgrade again.

---

### Post by sgosnell on 2009-05-07
You have two repositories duplicated.  Comment out or delete one of each.

---

### Post by nachos99 on 2009-05-07
Thank you for the responses. 

I'm not sure if I did it correctly but I think I commented out the duplicated ones.  It now cleanly does the apt-get update and does not show problems.  

I guess the continued upgrade manager problem is another issue.  

This particular problem with the apt-get and duplicate repositories has been solved.

---

