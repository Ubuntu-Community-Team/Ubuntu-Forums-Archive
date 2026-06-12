---
title: "help bugs in my clean install of ubuntu 9.1"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by madmax49er on 2009-11-15
help i am a pc tech that is adverse with hardware mainly not applications side of things!

i just installed the latest update of ubuntu on my computer while ending the set up told me it had problems i just hoped it would at least boot properly and sucess with that yay!

i am trying to install wine and it tells me to fix problems first!

it has been over 20 yrs since i worked with programming etc.

i do not know how to fix it i need someone who is willing to guide me and be patient with me so it could be addressed and solved for me please please please with a karmic koala on top please lol hehehe.

the email address i used for this forum will be responded to on my windows based computer.

thank you to whomever may help and i have noticed u have no teams down here in australasia region or new zealand for that matter not that i am worried.

patiently await a response from someone able to help!

cheers

 madmax49er

---

### Post by grandtoubab on 2009-11-15
[I]"I am trying to install wine and it tells me to fix problems first!"

tell us wich one at least:lolflag:

[/I]first check your packages.in a terminal window to see the errors

check your list
     ```
sudo apt-get update 
```

upgrade your packages
     ```
sudo apt-get upgrade 
```

verify you do not miss new packages
     ```
sudo apt-get dist-upgrade
```

---

### Post by mikewhatever on 2009-11-15
Please post the exact error message you are seeing, cause otherwise people have no clue what kind of programming you are talking about.;)

---

### Post by madmax49er on 2009-11-15
sudo apt-get update

this is the result i got with that first suggestion

  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/restricted Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/universe Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates Release.gpg
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/main Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/restricted Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/universe Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/multiverse Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports Release.gpg       
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports/main Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports/restricted Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports/universe Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports/multiverse Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-proposed Release.gpg        
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-proposed/restricted Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-proposed/main Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-proposed/universe Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Reading package lists... Done
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

am trying the next part now

---

### Post by madmax49er on 2009-11-15
this was the second one u suggested

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

trying the third one now

---

### Post by madmax49er on 2009-11-15
this was the third suggestion

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

ok so now what?

---

### Post by sandyd on 2009-11-15
> **madmax49er said:**
> sudo apt-get update

this is the result i got with that first suggestion

  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main Translation-en_AU
  <snip>

W: Some index files failed to download, they have been ignored, or old ones used instead.

am trying the next part now
do this.

create a new text file on your desktop called sources.list
paste this into the file
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some appligbtions which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from gbnonigbl's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by gbnonigbl and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner
deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe                                                             
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse   

```add this to the bottom of the file, (optional)
```

##KDE3##
# deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu jaunty main 
# deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu jaunty main
# deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main

##VirtualBox##
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

##KDE Backports##
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main

##Google Chrome##
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

##WINE (Devel)##
deb http://wine.budgetdedicated.com/apt karmic main

##Cairo Dock##
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/neversfelde/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/neversfelde/ppa/ubuntu karmic main 

##Kmess##
deb http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu karmic main
deb-src http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu karmic main

##Mozilla-Daily Builds##
# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main\

##Giftwrap##
deb http://ppa.launchpad.net/giftwrap/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/giftwrap/ppa/ubuntu karmic main

##Songbird##
deb http://ppa.launchpad.net/songbird-daily/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/songbird-daily/ppa/ubuntu karmic main

##ToR##
deb http://deb.torproject.org/torproject.org jaunty main
deb http://apt.dolphinaura.studenthotspot.net/ jaunty main

##Personal PPA##
# deb http://ppa.launchpad.net/dolphinaura/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/dolphinaura/ppa/ubuntu karmic main

##WinFF##
deb http://winff.org/ubuntu jaunty universe

##Virtualbox##
deb http://download.virtualbox.org/virtualbox/debian karmic non-free


```save it, open a terminal and run this
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo mv ~/Desktop/sources.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get install wine wine-gecko cabextract
cd /usr/bin
sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks
winetricks allfonts fontfix fontsmooth-rgb

```

---

### Post by madmax49er on 2009-11-15
when i try to install wine i get the following error message mike

Could not apply changes!
Fix broken packages first.

dont ask me what packages are broken as it beats the hell out of me!

---

### Post by madmax49er on 2009-11-15
a@a:~$ sudo mv /etc/apt/source.list /etc/apt/source.list.bak
mv: cannot stat `/etc/apt/source.list': No such file or directory
a@a:~$ sudo mv ~/desktop/source.list /etc/apt/source.list
mv: cannot stat `/home/a/desktop/source.list': No such file or directory

this is what happens when i do as u told me

---

### Post by madmax49er on 2009-11-15
[/code]save it, open a terminal and run this
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo mv ~/Desktop/sources.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get install wine wine-gecko cabextract
cd /usr/bin
sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks
winetricks allfonts fontfix fontsmooth-rgb

```[/quote]

i got as far as sudo apt-get update

this is as far it it got with that

a@a:~$ sudo apt-get update
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release.gpg [197B]                 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/non-free Translation-en_AU           
Get:2 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg [197B]                 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_AU           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_AU                    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_AU              
Get:3 [http://apt.dolphinaura.studenthotspot.net](http://apt.dolphinaura.studenthotspot.net) jaunty Release.gpg [197B]      
Ign [http://apt.dolphinaura.studenthotspot.net](http://apt.dolphinaura.studenthotspot.net) jaunty/main Translation-en_AU    
Get:4 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release [3,454B]                   
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg [189B]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_AU              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_AU              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_AU                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_AU              
Ign [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release                              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg [189B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_AU            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_AU      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_AU        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_AU      
Get:7 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release [3,454B]                   
Get:8 [http://apt.dolphinaura.studenthotspot.net](http://apt.dolphinaura.studenthotspot.net) jaunty Release [4,569B]        
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_AU                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Get:10 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/non-free Packages [1,507B]        
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release.gpg [189B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Translation-en_AU          
Get:12 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release [1,019B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Translation-en_AU    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Translation-en_AU      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Translation-en_AU    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg [189B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_AU           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                             
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Get:18 [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages [1,264B]        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_AU     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_AU       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_AU     
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release [44.1kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Ign [http://apt.dolphinaura.studenthotspot.net](http://apt.dolphinaura.studenthotspot.net) jaunty Release                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Ign [http://apt.dolphinaura.studenthotspot.net](http://apt.dolphinaura.studenthotspot.net) jaunty/main Packages             
Get:23 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages [1,276B]           
Get:24 [http://winff.org](http://winff.org) jaunty Release.gpg [197B]                              
Ign [http://winff.org](http://winff.org) jaunty/universe Translation-en_AU                         
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release [41.7kB]             
Ign [http://apt.dolphinaura.studenthotspot.net](http://apt.dolphinaura.studenthotspot.net) jaunty/main Packages             
Get:26 [http://apt.dolphinaura.studenthotspot.net](http://apt.dolphinaura.studenthotspot.net) jaunty/main Packages [752B]   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release [37.1kB]              
Get:28 [http://winff.org](http://winff.org) jaunty Release [2,037B]                                
Ign [http://winff.org](http://winff.org) jaunty Release                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                              
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources [116kB]             
Get:30 [http://winff.org](http://winff.org) jaunty/universe Packages [940B]                        
Get:31 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources [2,795kB]             
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Get:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Get:35 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Get:36 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [65.9kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Get:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages [73.3kB]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources [14.2kB]                   
Get:40 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [3,291B]                  
Get:41 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources [1,500B]                   
Get:42 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [2,502B]                  
Get:43 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [2,240B]                  
Get:44 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources [1,042B]                   
Get:45 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [14B]                     
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources [14B]                      
Get:47 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [1,944B]                  
Get:48 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources [686B]                     
Get:49 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [1,150B]                  
Get:50 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources [689B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5,133kB]            
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages [190kB]            
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages [61.7kB]         
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages [14B]      
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources [14B]       
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources [21.8kB]          
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources [655B]      
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources [8,266B]      
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages [31.8kB]     
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages [14B]      
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages [14B]          
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages [14B]    
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages [14B]      
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages [14B]    
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Sources [14B]           
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Sources [14B]     
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Sources [14B]       
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Sources [14B]     
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages [14.2kB]        
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages [14B]     
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources [14B]      
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources [4,677B]         
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources [14B]      
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources [793B]       
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages [5,835B]    
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages [14B]     
Err [http://deb.torproject.org](http://deb.torproject.org) jaunty Release.gpg                               
  Cannot initiate the connection to deb.torproject.org:80 (2001:4dd0:1234:1::deb). - connect (101: Network is unreachable) [IP: 2001:4dd0:1234:1::deb 80]
Err [http://deb.torproject.org](http://deb.torproject.org) jaunty/main Translation-en_AU
  Cannot initiate the connection to deb.torproject.org:80 (2001:4dd0:1234:1::deb). - connect (101: Network is unreachable) [IP: 2001:4dd0:1234:1::deb 80]
Fetched 9,104kB in 2min 0s (75.5kB/s)               
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://apt.dolphinaura.studenthotspot.net](http://apt.dolphinaura.studenthotspot.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 839A267844F9E03A
W: GPG error: [http://winff.org](http://winff.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1CD52D7BAAFE086A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7274A4DAE80D6BF5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5646F8B10331274D
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A193607A1D2EC123
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7CA7665B207CAD03
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D725E4885719E347
W: Failed to fetch [http://deb.torproject.org/torproject.org/dists/jaunty/Release.gpg](http://deb.torproject.org/torproject.org/dists/jaunty/Release.gpg)  Cannot initiate the connection to deb.torproject.org:80 (2001:4dd0:1234:1::deb). - connect (101: Network is unreachable) [IP: 2001:4dd0:1234:1::deb 80]

W: Failed to fetch [http://deb.torproject.org/torproject.org/dists/jaunty/main/i18n/Translation-en_AU.bz2](http://deb.torproject.org/torproject.org/dists/jaunty/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to deb.torproject.org:80 (2001:4dd0:1234:1::deb). - connect (101: Network is unreachable) [IP: 2001:4dd0:1234:1::deb 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by madmax49er on 2009-11-15
thanks to carlee help wine is installed and running even though i am getting errors with i just perservered and got there in the end to the moderators u may close this tyhread now thnx to all that responded and helped me with thanks!

word of advice to non-australian: the koala bear is not cute and cuddly as it appears due to its living it life in trees its claws are Extremely sharp and have been known to slice a person's hand off at the wrist for example. what u see in zoo's are tame koala bears with all wild animals they can turn at anytime for no reason at all wild animals tame or not should always be aware they may cause serious injury even from unprovoked attacks all animals retain the naturally wild tendacies.

---

### Post by grandtoubab on 2009-11-16
Err [http://deb.torproject.org]("http://deb.torproject.org/")  jaunty Release.gpg                               
  Cannot initiate the connection to deb.torproject.org:80  (2001:4dd0:1234:1::deb). - connect (101: Network is unreachable) [IP:  2001:4dd0:1234:1::deb 80]

@[carlee]("http://ubuntuforums.org/member.php?u=717412")

Why do you want making him mixe Karmic and Jaunty sources???

---

