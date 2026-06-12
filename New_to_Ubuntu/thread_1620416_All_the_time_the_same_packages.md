---
title: "All the time the same packages"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by vasiauvi on 2010-11-13
Hello all,
it's been a while since I've put a new thread here on ubuntuforums.org but now I need your clarification. Every time I'm upgrading my list of programs I get at least the same packages:
```
The following packages will be upgraded:
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg-extra
  firefox firefox-branding firefox-gnome-support xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support xulrunner-1.9.2
```
Can you tell me, please, why this is happening? Or what is causing this?

Thank you and have a nice day!

---

### Post by sikander3786 on 2010-11-13
Try

```
sudo apt-get update && sudo apt-get upgrade
```

Say Yes when prompted and post the output. If the upgrade was successful, they should not appear again.

---

### Post by vasiauvi on 2010-11-13
> **sikander3786 said:**
> Try

```
sudo apt-get update && sudo apt-get upgrade
```

Say Yes when prompted and post the output. If the upgrade was successfull, they should not appear again.

Hello,
Thanks for response!
Every time I make the update & upgrade and every time, everyday I get at least the same packages, meaning I get the update for other programs + this packages above. This are like dummies to me! Tomorrow after I will do update and upgrade I will get the same packages...

---

### Post by azertyh on 2010-11-13
hello,
run update manager, tick updates ONLY about chromium and install updates. when it finished, tick updates only about firefox and install updates ; and so on.
perhaps, you will find which updates can't be updated.

---

### Post by mcduck on 2010-11-13
> **vasiauvi said:**
> Hello,
Thanks for response!
Every time I make the update & upgrade and every time, everyday I get at least the same packages, meaning I get the update for other programs + this packages above. This are like dummies to me! Tomorrow after I will do update and upgrade I will get the same packages...

Next time you do that, could you post the whole output from apt-get here please? That would make it a lot easier to figure out what's happening...

---

### Post by oldos2er on 2010-11-13
> **vasiauvi said:**
>  Every time I'm upgrading my list of programs I get at least the same packages:
```
The following packages will be upgraded:
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg-extra
  firefox firefox-branding firefox-gnome-support xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support xulrunner-1.9.2
```
Can you tell me, please, why this is happening? Or what is causing this?


Do you have their nightly (or daily) PPAs enabled?

---

### Post by wojox on 2010-11-13
Try

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Else change servers.

---

### Post by OneMixDJ on 2010-11-27
> **sikander3786 said:**
> Try

```
sudo apt-get update && sudo apt-get upgrade
```

Say Yes when prompted and post the output. If the upgrade was successful, they should not appear again.

sikander3786; many thanks!
I had the same problem and your suggestion appears to have worked.
Output is below.
Once it was finished, I ran Update Manager to be sure and I didn't receive any more updates for Chromium. 
10-15 mins later, I did a _Check_ via Update Manager and still no new updates. Good deal!

***______Output______***

[COLOR="Blue"]
cair@karen:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for cair: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
sudo: unable to resolve host karen
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.7MB of archives.
After this operation, 213kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main chromium-codecs-ffmpeg 0.6+svn20101124r67203+67410-0ubuntu1~ucd1~hardy [332kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main chromium-browser-inspector 9.0.595.0~svn20101127r67482-0ubuntu1~ucd1~hardy [553kB]
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main chromium-browser 9.0.595.0~svn20101127r67482-0ubuntu1~ucd1~hardy [14.8MB]
Fetched 15.7MB in 1min7s (234kB/s)                                             
(Reading database ... 108326 files and directories currently installed.)
Preparing to replace chromium-codecs-ffmpeg 0.6+svn20101116r66222+66999-0ubuntu1~ucd1~hardy (using .../chromium-codecs-ffmpeg_0.6+svn20101124r67203+67410-0ubuntu1~ucd1~hardy_i386.deb) ...
Unpacking replacement chromium-codecs-ffmpeg ...
Preparing to replace chromium-browser-inspector 9.0.593.0~svn20101124r67207-0ubuntu1~ucd1~hardy (using .../chromium-browser-inspector_9.0.595.0~svn20101127r67482-0ubuntu1~ucd1~hardy_all.deb) ...
Unpacking replacement chromium-browser-inspector ...
Preparing to replace chromium-browser 9.0.593.0~svn20101124r67207-0ubuntu1~ucd1~hardy (using .../chromium-browser_9.0.595.0~svn20101127r67482-0ubuntu1~ucd1~hardy_i386.deb) ...
Unpacking replacement chromium-browser ...
Setting up chromium-browser-inspector (9.0.595.0~svn20101127r67482-0ubuntu1~ucd1~hardy) ...
Setting up chromium-codecs-ffmpeg (0.6+svn20101124r67203+67410-0ubuntu1~ucd1~hardy) ...
Setting up chromium-browser (9.0.595.0~svn20101127r67482-0ubuntu1~ucd1~hardy) ...[/COLOR]


***_______END_______***

---

### Post by sikander3786 on 2010-11-27
> **OneMixDJ said:**
> sikander3786; many thanks!
I had the same problem and your suggestion appears to have worked.
Output is below.
Once it was finished, I ran Update Manager to be sure and I didn't receive any more updates for Chromium. 
10-15 mins later, I did a _Check_ via Update Manager and still no new updates. Good deal!


You are Welcome :-)

Very few times I see someone who at least searched the forums before posting a new thread :-)

Happy Ubuntu-ing!

---

### Post by vasiauvi on 2010-11-30
Hello,
Thanks for helping me and sorry that I didn't responded quicker but I made a fresh install of Maverick and obvious I don't have the same issue.

The thing was that I had the dayly builds PPA and this meaning that maybe the applications were updated dayly and that's why I had everyday the same updates.

---

