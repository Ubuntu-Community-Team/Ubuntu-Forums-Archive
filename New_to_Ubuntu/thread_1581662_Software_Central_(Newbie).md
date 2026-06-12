---
title: "Software Central (Newbie)"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by 420 on 2010-09-25
Heya,

Every time I try installing something from Software Central I get an error.
For instance I tried installing Sysinfo this morning and got the error:


> **Requires installation of untrusted packages**

The action would require the installation
of packages from unauthenticated
sources.

v Details
SysinfoSame error for everything I try to install. What have I done wrong and how do I fix it? :-?

---

### Post by mörgæs on 2010-09-25
If you reboot the machine, can you install from Synaptic?

---

### Post by sandyd on 2010-09-25
> **420 said:**
> Heya,

Every time I try installing something from Software Central I get an error.
For instance I tried installing Sysinfo this morning and got the error:


Same error for everything I try to install. What have I done wrong and how do I fix it? :-?
post output of
```

cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by 420 on 2010-09-25
Yes, I can install from Synaptic.

---

### Post by 420 on 2010-09-25
> **sandyd said:**
> post output of
```

cat /etc/apt/sources.list
sudo apt-get update
```
```
420@420-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
420@420-desktop:~$ sudo apt-get update
[sudo] password for 420: 
Get: 1 http://security.ubuntu.com lucid-security Release.gpg [198B]            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB   
Get: 2 http://archive.canonical.com lucid Release.gpg [198B]                   
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB       
Get: 3 http://archive.ubuntu.com lucid Release.gpg [189B]                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Hit http://archive.canonical.com lucid Release                 
Hit http://archive.ubuntu.com lucid Release                                    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://archive.ubuntu.com lucid/main Sources                     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Get: 4 http://security.ubuntu.com lucid-security Release [38.5kB]    
Get: 5 http://gb.archive.ubuntu.com lucid Release.gpg [189B]                   
Get: 6 http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB [62.9kB]
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://archive.ubuntu.com lucid/restricted Sources                         
Get: 7 http://security.ubuntu.com lucid-security/main Packages [82.6kB]        
Get: 8 http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB [2,332B]
Get: 9 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB [33.9kB]
Get: 10 http://security.ubuntu.com lucid-security/restricted Packages [14B]    
Get: 11 http://security.ubuntu.com lucid-security/restricted Sources [14B]     
Get: 12 http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [37.7kB]
Get: 13 http://security.ubuntu.com lucid-security/main Sources [29.7kB]        
Get: 14 http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [37.7kB]
Get: 15 http://security.ubuntu.com lucid-security/multiverse Sources [656B]    
Get: 16 http://security.ubuntu.com lucid-security/universe Sources [9,810B]    
Hit http://gb.archive.ubuntu.com lucid Release                                 
Get: 17 http://security.ubuntu.com lucid-security/universe Packages [39.8kB]   
Hit http://gb.archive.ubuntu.com lucid/main Packages                           
Hit http://gb.archive.ubuntu.com lucid/restricted Packages                     
Hit http://gb.archive.ubuntu.com lucid/restricted Sources                      
Hit http://gb.archive.ubuntu.com lucid/main Sources                            
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://gb.archive.ubuntu.com lucid/universe Sources                        
Hit http://gb.archive.ubuntu.com lucid/universe Packages                       
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages                     
Get: 18 http://security.ubuntu.com lucid-security/multiverse Packages [1,994B] 
Fetched 318kB in 46s (6,866B/s)                                                
Reading package lists... Done
420@420-desktop:~$ 
```

---

### Post by mörgæs on 2010-09-25
> **420 said:**
> Yes, I can install from Synaptic.

Good, then forget about Software Centre. Synaptic is as solid as it can be, unlike SC.

---

### Post by sandyd on 2010-09-25
> **420 said:**
> ```
420@420-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
420@420-desktop:~$ sudo apt-get update
[sudo] password for 420: 
Get: 1 http://security.ubuntu.com lucid-security Release.gpg [198B]            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB   
Get: 2 http://archive.canonical.com lucid Release.gpg [198B]                   
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB       
Get: 3 http://archive.ubuntu.com lucid Release.gpg [189B]                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Hit http://archive.canonical.com lucid Release                 
Hit http://archive.ubuntu.com lucid Release                                    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://archive.ubuntu.com lucid/main Sources                     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Get: 4 http://security.ubuntu.com lucid-security Release [38.5kB]    
Get: 5 http://gb.archive.ubuntu.com lucid Release.gpg [189B]                   
Get: 6 http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB [62.9kB]
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://archive.ubuntu.com lucid/restricted Sources                         
Get: 7 http://security.ubuntu.com lucid-security/main Packages [82.6kB]        
Get: 8 http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB [2,332B]
Get: 9 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB [33.9kB]
Get: 10 http://security.ubuntu.com lucid-security/restricted Packages [14B]    
Get: 11 http://security.ubuntu.com lucid-security/restricted Sources [14B]     
Get: 12 http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [37.7kB]
Get: 13 http://security.ubuntu.com lucid-security/main Sources [29.7kB]        
Get: 14 http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [37.7kB]
Get: 15 http://security.ubuntu.com lucid-security/multiverse Sources [656B]    
Get: 16 http://security.ubuntu.com lucid-security/universe Sources [9,810B]    
Hit http://gb.archive.ubuntu.com lucid Release                                 
Get: 17 http://security.ubuntu.com lucid-security/universe Packages [39.8kB]   
Hit http://gb.archive.ubuntu.com lucid/main Packages                           
Hit http://gb.archive.ubuntu.com lucid/restricted Packages                     
Hit http://gb.archive.ubuntu.com lucid/restricted Sources                      
Hit http://gb.archive.ubuntu.com lucid/main Sources                            
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://gb.archive.ubuntu.com lucid/universe Sources                        
Hit http://gb.archive.ubuntu.com lucid/universe Packages                       
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages                     
Get: 18 http://security.ubuntu.com lucid-security/multiverse Packages [1,994B] 
Fetched 318kB in 46s (6,866B/s)                                                
Reading package lists... Done
420@420-desktop:~$ 
```
must be a problem with SC, no problems here.

---

### Post by sanderd17 on 2010-09-25
I suppose purging the software center would fix the problem. The only problem with that solution is that when the SC is uninstalled, it takes the ubuntu-desktop package with him. I guess that's not such a good idea.

---

### Post by Elfy on 2010-09-25
Put ubuntu-desktop back then if and when you come to upgrade, I think it will make the upgrade easier - it's only a meta package.

Removing anything that comes with default ubuntu will remove ubuntu-desktop as far as I know - similarly with kubuntu-desktop xubuntu-desktop etc

---

### Post by theozzlives on 2010-09-25
If you're installing 3rd party or "after market" software, you may need the key to verify the software comes from a trusted source.

---

