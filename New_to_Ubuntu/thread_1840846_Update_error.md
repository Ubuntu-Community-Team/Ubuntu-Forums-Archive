---
title: "Update error"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by cstambaugh on 2011-09-08
Hello, I am A new to Ubuntu user, only a few months but have made the switch on one computer completely from Windows, and plan to do the others once I am out of school. (they use a program unsupported by wine so I have to stay right now ). I am using Ubuntu 10 and am having an issue and wanted to see if I could get some help. I have searched a few forums, and have tried a few things, and no help. 
I have an error I am getting trying to do updates, and Im not sure why. This is the message on the error as copied and pasted:


Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34). - connect (110: Connection timed out)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org:http:
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org:http:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://ppa.launchpad.net/mcenery/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mcenery/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Unable to connect to packages.freecontrib.org:http:
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Unable to connect to packages.freecontrib.org:http:
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Unable to connect to packages.freecontrib.org:http:
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Unable to connect to packages.freecontrib.org:http:
Some index files failed to download, they have been ignored, or old ones used instead.



My computer is connected to the internet, because im using it now. I am pretty sure I need to add or change repositories, I may be wrong, but I dont know which ones.
Any help would be greatly appreciated.

Thanks, Chris

---

### Post by saltmarshlamb on 2011-09-08
Looks like they are all breezy repos - out of date since 2007. Why are you using them or where did you find them?

---

### Post by Enigmapond on 2011-09-08
+1

Open the terminal and do:

```
cat /etc/apt/sources.list
``` 

and post the output of here between the [code] tags:

---

### Post by cstambaugh on 2011-09-08
Forgive my newbness but I do not know. I am only mainly using wine, Ubuntu tweak, Compiz, and cairo dock. Not sure any thing from breezy here is the code you asked for.

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main universe restricted multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports universe main multiverse restricted
chris@chris-laptop:~$

---

### Post by Enigmapond on 2011-09-08
Ok..then do:

```
sudo gedit /etc/apt/sources.list
```

and either put a # sign in front of everything breezy or just remove the entire lines. Save & exit and try the update again.

---

### Post by ubudog on 2011-09-08
Yep, you've got a bunch of Breezy repos there.  You can easily edit them:  (Ubuntu Software Center>Edit>Software Sources...)  

Or, in 10.04: (System>Administration>Software Sources)

You can easily configure your repos there.  Do you remember adding any repos recently?

---

### Post by cstambaugh on 2011-09-08
Not that I remember adding... I ran the code and it stopped all the breezy but still doing this:

Failed to fetch [http://ppa.launchpad.net/mcenery/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mcenery/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


I dont remember adding any repos before this started. 

I didnt even know you could add or change repos until I started looking things up, but didnt know how till this post.

What is this repo for?

---

### Post by ajgreeny on 2011-09-08
This is very odd, but easily put right.

Go to [Sources List Generator]("http://repogen.simplylinux.ch/") and run the online tick-box questionaire to make a new sources.list file then open up your current one with ```
gksudo gedit /etc/apt/sources.list
``` and delete everything in it and add the new text produced by this site, then save the file and run ```
sudo apt-get update
```

---

### Post by cstambaugh on 2011-09-08
I did that , now firefox will not work, or install, says it has broken packages?

---

### Post by ubudog on 2011-09-08
> **cstambaugh said:**
> I did that , now firefox will not work, or install, says it has broken packages?

Can you do a:
```
sudo apt-get update
```

And post the output?

---

### Post by cstambaugh on 2011-09-08
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Get:2 [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg [197B]                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/contrib Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) lucid/main Translation-en_US
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Ign [http://ppa.launchpad.net/norsetto/ppa/ubuntu/](http://ppa.launchpad.net/norsetto/ppa/ubuntu/) lucid/main Translation-en_US 
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ubuntu/](http://ppa.launchpad.net/tualatrix/ubuntu/) lucid/main Translation-en_US    
Get:5 [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release [5,447B]                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/) oneiric/main Translation-en_US
Ign [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu/](http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/contrib Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/mcenery/ppa/ubuntu/](http://ppa.launchpad.net/mcenery/ppa/ubuntu/) lucid/main Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/) lucid/main Translation-en_US
Get:7 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/gnome-terminal/ubuntu/](http://ppa.launchpad.net/tualatrix/gnome-terminal/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/) oneiric/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing/non-free Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/](http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/) lucid/main Translation-en_US
Get:8 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Get:9 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Get:10 [http://dl.google.com](http://dl.google.com) testing Release [2,513B]                           
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:14 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                            
Get:15 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:16 [http://dl.google.com](http://dl.google.com) testing/non-free Packages [793B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:17 [http://dl.google.com](http://dl.google.com) stable/main Packages [464B]                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources
Fetched 10.4kB in 1s (5,829B/s)
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C41B720D95628707
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: Failed to fetch [http://ppa.launchpad.net/mcenery/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mcenery/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
chris@chris-laptop:~$ 


I found something installed on my computer that was called nightly? it says it is firefox related and am using it now, looks identical to firefox, so im guessing some change I did changed this as well

---

### Post by ajgreeny on 2011-09-08
My goodness, you must have asked for just about every repository available on the sources-list-generator site, looking at that list of errors.

I would suggest you open up **system->administration->software-sources** and uncheck all the source repos, and at least for now, the ones listed in the "Other Software" tab of that dialog box.  That will trim things down to a more normal vanilla install list.  In the updates tab remove the ticks from the boxes other than **Important security** and **recommended**, then refresh the repos again with ```
sudo apt-get update
```

---

### Post by cstambaugh on 2011-09-08
ok did that and it is much better. I only checked the programs that were installed on my system on the source page. Thanks for the help. no more error as of now!! YAY

---

### Post by ajgreeny on 2011-09-08
Great!

Now if you want to, add back in the **medibuntu** repos on the "Other software" tab of the software sources dialog.  It is incredibly useful to enable that for many multimedia applications that you may find you would like.

---

### Post by wildmanne39 on 2011-09-08
> **ajgreeny said:**
> This is very odd, but easily put right.

Go to [Sources List Generator]("http://repogen.simplylinux.ch/") and run the online tick-box questionaire to make a new sources.list file then open up your current one with ```
gksudo gedit /etc/apt/sources.list
``` and delete everything in it and add the new text produced by this site, then save the file and run ```
sudo apt-get update
```
Hi ajgreeny, that is a great link, thank you for posting it.

---

### Post by cstambaugh on 2011-09-08
I dont have an medibuntu repo... how do I add?

I have compiz is there any other eye candy programs that are cool? Any other software reccommended? Thanks for your help today. Have another thread trying to hook up IPOD and not getting very far on that 1 Do you know anything about that?

---

### Post by ubudog on 2011-09-08
> **cstambaugh said:**
> I dont have an medibuntu repo... how do I add?

I have compiz is there any other eye candy programs that are cool? Any other software reccommended? Thanks for your help today. Have another thread trying to hook up IPOD and not getting very far on that 1 Do you know anything about that?

See [this]("http://medibuntu.org/repository.php") for information on how to add the Medibuntu repository.  

Not that I know of, Compiz is pretty cool.  I recommend that you install ccsm, to manage Compiz.  You can do stuff like desktop cube, etc.  That can be achieved like so:
```
sudo apt-get install compizconfig-settings-manager
```

Can you post the thread?  :-)

---

### Post by wildmanne39 on 2011-09-08
Hi, yes there is plenty of eye candy, you can click on how to set up the cube and effects in 11.04, and it will give you directions how to add eye candy as you call it.

Are you using 11.04?

I can not help with IPOD and I only use compiz with many effects like the cube, burn, airplane and many more effects. 

But 11.04 is touchy so if you are using it use my guide and you should be ok.
Thank you

---

### Post by cstambaugh on 2011-09-08
I have CCSM, all the cube effects and all, this is one of the main features I LOVE on Ubuntu, and also it does not use as much resources as windows 7 does. 
here is the URL for the post on thr IPOD. I have extra screensavers also installed I was looking for a live wallpaper, maybe aliens or a customizable matrix code. And stumbled on a few cool screensavers. But nothing that jumps out like CCSM stuff does.

[http://ubuntuforums.org/showthread.php?t=1840893](http://ubuntuforums.org/showthread.php?t=1840893)

---

### Post by wildmanne39 on 2011-09-08
Hi, it sounds like you are about set then, just remember to be careful changing settings in compiz so you do not break unity.
Here are some links, you  might find something you like.
[http://www.wallpaperstop.com/3d-wallpaper/fantasy-wallpaper/3d-wallpaper-download-1005023.html](http://www.wallpaperstop.com/3d-wallpaper/fantasy-wallpaper/3d-wallpaper-download-1005023.html)
Here are links for live wall paper.
[http://compixels.com/7731/ubuntu-wallpaper-pack-that-automatically-changes-with-time-of-day](http://compixels.com/7731/ubuntu-wallpaper-pack-that-automatically-changes-with-time-of-day)
Thank you

---

### Post by ubudog on 2011-09-08
> **wildmanne39 said:**
> Hi, it sounds like you are about set then, just remember to be careful changing settings in compiz so you do not break unity.
Here are some links, you  might find something you like.
[http://www.wallpaperstop.com/3d-wallpaper/fantasy-wallpaper/3d-wallpaper-download-1005023.html](http://www.wallpaperstop.com/3d-wallpaper/fantasy-wallpaper/3d-wallpaper-download-1005023.html)
Here are links for live wall paper.
[http://compixels.com/7731/ubuntu-wallpaper-pack-that-automatically-changes-with-time-of-day](http://compixels.com/7731/ubuntu-wallpaper-pack-that-automatically-changes-with-time-of-day)
Thank you

+1 

Nice links!

---

### Post by wildmanne39 on 2011-09-08
Hi ubudog, thank you.

---

