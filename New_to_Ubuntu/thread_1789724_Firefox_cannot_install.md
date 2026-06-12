---
title: "Firefox cannot install"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by DayLite on 2011-06-24
Firefox would not return to previous site, so I uninstalled it. Then when I wanted to re-install it, this is the message I got.

```
The following packages have unmet dependencies:

firefox: Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
```

How do I fix it? :(

I am using Unity 2

---

### Post by jtarin on 2011-06-24
Check your software sources.
Install Firefox from the 11.04 repository, that's the most current one. 

Some of the packages look like they are too old for 11.04 and look like they are from an earlier version...... 10.04?

Maybe you don't have the multiverse channel enabled and the packages are still there from before you upgraded an older version.

---

### Post by lovinglinux on 2011-06-24
After sorting out the dependency issue, see [this]("http://www.webgapps.org/tutorials/firefox/troubleshooting/features-issues-and-solutions") to solve your problem with the Back functionality in Firefox.

---

### Post by DayLite on 2011-06-24
multiverse channel enabled

Checked software sources, all for Natty.

" Install Firefox from the 11.04 "

Can't

---

### Post by jtarin on 2011-06-24
Try these inthis order.
```
apt-get -f install
apt-get clean all

```

---

### Post by trizrK on 2011-06-24
> **DayLite said:**
> Firefox would not return to previous site, so I uninstalled it. Then when I wanted to re-install it, this is the message I got.

```
The following packages have unmet dependencies:

firefox: Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
```How do I fix it? :(

I am using Unity 2
Just install the repositories through synaptic

---

### Post by DayLite on 2011-06-24
> **jtarin said:**
> Try these inthis order.
```
apt-get -f install
apt-get clean all

```
Still cannot do :(

```
joan@joan-laptop:~$ sudo apt-get -f install
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up opera (11.11.2109) ...
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 35, in <module>
    from softwarecenter.db.update import rebuild_database
  File "/usr/share/software-center/softwarecenter/db/update.py", line 70, in <module>
    cataloged_times = cPickle.load(open(CF))
cPickle.UnpicklingError: unpickling stack underflow
dpkg: error processing opera (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 opera
E: Sub-process /usr/bin/dpkg returned an error code (1)
joan@joan-laptop:~$ sudo apt-get clean all
 
```

Opera works fine.  Why is this an issue?

---

### Post by jtarin on 2011-06-24
First backup your firefox profile.

```
dpkg --purge mozilla-firefox
```

---

### Post by jtarin on 2011-06-24
> **DayLite said:**
> 
Opera works fine.  Why is this an issue?One issue at a time.:p

---

### Post by DayLite on 2011-06-24
> **jtarin said:**
> dpkg --purge mozilla-firefox

Now what?????
```
joan@joan-laptop:~$ dpkg --purge mozilla-firefox
dpkg: error: requested operation requires superuser privilege
joan@joan-laptop:~$ sudo dpkg --purge mozilla-firefox
dpkg: warning: there's no installed package matching mozilla-firefox
joan@joan-laptop:~$ 
 
```

---

### Post by jtarin on 2011-06-24
```
sudo gedit /etc/apt/sources.list

```
be sure to only have natty repo enabled

```
sudo rm /var/cache/apt/archives*
```

then run update again

---

### Post by DayLite on 2011-06-24
> **jtarin said:**
> ```
sudo gedit /etc/apt/sources.list

```
be sure to only have natty repo enabled

```
sudo rm /var/cache/apt/archives*
```

then run update again

That didn't do anything but open up a text editor.

---

### Post by jtarin on 2011-06-24
> **DayLite said:**
> That didn't do anything but open up a text editor.
Yes and you should visibly check that you have the Natty repos available before continuing. Just copy and paste that file and I will look.
Did you by any chance run ```
sudo rm /var/cache/apt/archives/*
```

---

### Post by DayLite on 2011-06-24
[QUOTE=jtarin;10978102]Yes and you should visibly check that you have the Natty repos available before continuing. Just copy and paste that file and I will look.
Did you by any chance run ```
sudo rm /var/cache/apt/archives*
```[/Q

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Beta i386 (20110417)]/ natty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository

# deb [http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu](http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu) natty main
# deb-src [http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu](http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu) natty main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main

---

### Post by DayLite on 2011-06-24
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Beta i386 (20110417)]/ natty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.hmc.edu/ubuntu/ natty main universe restricted multiverse
deb-src http://mirror.hmc.edu/ubuntu/ natty universe main multiverse restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

deb http://mirror.hmc.edu/ubuntu/ natty-security main universe restricted multiverse
deb-src http://mirror.hmc.edu/ubuntu/ natty-security main universe restricted multiverse #Added by software-properties
deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository

deb http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu natty main
deb-src http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu natty main
deb http://mirror.hmc.edu/ubuntu/ natty-updates main universe restricted multiverse
deb-src http://mirror.hmc.edu/ubuntu/ natty-updates main universe restricted multiverse #Added by software-properties 
```

---

### Post by jtarin on 2011-06-24
Sorry....I missed a forward slash

clean the cache:

```
sudo rm /var/cache/apt/archives/*
```

---

### Post by HeadHunter00 on 2011-06-24
> **DayLite said:**
> Firefox would not return to previous site, so I uninstalled it. Then when I wanted to re-install it, this is the message I got.

```
The following packages have unmet dependencies:

firefox: Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
```How do I fix it? :(

I am using Unity 2
try typing in this command:
```
sudo apt-get update && sudo apt-get install libgcc1=1:4.5.2-8ubuntu4 zlib1g=1:1.2.3.4.dfsg-3ubuntu3
```
if you get any errors, post them, if not, then you should be able to install firefox now.

---

### Post by DayLite on 2011-06-25
> **HeadHunter00 said:**
> try typing in this command:
```
sudo apt-get update && sudo apt-get install libgcc1=1:4.5.2-8ubuntu4 zlib1g=1:1.2.3.4.dfsg-3ubuntu3
```
if you get any errors, post them, if not, then you should be able to install firefox now.

This is how the terminal responded:
```
joan@joan-laptop:~$ sudo apt-get update && sudo apt-get install libgcc1=1:4.5.2-8ubuntu4 zlib1g=1:1.2.3.4.dfsg-3ubuntu3
[sudo] password for joan: 
Ign http://mirror.hmc.edu natty InRelease
Ign http://mirror.hmc.edu natty-security InRelease                             
Ign http://mirror.hmc.edu natty-updates InRelease                              
Hit http://mirror.hmc.edu natty Release.gpg                                    
Ign http://archive.canonical.com natty InRelease                               
Hit http://mirror.hmc.edu natty-security Release.gpg                           
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://mirror.hmc.edu natty-updates Release.gpg                            
Ign http://extras.ubuntu.com natty InRelease                                   
Hit http://mirror.hmc.edu natty Release                                        
Hit http://mirror.hmc.edu natty-security Release                               
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://mirror.hmc.edu natty-updates Release                                
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.canonical.com natty Release                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com natty Release                                     
Hit http://packages.medibuntu.org natty InRelease                              
Hit http://mirror.hmc.edu natty/universe Sources                               
Hit http://mirror.hmc.edu natty/main Sources                                   
Hit http://mirror.hmc.edu natty/multiverse Sources                             
Hit http://mirror.hmc.edu natty/restricted Sources                             
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://mirror.hmc.edu natty/main i386 Packages                             
Hit http://mirror.hmc.edu natty/universe i386 Packages                         
Hit http://mirror.hmc.edu natty/restricted i386 Packages                       
Hit http://mirror.hmc.edu natty/multiverse i386 Packages                       
Ign http://mirror.hmc.edu natty/main TranslationIndex                          
Ign http://mirror.hmc.edu natty/multiverse TranslationIndex                    
Ign http://mirror.hmc.edu natty/restricted TranslationIndex                    
Ign http://mirror.hmc.edu natty/universe TranslationIndex                      
Hit http://mirror.hmc.edu natty-security/main Sources                          
Hit http://mirror.hmc.edu natty-security/universe Sources                      
Hit http://mirror.hmc.edu natty-security/restricted Sources                    
Hit http://mirror.hmc.edu natty-security/multiverse Sources                    
Hit http://mirror.hmc.edu natty-security/main i386 Packages                    
Hit http://mirror.hmc.edu natty-security/universe i386 Packages                
Hit http://mirror.hmc.edu natty-security/restricted i386 Packages              
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://mirror.hmc.edu natty-security/multiverse i386 Packages              
Ign http://mirror.hmc.edu natty-security/main TranslationIndex                 
Ign http://mirror.hmc.edu natty-security/multiverse TranslationIndex           
Ign http://mirror.hmc.edu natty-security/restricted TranslationIndex           
Ign http://mirror.hmc.edu natty-security/universe TranslationIndex             
Hit http://mirror.hmc.edu natty-updates/main Sources                           
Hit http://mirror.hmc.edu natty-updates/universe Sources                       
Hit http://mirror.hmc.edu natty-updates/restricted Sources                     
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://mirror.hmc.edu natty-updates/multiverse Sources                     
Hit http://mirror.hmc.edu natty-updates/main i386 Packages                     
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://mirror.hmc.edu natty-updates/universe i386 Packages                 
Hit http://mirror.hmc.edu natty-updates/restricted i386 Packages               
Hit http://mirror.hmc.edu natty-updates/multiverse i386 Packages               
Ign http://mirror.hmc.edu natty-updates/main TranslationIndex                  
Ign http://mirror.hmc.edu natty-updates/multiverse TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/restricted TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/universe TranslationIndex              
Hit http://ppa.launchpad.net natty Release                                     
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty Release                                     
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://mirror.hmc.edu natty/main Translation-en_US                         
Ign http://mirror.hmc.edu natty/main Translation-en                            
Ign http://mirror.hmc.edu natty/multiverse Translation-en_US                   
Ign http://mirror.hmc.edu natty/multiverse Translation-en                      
Ign http://mirror.hmc.edu natty/restricted Translation-en_US                   
Ign http://mirror.hmc.edu natty/restricted Translation-en                      
Ign http://mirror.hmc.edu natty/universe Translation-en_US                     
Ign http://mirror.hmc.edu natty/universe Translation-en                        
Ign http://mirror.hmc.edu natty-security/main Translation-en_US                
Ign http://mirror.hmc.edu natty-security/main Translation-en                   
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en_US          
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en             
Ign http://mirror.hmc.edu natty-security/restricted Translation-en_US          
Ign http://mirror.hmc.edu natty-security/restricted Translation-en             
Ign http://mirror.hmc.edu natty-security/universe Translation-en_US            
Ign http://mirror.hmc.edu natty-security/universe Translation-en               
Ign http://mirror.hmc.edu natty-updates/main Translation-en_US                 
Ign http://mirror.hmc.edu natty-updates/main Translation-en                    
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en_US           
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en              
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en_US           
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en              
Ign http://mirror.hmc.edu natty-updates/universe Translation-en_US             
Ign http://mirror.hmc.edu natty-updates/universe Translation-en                
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://us.archive.ubuntu.com lucid-backports InRelease                     
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg
Hit http://us.archive.ubuntu.com lucid-backports Release  
Hit http://us.archive.ubuntu.com lucid-backports/main Sources
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com lucid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com lucid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com lucid-backports/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com lucid-backports/main TranslationIndex         
Ign http://us.archive.ubuntu.com lucid-backports/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/universe TranslationIndex
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en
Ign http://packages.medibuntu.org natty/free Translation-en_US
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_US
Ign http://packages.medibuntu.org natty/non-free Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgcc1 is already the newest version.
zlib1g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up opera (11.11.2109) ...
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 35, in <module>
    from softwarecenter.db.update import rebuild_database
  File "/usr/share/software-center/softwarecenter/db/update.py", line 70, in <module>
    cataloged_times = cPickle.load(open(CF))
cPickle.UnpicklingError: unpickling stack underflow
dpkg: error processing opera (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
joan@joan-laptop:~$ 
 
```

Didn't work. I tried ti install Firefox and this is what happened:

The following packages have unmet dependencies:

firefox: Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

---

### Post by DayLite on 2011-06-27
joan@joan-laptop:~$ sudo apt-get install firefox ubufox
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 firefox : Depends: libasound2 (> 1.0.24.1)
E: Broken packages
joan@joan-laptop:~$

---

### Post by HeadHunter00 on 2011-06-27
well, if nothing works, you can just download a tarball of firefox from mozilla's website and use that. also, try upgrading libasound now. sudo apt-get install libasound2=1.0.24.1-0ubuntu5
then try installing firefox.

---

### Post by DayLite on 2011-06-27
> **HeadHunter00 said:**
> well, if nothing works, you can just download a tarball of firefox from mozilla's website and use that. also, try upgrading libasound now. sudo apt-get install libasound2=1.0.24.1-0ubuntu5
then try installing firefox.

I tried to install libasound and this is what occured.

```
joan@joan-laptop:~$  sudo apt-get install libasound2=1.0.24.1-0ubuntu5
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libasound2 : Depends: libpython2.7 (>= 2.7) but it is not going to be installed
E: Broken packages
joan@joan-laptop:~$ 
 
```

---

### Post by DayLite on 2011-06-27
> **HeadHunter00 said:**
> well, if nothing works, you can just download a tarball of firefox from mozilla's website and use that. 

Instruct me, please, how do I proceed:confused: I downloaded the tarball, but I don't know how to install it.  Simple instructions, please.

---

### Post by HeadHunter00 on 2011-06-27
you download it, extract it, and the folder that you extracted, inside it you will find a file named firefox, you run it and bingo.

---

### Post by DayLite on 2011-06-28
> **HeadHunter00 said:**
> you download it, extract it, and the folder that you extracted, inside it you will find a file named firefox, you run it and bingo.

Ok, I can run Firefox, like you instructed but how can I install it? I have to keep on returning to my download folder, opening the Firefox folder, find the one that says 'Firefox' and choose to run it.

I tried to drag the icon to the launcher in Unity 2 but it won't go there.

Thanks for your help.

---

