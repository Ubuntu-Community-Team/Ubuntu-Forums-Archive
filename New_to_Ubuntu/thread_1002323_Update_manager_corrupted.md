---
title: "Update manager corrupted?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by kminney on 2008-12-04
Trouble starting hardy. Update was giving an error message and can't get into synaptic package manager.
Used command line and things loaded, but ended with error message:
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

What do I do.
Also, the tool bar is imcomplete and my mouse can't drag and drop.
Think it;s a gnome problem, but I am a newbie and don't know what to do.
Thanks in advance.
Kevin

---

### Post by taurus on 2008-12-04
Let's have a look at your /etc/apt/sources.list to make sure everything is in order.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by kminney on 2008-12-05
Here you go and thank you.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by halitech on 2008-12-05
when you did it fromt the command line, did you prefix it with sudo?

---

### Post by taurus on 2008-12-05
> **kminney said:**
> Here you go and thank you.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

I believe that is just the last screen.  Scroll up from a terminal and post the whole /etc/apt/sources.list.

---

### Post by kminney on 2008-12-05
That unfortunately was it.
I used the kde log in function so I'm able to use my mouse normally, but I don't know what will happen with the update manager.
I was in gnome.
I go to package manager and it searches and gives this error message;
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
What next?
Thanks,
kevin

---

### Post by kminney on 2008-12-05
Got into synaptic package manager got this message:
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by taurus on 2008-12-05
Close down synaptic.  Then, what happens when you run this command from a terminal?

```
sudo apt-get update
```

---

### Post by kminney on 2008-12-05
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [390kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [7487B]    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [102kB]           
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [892B]      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [147kB]      
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [34.0kB]      
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [24.2kB]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [4020B]    
Fetched 768kB in 11s (69.2kB/s)                                                 
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
So what now?
Thanks,
Kevin

---

### Post by halitech on 2008-12-07
try this in a terminal

```
apt-get clean all
```

---

### Post by BunnyGirlDoom on 2008-12-08
I am having this issue as well. I spent a few hours researching this last night with no solution to my specific situation. Seems to have happened after my laptop went to sleep/hibernate. When I came back to it it was on but wouldn't come out of hibernation. I did a hard boot and suddenly I couldn't boot into Ubuntu - would freeze at it was loading (blinking scroll and capslock LEDs). None of the other 2 kernel versions or "safe" modes would boot either.

Finally, I booted with my Live CD and used Gparted to check errors on my boot drive (listed as SDA5). The check fixed errors and allowed me to reboot but then I got a package manager warning - the same as above.

I have tried 
```
dpkg --clear-avail
```
```
apt-get clean
```
```
apt-get update
```
```
apt-get upgrade
```

and

```
dpkg --configure -a
```

That code above produced:

> -- dpkg: parse error, in file `/var/lib/dpkg/status' near line 2

I tried replacing the status file with status-old but still the same problem. Further more I am unable to open either of the status files and display as "unknown" for file type. Not sure if they had always been this way but they seem to be the only files in that directory listed as "unknown."

I was considering seeing if Live CD has a status file I can use to at least get package manager running but I'm not sure how my system would response as it would not have the correct apps installed. I figured if I could open the corrupted status file, I could compare it to a good status file ans see if i could hand correct errors, but I'm not sure how to edit the file. When I try to access it through terminal it says the file isn't there.

I can output the errors I am getting in package manager and post them here after work. 

One thing I would like to do is output my boot log - even though it boots now it will stop the load bar and go into text load with an error in red that goes by very quick. Not sure if this is related to package manager or another system error. How can I get a log of my startup?

Thanks! Will add more info when I am home.

-BGD

Oh! Not sure if this will be useful - this system was dual boot but I wanted to switch over to linux completely on that machine so I reformatted the WinXP partition and removed the section with the choice to boot XP in grub. I am doubtful that is an issue since it had booted fine since then, on a number of boots, but thought I should maybe mention it.

Last app I installed before it went kaplooey was VirtualBox, if that matters.

Cheers!

---

### Post by sneeks on 2008-12-08
i did have this problem a few weeks ago,but with gutsy,and it was down to a specific program not being able to update,i think it was something to do with hp printing,so i removed them,and all was well

---

### Post by BunnyGirlDoom on 2008-12-09
Update:

Ok the red warning I get while booting is just after it mentions virtual box (which I uninstalled before the problem yesterday).

Also, I was unable to open status files (inducing backup and old) with text editor but WAS able to access it in OpenOffice. The file is completely garbled, so I'm thinking it's unrepairable at this pint. I made a backup and stored it on another drive (of the corrupted status) and replaced it with the Live CD status file. When I did a --configure command it told me it encountered and End of File error.

So, not sure what to do at this point. Is there a way to complete reinstall package manager? How will that affect my current installed apps? I am assuming they will not show as installed, for one - including packages available from Update Mgr - but is it possible to relink them somehow? Or am I looking at a total system reinstall?

Thanks!

-BGD

---

### Post by kminney on 2008-12-09
I tried the apt get clean all and got this error message:
 Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
 What Bunny girl is talking about is similar to mine.
Getting my computer to start up after hibernation seemed to start this off.
I'm interested in the idea of a reinstall too.
Thanks for the help,
kevin

---

### Post by Tatty on 2008-12-09
> **kminney said:**
> I tried the apt get clean all and got this error message:
 Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory


That error message usually means you have another instance of a package manager open.  You can only run one instance of apt-get/synaptic/add-remove programs/etc at a time.

---

### Post by kminney on 2008-12-10
No other manager open
Thanks,
Kevin

---

### Post by BunnyGirlDoom on 2008-12-16
*bump*

---

