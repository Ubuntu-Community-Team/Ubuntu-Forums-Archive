---
title: "E:Malformed line 34 in source list /etc/apt/sources.list (dist parse), E:The list of"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by flavs2001 on 2010-06-06
Am beginner in Ubuntu and have a problem with the next error:

E:Malformed line 34 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read

I can`t install o uninstall any software or do updates.

Can somebody  help me please.

I have an aspire one netbook with windows Xp and a Wubi installation.

Thanks


Flavio

---

### Post by halitech on 2010-06-06
can you post the output of
```
cat /etc/apt/sources.list
```
so we can see what line 34 is

---

### Post by flavs2001 on 2010-06-06
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty restricted main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras # disabled on upgrade to karmic

---

### Post by halitech on 2010-06-06
somethings not right there, you only have 13 lines there. run
```
sudo apt-get update
```
and post the output

---

### Post by flavs2001 on 2010-06-06
this is  happens

E: Malformed line 34 in source list /etc/apt/sources.list (dist parse)

---

### Post by halitech on 2010-06-06
there is nothing more to the error then what you are giving us?

open the file in gedit and post it from there
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by flavs2001 on 2010-06-06
OK this is result

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty restricted main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras # disabled on upgrade to karmic

---

### Post by wojox on 2010-06-06
How many repo's are enabled? What's 

```
ls -l /etc/apt/sources.list.d
```

---

### Post by DougieFresh4U on 2010-06-06
This may not sound correct, but I would replace sources list. I do not like the looks of your list as it seems something is missing. I am not sure where it is, but there is some where to generate new sources list.
Maybe some one will chime in with link to it :)
Good luck, all is not lost yet.

---

### Post by flavs2001 on 2010-06-06
total 20
-rw-r--r-- 1 root root 93 2010-06-06 16:50 bisigi.list
-rw-r--r-- 1 root root 59 2009-10-31 16:30 bisigi.list.distUpgrade
-rw-r--r-- 1 root root 93 2010-06-06 16:50 bisigi.list.save
-rw-r--r-- 1 root root 48 2010-06-06 16:50 google-chrome.list
-rw-r--r-- 1 root root 48 2010-06-06 16:50 google-chrome.list.save

---

### Post by wojox on 2010-06-06
> **flavs2001 said:**
> total 20
-rw-r--r-- 1 root root 93 2010-06-06 16:50 bisigi.list
-rw-r--r-- 1 root root 59 2009-10-31 16:30 bisigi.list.distUpgrade
-rw-r--r-- 1 root root 93 2010-06-06 16:50 bisigi.list.save
-rw-r--r-- 1 root root 48 2010-06-06 16:50 google-chrome.list
-rw-r--r-- 1 root root 48 2010-06-06 16:50 google-chrome.list.save

This should be where it's coming from. Open System > Admin > Sources List > Other Software.

Untick bisigi and google-chrome.

Close and again run 

```
sudo apt-get update
```

---

### Post by marcoftheknight on 2010-06-06
I would go to your synaptic package manager change all the setting to defaul or make sure they are set correctly then make sure your

uder system administration--> package sources everything looks ok there no weird things youve done.

just do a little browing enable stuff (lol)
then sudo apt-get update (or what ever the comman is)

SHoudl look like this:

Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done

---

### Post by flavs2001 on 2010-06-06
din`t see that

---

### Post by flavs2001 on 2010-06-06
the list show only 9 lines but not taht

---

### Post by wojox on 2010-06-06
> **flavs2001 said:**
> the list show only 9 lines but not taht

What does it show? take a screen shot or something. :)

---

### Post by k3lt01 on 2010-06-07
> **wojox said:**
> What does it show? take a screen shot or something. :)Take a look at post number 3 and post number 7 that will save the OP from taking a screenshot.

@OP. THis is what your /etc/apt/sources.list should look like

```
#

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ lucid universe
deb http://au.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://au.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
```

My advice to you would be to copy this to a text (gedit) file and modify it to suit the distribution you are using (Karmic, Intrepid, Hardy, Lucid), and the country you are in. Then copy the nw file to your /etc/apt/sources.list file. Also it is not good practice to mix distribution repositories like it appears you have in the list you have put up for us to check. Doing that can cause clashes and breakages with applications.

Let us know how you go.

---

