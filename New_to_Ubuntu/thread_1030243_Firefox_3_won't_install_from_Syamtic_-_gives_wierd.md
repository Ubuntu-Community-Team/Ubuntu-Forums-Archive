---
title: "Firefox 3 won't install from Syamtic - gives wierd error"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by cogvos on 2009-01-04
Could someone show me how to install firefox 3 which synaptic keeps giving the following error?

firefox-3.0:
  Depends: xulrunner-1.9 (>=1.9.0.1) but 1.9~a8-0ubuntu2 is to be installed

I only have the option to download the ubuntu version of xulrunner (whatever *that* is!) so how do I get the one that firefox wants???

I'm running Ubuntu 7.10 with most of the updates, erm updated... (Avant window manager won't for some reason...)

Yours baffled.

John.

---

### Post by Bachstelze on 2009-01-04
Please paste the contents of [font="monospace"]/etc/apt/sources.list[/font].

---

### Post by cogvos on 2009-01-04
Hi, sorry its a bit long...

I guess the comented out bits were as I dod not have broadband at the time of the install and so was not connect to the internet(?)

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted

---

### Post by northern lights on 2009-01-04
*xulrunner* is in the *universe* repository.

The British mirror of these is commented, but the main mirror appears available.

It might generally be a good idea to clear your *sources.list* up a bit.

Should you choose to do so, backup your current file```
sudo cp /etc/apt/source.list /etc/apt/sources.list_bkup
```

Subsequently open the file with gedit as root```
gksu gedit /etc/apt/sources.list
```and replace it with this:```
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```
I've noticed that you have *backports* enabled - this is not very recommendable for the inexperienced user.
You might also want to consider adding the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository, even though this has nothing to do with your FF3/xulrunner issue.

---

### Post by cogvos on 2009-01-04
Hi in Syaptic I am getting Xulrunner. But not the version that Firefox 3 insists it needs, which is I guess where the problem is(?) 

Thing is I can't figure out how to get synaptic to give me the version that Firefox wants - since it only gives one, which is not the one that Firefox wants... Sorry that doesn't make much sense :(

John.

---

### Post by Bachstelze on 2009-01-04
Okay, let's clean it up a bit :

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
 
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner
 
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse

deb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```

Now try again:

```
sudo apt-get update
sudo apt-get install firefox-3.0
```

---

### Post by cogvos on 2009-01-04
??? Sorry Having done this I am still getting the error - tried both versions of the sources list... 

In a terminal it shows...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9.0.1) but 1.9~a8-0ubuntu2 is to be installed
E: Broken packages
:confused:

---

### Post by Bachstelze on 2009-01-04
Do you already have a version of [font="monospace"]xulrunner-1.9[/font] installed? If so, uninstall it beforehand.

---

### Post by cogvos on 2009-01-04
Erm yes (it had a green square and a little star besides it. When I said update I was informed that doing so would break something called Yelp (what's yelp????)

I marked it for removal (xulrunner - not Yelp) and Xulrunner 1.9 was removed.

However...

Trying to install Firefox now gives...

firefox-3.0:
 Depends: xulrunner-1.9 but it is not going to be installed

I thought that synaptic also installed dependences....?

Help?

John.

---

### Post by Bachstelze on 2009-01-04
[http://packages.ubuntu.com/gutsy-updates/yelp](http://packages.ubuntu.com/gutsy-updates/yelp)

And it's weird that you got thins message because apparently, it does not depend on xulrunner-1.9.

First, please close Synaptic and let's work in the terminal, it will let us see more clearly what's going on.

```
sudo apt-get update
sudo apt-get install firefox-3.0
```

What does that give?

---

### Post by cogvos on 2009-01-04
??? wonder if something, other than me) has got confused... Anyway I've closed the gnome synaptic and in a terminal....

sudo apt-get update gives

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/restricted Translation-en_GB
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB                  
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB            
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg [189B]           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB    
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports Release.gpg [189B]         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Translation-en_GB    
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release.gpg                            
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Sources         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Sources   
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages
  404 Not Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Sources  
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Sources
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Fetched 5B in 0s (10B/s) 
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

sudo apt-get install firefox-3.0 gives 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9.0.1) but it is not going to be installed
E: Broken packages

:confused:

---

### Post by Bachstelze on 2009-01-04
So, let's see what happens when you try to install [font="monospace"]xulrunner-1.9[/font].

```
sudo apt-get install xulrunner-1.9
```

(As a side note, why are you still using Gutsy? It might just be easier to upgrade to at least Hardy...)

---

### Post by cogvos on 2009-01-04
OK. This gives

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 99 not upgraded.

I think I understand about the lib not being needed, but why is the installed count 0? Shouldn't it be 1? And why doesn't it say that it's installed xulrunner-1.9?

---

### Post by Bachstelze on 2009-01-04
Because you didn't uninstall the version you have. ;) And since it's already installed, Apt does not install it again. So let's see which version you currently have:

```
dpkg -l | grep xulrunner
```

---

### Post by cogvos on 2009-01-04
That's odd I used the gnome syamptic and marked it for removal and that told me it had removed it (this was when you asked me to do so a while back)

dpkg -l | grep xulrunner gives 

rc  xulrunner-1.9                              1.9~a8-0ubuntu2                      XUL + XPCOM application runner

The version listed is the only one that comes up when I run the gnome synaptic

John.

Oh regarding upgrading, 7.10 is the 1st version of Linux that I have ever got to work on this system without problems with crashes, extending lib<something or other - can't remember what> or me tearing my hair out. I'm thus a little reticent about potentially breaking anything...

---

### Post by Bachstelze on 2009-01-04
Sorry, I missed something there:

> 0 upgraded, 0 newly installed, 0 to remove **and 99 not upgraded**.

What does this tell you?

```
sudo apt-get dist-upgrade
```

---

### Post by cogvos on 2009-01-04
Odd?? I though I had updated everything... anyway this produced a huge list, then end of which is below... Please tell me if you want the full list.


Get: 107 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main python-libxml2 2.6.30.dfsg-2ubuntu1.4 [263kB]
Get: 108 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main ruby1.8 1.8.6.36-1ubuntu3.3 [240kB]
Get: 109 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main tk8.4 8.4.15-1ubuntu1.1 [1003kB]
Get: 110 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main compiz-fusion-plugins-main 0.5.2+git20070928-0ubuntu2.2 [605kB]
Get: 111 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse mencoder 2:1.0~rc2-0ubuntu1~gutsy1 [3680kB]
Get: 112 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse mplayer 2:1.0~rc2-0ubuntu1~gutsy1 [4336kB]
Fetched 250MB in 4m43s (880kB/s)                                               
Failed to fetch [http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/python-libawn-bzr_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/python-libawn-bzr_0.2.0-bzr158-1_i386.deb)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/libawn-bzr_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/libawn-bzr_0.2.0-bzr158-1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


<edit>

sadly

 sudo apt-get install firefox-3.0
still gives ...

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9.0.1) but it is not going to be installed
E: Broken packages

---

### Post by Bachstelze on 2009-01-04
Okay, let's get rid of that repo you have, since it's down. Remove those two lines in your sources.list:

```
deb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```

And then

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by cogvos on 2009-01-04
Aye aye aye!

This updated loads, including the kernal so it's now asking me to reboot. Should I or is there anything else I need to do first?

Do you need to see any of the update output? ( I don't know how to get it back after the reboot.

John.

---

### Post by Bachstelze on 2009-01-04
If it doesn't say packages were removed or kept back, it means all went well so you can reboot, and try to install firefox 3 afterwards.

---

### Post by cogvos on 2009-01-04
OK Done that. The update mucked up grub (setting the root dir to (1,7) instead of (0,6) but I've met that before in a failed attempt to install Suse 9.something so was abe to fix.

Sadly I still cant install firefox :(

john@john-desktop:/$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9.0.1) but it is not going to be installed
E: Broken packages

Is it worth trying to install xulrunner using some kind of force switch?

---

### Post by northern lights on 2009-01-04
You might want to try running```
sudo apt-get --fix-missing install xulrunner-1.9
```or the *--fix-broken* switch (instead of *--fix-missing*) or selecting the "Fix Broken Packages" entry in Synaptic's "Edit" menu.

> **cogvos said:**
> Is it worth trying to install xulrunner using some kind of force switch?
There's no such force switch per se. The closest are the two suggested above.

It could further be that you have the package *xulrunner* installed already (rather than *xulrunner-**1.9***). Can you post the output of```
aptitude search xulrunner
```to verify?

---

### Post by cogvos on 2009-01-04
aptitude search xulrunner
v   liferea-xulrunner               -                                           
p   xulrunner                       - XUL + XPCOM application runner            
c   xulrunner-1.9                   - XUL + XPCOM application runner            
p   xulrunner-1.9-dev               - XUL + XPCOM development files             
p   xulrunner-1.9-dom-inspector     - tool for inspecting the DOM of pages in Mo
p   xulrunner-1.9-gnome-support     - Support for Gnome in xulrunner-1.9 applica
p   xulrunner-1.9-venkman           - Venkman is Mozilla-based JavaScript debugg
p   xulrunner-gnome-support         - Support for Gnome in xulrunner application

:confused:

<edit>

If I look at gnomes synaptic it is not installed. The sqaure is blank not green. If I try and install it says

xulrunner-1.9:
  Breaks: yelp (<2.22.1-0ubuntu2.8.04.1) but 2.20.0-0ubuntu3.1 is to be installed

But from the past posts I have been told that yelp does not use Xulrunner... Argh!

---

### Post by northern lights on 2009-01-04
> **cogvos said:**
> aptitude search xulrunner
v   liferea-xulrunner               -                                           
p   xulrunner                       - XUL + XPCOM application runner            
[COLOR="Red"]**c**   xulrunner-1.9                   - XUL + XPCOM application runner         [/COLOR]   
p   xulrunner-1.9-dev               - XUL + XPCOM development files             
p   xulrunner-1.9-dom-inspector     - tool for inspecting the DOM of pages in Mo
p   xulrunner-1.9-gnome-support     - Support for Gnome in xulrunner-1.9 applica
p   xulrunner-1.9-venkman           - Venkman is Mozilla-based JavaScript debugg
p   xulrunner-gnome-support         - Support for Gnome in xulrunner application
The "c" flag states that the package has been removed but it's configuration files are still present. Running```
sudo aptitude purge xulrunner-1.9
```will remove it's configuration files. Whether that will allow you to reinstall it, is a different question though.

---

### Post by cogvos on 2009-01-04
Ok this gave ....

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-desktop:/$ sudo aptitude purge xulrunner-1.9
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libsdl-ttf2.0-0 
The following packages will be REMOVED:
  xulrunner-1.9{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 77.8kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 176413 files and directories currently installed.)
Removing libsdl-ttf2.0-0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 176406 files and directories currently installed.)
Removing xulrunner-1.9 ...
Purging configuration files for xulrunner-1.9 ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done    

So it looks like Xulrunner has been removed as has that odd libsdl thing.

aptitude search xulrunner shows

v   liferea-xulrunner              -                                          
p   xulrunner                      - XUL + XPCOM application runner           
p   xulrunner-1.9                  - XUL + XPCOM application runner           
p   xulrunner-1.9-dev              - XUL + XPCOM development files            
p   xulrunner-1.9-dom-inspector    - tool for inspecting the DOM of pages in M
p   xulrunner-1.9-gnome-support    - Support for Gnome in xulrunner-1.9 applic
p   xulrunner-1.9-venkman          - Venkman is Mozilla-based JavaScript debug
p   xulrunner-gnome-support        - Support for Gnome in xulrunner applicatio
john@john-desktop:/$ 

But...

I still can't install xulrunner cos of 
xulrunner-1.9:
  Breaks: yelp (<2.22.1-0ubuntu2.8.04.1) but 2.20.0-0ubuntu3.1 is to be installed

and firefox is still insisting it needs it....

In total desperation I completely removed Yelp, which also removed gnome-desktop and gnome-docs (!!!) So I then re-stalled gnome-desktop (which put everything back again) and it still won't work.:confused::confused::confused:

---

### Post by Bachstelze on 2009-01-04
Know what? Instead of trying to install the backported version from the repos, I think you might be better off grabbing Firefox 3 from Mozilla's website and using that. :p

---

### Post by cogvos on 2009-01-04
OK... I've downloaded 3.0.5 and its now sitting in the archive manager as a folder... erm stupid question - what now? Do I just double click... drag the folder somewhere - in which case where? or what?

Also is this weird Yelp problem going to bite me in the future?

John.

---

### Post by northern lights on 2009-01-04
mkey.

I think I figured it out.

You did not run a distribution upgrade as HymnToLife suggested, right? Cause this suggestion of hers appears more necessary than you, I or even she might have figured.

The version of xulrunner-1.9 icluded in gutsy is [1.9 Alpha8]("http://packages.ubuntu.com/search?keywords=xulrunner-1.9&searchon=names&suite=gutsy&section=all") opposed to [1.9.0.5]("http://packages.ubuntu.com/search?keywords=xulrunner-1.9&searchon=names&suite=intrepid&section=all") in Hardy or Intrepid.

You either have to upgrade to at least Hardy, or remove all instances of xulrunner (as you have before using *aptitude purge*) and install from source. Check [here]("http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/") for that option. I'd highly recommend upgrading to Hardy.

---

### Post by Bachstelze on 2009-01-04
> **northern lights said:**
> 
The version of xulrunner-1.9 icluded in gutsy is [1.9 Alpha8]("http://packages.ubuntu.com/search?keywords=xulrunner-1.9&searchon=names&suite=gutsy&section=all") opposed to [1.9.0.5]("http://packages.ubuntu.com/search?keywords=xulrunner-1.9&searchon=names&suite=intrepid&section=all") in Hardy or Intrepid.

He has the backports repo enabled, which has 1.9.0.3.

[http://packages.ubuntu.com/gutsy-backports/xulrunner-1.9](http://packages.ubuntu.com/gutsy-backports/xulrunner-1.9)

---

### Post by Bachstelze on 2009-01-04
> **cogvos said:**
> OK... I've downloaded 3.0.5 and its now sitting in the archive manager as a folder... erm stupid question - what now? Do I just double click... drag the folder somewhere - in which case where? or what?

```
sudo tar xzvf Firefox-blahblahblah.tar.gz -C /opt
/opt/firefox/firefox
```

The first command will extract Firefox in /opt, and the second one will run it.

---

### Post by northern lights on 2009-01-04
> **HymnToLife said:**
> He has the backports repo enabled, which has 1.9.0.3
Darn it.

This issue can't be so freakin' hard to fix.

I'm stumped, though. This was the last straw I was holding on to.

---

### Post by cogvos on 2009-01-04
Oh darn. I guess this explains things... OK I dread to ask... How do I upgrade? The only synaptic option I have is 8.04 LTS. But that's a server system isn't it? This really seams a sledgehammer to crack a walnut, and sorry to say this I really can see why people stick with Microsoft at present. It's a rubbish product, but you just download things and they work... well sort of, slowly and with huge security holes, but they work... kind of.

---

### Post by kansasnoob on 2009-01-04
I really, really like the simplicity of Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Just start where it says:

> Usage Instructions

Installation

Note: after installation, do not remove the repositories version of Firefox, as doing so will break a lot of Gnome packages that depend on the Gecko rendering engine.

Here are the steps to use this script to install the Mozilla build of Firefox, Thunderbird, or SeaMonkey:

    * Download .deb installer of the latest release (follow this link to the file release servers), and save it to your disk.
          o Users of 64 bit Ubuntu, get the amd64 package (and see this note for 64 bit users); users of 32 bit Ubuntu get the i386 package. To determine which one you have .............


Download it to your desktop. Then double click it to install it.

Then go to terminal and:

```
ubuntuzilla.py -a install -p firefox

```

The installer will ask a few simple questions like do you want the newest version, setting language, etc. Just be patient! At the very end it'll ask if you want to enable auto-updates for Firefox.

It's sweet (and easy).

---

### Post by cogvos on 2009-01-04
Actually belay that last post!

They gnome synaptic is telling me that Xulrunner is_ not_ installed. there are no green boxes on any items marked Xulrunner - see below attachment

There is also a xulrunner at 1.8.1.4.2ubunttu5 listed (which is also not installed)

If this is the case then how does Yelp work if it does need it? Surly it should be screaming (or whatever) I'm broken? If it does not need it (and HymToLife has told me that it does not, then is there a problem with some kind of 'this package needs these packages sor of index file' thing? If I deit that file to say 'don't use Xulrunner' will that fix the problem?

<edit.

Really easy Kansasnoob? Please tell me yes....

---

### Post by Bachstelze on 2009-01-04
> **cogvos said:**
> If it does not need it (and HymToLife has told me that it does not, then is there a problem with some kind of 'this package needs these packages sor of index file' thing? If I deit that file to say 'don't use Xulrunner' will that fix the problem?

It doesn't need it *directly*, but most likely it needs a package that in turn needs it.

---

### Post by cogvos on 2009-01-04
> **HymnToLife said:**
> It doesn't need it *directly*, but most likely it needs a package that in turn needs it.


Hmmm... 'Twas on a Monday morning the gasman came to call... ' Google Flanders and Swan if anyone wonders what I'm gibbering on about.,

If I upgrade (and can someone tell me how) will this fix all the grief I am having? Or should I go for kansasnoob's solution. Is it simple? I like simple...

---

### Post by northern lights on 2009-01-04
> **cogvos said:**
> should I go for kansasnoob's solution. Is it simple? I like simple...
If he says it's easy, it most likely is. Whether it's gonna work without xulrunner (i.e. not depend on it also) I wouldn't be too certain. But what the heck? Try it. Can't screw anything up much more, FF-wise...

> **cogvos said:**
> If I upgrade (and can someone tell me how) will this fix all the grief I am having?
Would never promise something I can't know. And it can't be know for sure, as it depends on what's causing your error, which we still haven't figured out.

I'd upgrade regardless, though.

Run```
update-manager --devel-release
```to upgrade the release.

---

### Post by kansasnoob on 2009-01-04
> **cogvos said:**
> Actually belay that last post!

They gnome synaptic is telling me that Xulrunner is_ not_ installed. there are no green boxes on any items marked Xulrunner - see below attachment

There is also a xulrunner at 1.8.1.4.2ubunttu5 listed (which is also not installed)

If this is the case then how does Yelp work if it does need it? Surly it should be screaming (or whatever) I'm broken? If it does not need it (and HymToLife has told me that it does not, then is there a problem with some kind of 'this package needs these packages sor of index file' thing? If I deit that file to say 'don't use Xulrunner' will that fix the problem?

<edit.

Really easy Kansasnoob? Please tell me yes....

Yeah, really easy! I've been doing some testing for nanotube:

[http://ubuntuforums.org/showthread.php?t=1016213](http://ubuntuforums.org/showthread.php?t=1016213)

And it tends to install needed dependencies. If not, it tends to tell you just what's wrong!

---

### Post by madmaxnj on 2009-01-05
Why the urgency for FF3?  Just a question.

FWIW.  I'm running Intrepid and one of the recently recommended updates something totally hosed up with FF3 and xulrunner 1.9 and now nothing works.  I had to completely uninstall both and installed an ancient version of Seamonkey just to get internet back.

[http://ubuntuforums.org/showthread.php?t=1026086](http://ubuntuforums.org/showthread.php?t=1026086)

If you've been so reluctant to upgrade your OS, maybe you should stay with your working browser too.  Just my 2c.

---

