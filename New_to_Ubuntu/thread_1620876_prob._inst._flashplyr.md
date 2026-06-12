---
title: "prob. inst. flashplyr"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by fairbrother89 on 2010-11-13
please excuse my laziness as i'm sure the answer is somewhere on the forum. would you mind giving me a link to it if it is please.
i have upgraded my installation to version 8.04 and tried to instal adobe flash player 10. the eeror meesage i get is; dependency is not satisfiable libpango 1.0-0.
i don't know what that means or what to do.
thanks for your help.

---

### Post by fairbrother89 on 2010-11-15
no replies. i just don't know what i'm going to do about all this linux business. i'll just have to persevere. maybe i'll install issue 10 of ubuntu.i don't know why it didn't just upgrade to that straight away. when i did issue 8. one at a time i suppose. libpango. cairo. what is this. its all greek to me. :guitar:

---

### Post by sikander3786 on 2010-11-15
Hi. Sorry your first ever post got a late reply :-) Might be because there was not a lot of information present there. Don't know :-)

From terminal please post the output of

```
sudo apt-get update
```

and

```
sudo apt-get install -f
```

Which version of Ubuntu were you running previously before upgrading to 8.04?

---

### Post by fairbrother89 on 2010-11-16
hi many thanks for your reply. it looks like i was running 7.1 prior to the update. it was a cover dvd on linux format mag. from 2008. i installed it over a defunct pirate copy of windows which microsoft had helpfully disabled which felt like my house being repossesed but i couldn't go back in to get my belongings.
i typed what you said into the terminal after the word desktop and my name at the cursor. it then requested a password but when i tried typing my password the cursor stopped flashing and nothing appeared. does this sound normal ?
btw. i went into your package manager and libpango 1.0-0 is there and selected.
i should have mentioned its a fairly old pc amd athlon 2600 and asrock mb with built in graphics controller.

---

### Post by sikander3786 on 2010-11-16
> it then requested a password but when i tried typing my password the cursor stopped flashing and nothing appeared. does this sound normal ?

After you copy/paste the commands from my above post and hit Enter, you'll be prompted to enter your password. Enter it and again hit Enter. You'll not see any characters or asterisk when you type password, type blindly and after hitting Enter, you'll see an output. Copy/paste that output from Terminal and post here.

> btw. i went into your package manager and libpango 1.0-0 is there and selected.

That package itself might be installed but it is broken because all its dependencies are not met.

The commands I posted earlier might fix the error or at least the output might give us a better idea of the problem.

---

### Post by fairbrother89 on 2010-11-16
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages      
Fetched 19.6kB in 0s (62.4kB/s)
Reading package lists... Done
phil@phil-desktop:~$ [this is the output to the first code]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phil@phil-desktop:~$ [this to the second code]


the above is what i'm getting[hopoe this helps]. thanks again.

---

### Post by fairbrother89 on 2010-11-17
mm still won't instal. wonder whether libpango won't be satisfied due to some hardware issue. i have 512mb memory installed but unsure of how much mem. the built in graphics adapter has. its a 2003 system essentially with asrock k7 s41gx motherboard. athlon 2600 cpu. chrome wouldn't instal either due to cairo2 not being happy.

---

### Post by sikander3786 on 2010-11-17
> **fairbrother89 said:**
> Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages      
Fetched 19.6kB in 0s (62.4kB/s)
Reading package lists... Done
phil@phil-desktop:~$ [this is the output to the first code]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phil@phil-desktop:~$ [this to the second code]


the above is what i'm getting[hopoe this helps]. thanks again.
This is not the complete output. Please copy/paste whole of it right here.

This one doesn't list any error at all.

---

### Post by fairbrother89 on 2010-11-17
i'm sorry but thats the only output i'm able to get. i've asked for each code twice and its the same story.
phil@phil-desktop:~$ sudo apt-get update
[sudo] password for phil: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages      
Fetched 19.6kB in 0s (64.2kB/s)
Reading package lists... Done
phil@phil-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Reading package lists... Done
phil@phil-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phil@phil-desktop:~$ 
phil@phil-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phil@phil-desktop:~$

---

### Post by sikander3786 on 2010-11-17
> **fairbrother89 said:**
> i'm sorry but thats the only output i'm able to get. i've asked for each code twice and its the same story.
phil@phil-desktop:~$ sudo apt-get update
[sudo] password for phil: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages      
Fetched 19.6kB in 0s (64.2kB/s)
Reading package lists... Done
phil@phil-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Reading package lists... Done
phil@phil-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phil@phil-desktop:~$ 
phil@phil-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phil@phil-desktop:~$
There are no messages at all :-)

Now type this and post the output as well.

```
sudo aptitude install flashplugin-installer
```

---

### Post by fairbrother89 on 2010-11-17
phil@phil-desktop:~$ sudo aptitude install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "flashplugin-installer"
Couldn't find any package whose name or description matched "flashplugin-installer"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
phil@phil-desktop:~$ 

looks like it couldn't find anything. the downloads are still in the download folder in firefox if thats of any relevance.

---

### Post by sikander3786 on 2010-11-17
Sorry you are using 8.04 so the command will look like,

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by fairbrother89 on 2010-11-17
phil@phil-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
phil@phil-desktop:~$

---

### Post by sikander3786 on 2010-11-17
Go to System > Administration > Software Sources and make sure Multiverse, Main, Universe, Restricted and Source repositories are enabled. Enable all of them and then,

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

If it still returns an error, also post the output of

```
cat /etc/apt/sources.list
```

---

### Post by fairbrother89 on 2010-11-17
phil@phil-desktop:~$ sudo apt-get update && sudo apt-get install flashplugin-nonfree
[sudo] password for phil: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 49 not upgraded.
Need to get 18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse flashplugin-nonfree 9.0.124.0ubuntu2 [18.7kB]
Fetched 18.7kB in 0s (198kB/s)           
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 136738 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--19:42:11--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 2.19.210.70
Connecting to fpdownload.macromedia.com|2.19.210.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:42:12 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

phil@phil-desktop:~$

---

### Post by fairbrother89 on 2010-11-17
phil@phil-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main multiverse restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main multiverse restricted universe #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
phil@phil-desktop:~$

---

### Post by sikander3786 on 2010-11-17
> Resolving fpdownload.macromedia.com... 2.19.210.70
Connecting to fpdownload.macromedia.com|2.19.210.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:42:12 ERROR 404: Not Found.

I have tested and macromedia server is not responding thats why it is returning 404 Error.

I found a workaround here to install the latest flash but beta.

[http://markusthielmann.com/blog/flash_10_beta_ubuntu_hardy](http://markusthielmann.com/blog/flash_10_beta_ubuntu_hardy)

Sad it is taking you too long and obstacle after obstacle but not Ubuntu's fault :-)

---

### Post by fairbrother89 on 2010-11-17
ok sikander. thanks very much for your help. would you suggest i install a beta version or wait for macromedia to respond. are we saying it was macremedia all along and thats why the original error occured ?

---

### Post by sikander3786 on 2010-11-17
No it was not macromedia at first. You had disabled almost all the repositories some-how under Software Sources and thats why you were not able to find the flash package. Now when you are able to find it, it is not responding :-)

And you might not be getting updates since the repositoies were disable. Re-check once again. Go to Software Sources > Updates and make sure lucid-updates and lucid-security is enabled and immediately do,

```
sudo apt-get update && sudo apt-get upgrade
```

Regarding beta version, I myself am using many software from Launchpad PPAs and never had a problem. No guarantees though.

Good Luck!

---

### Post by fairbrother89 on 2010-11-17
i don't see lucid anything i only see
hardy security
hardy proposed
hardy updates
hardy backports
**none of these are ticked.**
however check for daily updates is ticked.

---

### Post by sikander3786 on 2010-11-17
Tick hardy-security and hardy-updates.

I am sorry. Lucid is 10.04 while you are running hardy 8.04. Mixing up the 2 LTS release :-)

---

### Post by fairbrother89 on 2010-11-17
ok i've checked updates and security ran your code and its still updating. i won't post the output to that cade as it will likely take up the whole forum its still going. hope i've done the right thing.

---

### Post by sikander3786 on 2010-11-17
Yes it should've been a long output.

Hopefully everything would be fine.

---

### Post by fairbrother89 on 2010-11-18
i now have all updates for 8.04. flas installed. it has crashed once so far, maybe just teething troubles. anyway i've learnt a bit and understand how things work better now, so thanks. i guess the next thing i should do is upgrade to ubuntu 10. ;) and install a new graphics card as my picture isn't that great.

---

### Post by sikander3786 on 2010-11-18
Regarding upgrade to Lucid,

[https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS)

Which graphics card have you got? And which one are you planning to install?

If there are proprietary drivers installed in 8.04, it'd be better to remove them before running an upgrade as there often seems to be a problem...

---

### Post by fairbrother89 on 2010-11-18
i have an asrock motherboaed circa 2003 with built in sis chip. **i would **l**ike some advice on an upgrade.** _used card probably from ebay._ nothing too fancy as i don't play games just want something that will show an improvement on what i have. 
i switched to this older pc as my windows system was playing up. thats a 2006 system but i've noticed using the same monitor that this linux set up is giving an inferior picture using any resolution.

---

### Post by cucu007 on 2010-11-19
> **sikander3786 said:**
> There are no messages at all :-)

Now type this and post the output as well.

```
sudo aptitude install flashplugin-installer
```

Worked like a charm, just make sure those of you with a new install of 10.10 Maverick you will need to install aptitude using sudo apt-get install aptitude prior to executing the command, unless you wish to use sudo apt-get install flashplugin-installer..:p

---

