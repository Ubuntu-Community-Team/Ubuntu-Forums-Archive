---
title: "Having Trouble Installing ubuntu-restricted-extras"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by Ujomin on 2011-06-09
I've been trying various methods in an attempt to install ubuntu-restricted-extras for a friend for several hours now. No matter what I try, I always get the same result though.

I've tried updating my /etc/apt/sources.list file to reflect the following:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
```I've also used
```
sudo apt-get update && sudo apt-get upgrade
```followed by
```
sudo apt-get install ubuntu-restricted-extras
```No matter what combination of the following I use, I always receive this output from the terminal:
```
$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras
$
```Any help would be appreciated, as I'm trying to get my friend's laptop back to her as soon as possible.

Thanks,
Ujomin

---

### Post by Toz on 2011-06-09
Do you get any error messages when you run: ```
sudo apt-get update
```

What says: ```
apt-cache policy ubuntu-restricted-extras
```

---

### Post by Ujomin on 2011-06-09
This is my output from
```
sudo apt-get update
```
```
Ign http://archive.canonical.com natty InRelease
Ign http://extras.ubuntu.com natty InRelease                        
Ign http://us.archive.ubuntu.com natty InRelease                     
Ign http://us.archive.ubuntu.com natty-updates InRelease             
Ign http://us.archive.ubuntu.com natty-backports InRelease           
Ign http://security.ubuntu.com natty-security InRelease              
Hit http://archive.canonical.com natty Release.gpg                   
Hit http://extras.ubuntu.com natty Release.gpg                       
Hit http://us.archive.ubuntu.com natty Release.gpg                   
Hit http://security.ubuntu.com natty-security Release.gpg                                  
Hit http://archive.canonical.com natty Release                                             
Hit http://extras.ubuntu.com natty Release                           
Hit http://us.archive.ubuntu.com natty-updates Release.gpg            
Hit http://security.ubuntu.com natty-security Release                                      
Hit http://archive.canonical.com natty/partner Sources                                      
Hit http://extras.ubuntu.com natty/main Sources                      
Hit http://us.archive.ubuntu.com natty-backports Release.gpg         
Hit http://security.ubuntu.com natty-security/restricted Sources                           
Hit http://archive.canonical.com natty/partner i386 Packages                               
Ign http://archive.canonical.com natty/partner TranslationIndex                            
Hit http://extras.ubuntu.com natty/main i386 Packages                                      
Ign http://extras.ubuntu.com natty/main TranslationIndex             
Hit http://us.archive.ubuntu.com natty Release                       
Hit http://security.ubuntu.com natty-security/main Sources                                                        
Hit http://security.ubuntu.com natty-security/multiverse Sources                           
Hit http://security.ubuntu.com natty-security/universe Sources       
Hit http://security.ubuntu.com natty-security/main i386 Packages     
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates Release               
Hit http://security.ubuntu.com natty-security/universe i386 Packages                                              
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages                     
Ign http://security.ubuntu.com natty-security/main TranslationIndex                        
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex                  
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                    
Hit http://us.archive.ubuntu.com natty-backports Release                                   
Hit http://us.archive.ubuntu.com natty/restricted Sources                                                         
Hit http://us.archive.ubuntu.com natty/main Sources                                                               
Hit http://us.archive.ubuntu.com natty/multiverse Sources                                                         
Hit http://us.archive.ubuntu.com natty/universe Sources                                     
Hit http://us.archive.ubuntu.com natty/main i386 Packages                                                         
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                            
Hit http://us.archive.ubuntu.com natty/universe i386 Packages        
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com natty/main TranslationIndex         
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources                          
Hit http://us.archive.ubuntu.com natty-updates/main Sources                                
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources    
Hit http://us.archive.ubuntu.com natty-updates/universe Sources      
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages    
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-backports/main Sources                              
Hit http://us.archive.ubuntu.com natty-backports/restricted Sources                        
Hit http://us.archive.ubuntu.com natty-backports/universe Sources    
Hit http://us.archive.ubuntu.com natty-backports/multiverse Sources  
Hit http://us.archive.ubuntu.com natty-backports/main i386 Packages  
Hit http://us.archive.ubuntu.com natty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-backports/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-backports/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-backports/multiverse TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en_US     
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Ign http://us.archive.ubuntu.com natty-backports/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-backports/universe TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en        
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://security.ubuntu.com natty-security/main Translation-en_US 
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://us.archive.ubuntu.com natty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-backports/main Translation-en
Ign http://us.archive.ubuntu.com natty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-backports/universe Translation-en
Reading package lists... Done
```

As far as I can tell, there are no errors that occur.

As for the
```
apt-cache policy ubuntu-restricted-extras
```
command, this is my output:
```
N: Unable to locate package ubuntu-restricted-extras
```

---

### Post by dFlyer on 2011-06-09
Have you tried using synaptic and filter on ubuntu-restricted-extras? Make sure you have the multiverse archive enabled.

---

### Post by Toz on 2011-06-09
I get:> $ apt-cache policy ubuntu-restricted-extras 
ubuntu-restricted-extras:
  Installed: (none)
  Candidate: 43
  Version table:
     43 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/multiverse i386 Packages


and you have that repository in your sources.list file. *scratches head*

What do you have in your /etc/apt/sources.list.d directory?

---

### Post by Ujomin on 2011-06-09
> **dFlyer said:**
> Have you tried using synaptic and filter on ubuntu-restricted-extras? Make sure you have the multiverse archive enabled.
I've tried that as well, thanks for the tip though.

> **Toz said:**
> What do you have in your /etc/apt/sources.list.d directory?
I have nothing in that folder (including hidden files). Should there be something there?

---

### Post by Toz on 2011-06-09
Just checking.

Try another mirror?
```
sudo software-properties-gtk
```and check the "Download From" selection.

---

