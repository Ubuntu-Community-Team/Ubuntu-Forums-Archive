---
title: "cant install wine from anywhere"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by kitsuneclem on 2011-03-26
Ive been trying to Install wine from Both The terminal the wine Homepage and the Ubuntu software center with no success Keeps saying a irreparable error has acurrd and the install is forced to shut down

Ive had to reinstall Ubuntu (cause for some reason the last one broke) and I have been unable to reinstall Wine

please Id like some help thats easy to follow to get wine working on my computer

---

### Post by aaaaalex on 2011-03-26
Are you saying that ```
sudo apt-get install wine
``` gives you an error message? 

Can you paste that message here? I am sure we can get it fixed in no time.

---

### Post by kitsuneclem on 2011-03-26
> **aaaaalex said:**
> Are you saying that ```
sudo apt-get install wine
``` gives you an error message? 

Can you paste that message here? I am sure we can get it fixed in no time.

This is what happens in terminal

```
The following NEW packages will be installed:
  cabextract esound-clients esound-common gnome-exe-thumbnailer icoutils
  imagemagick libaudio2 libaudiofile0 libcdt4 libesd0 libgraph4 libgvc5
  libilmbase6 libmagickcore3-extra libmpg123-0 libnetpbm10 libopenal1
  libopenexr6 libpathplan4 libxdot4 netpbm ttf-mscorefonts-installer
  ttf-symbol-replacement ttf-umefont unrar winbind wine wine1.2 wine1.2-gecko
  winetricks
0 upgraded, 30 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.4kB/78.8MB of archives.
After this operation, 220MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main wine all 1.2.2-1ubuntu1~maverick2 [40.4kB]
Fetched 40.4kB in 0s (45.1kB/s)
Preconfiguring packages ...
Selecting previously deselected package ttf-symbol-replacement.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 failed to read on buffer copy for files list for package `cups-ppdc': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2) 
```

---

### Post by aaaaalex on 2011-03-26
Seems you are trying to get the package from a PPA Archive. Are yo sure taht one is working well? Maybe disable it for the time being to kep things simple. 

Also there seems to be something wrong with cups-ppdc... 

What happens if you try to clean your apt cache with ```
sudo apt-get clean
sudo apt-get install --reinstall cups-ppdc
sudo apt-get install wine
```

---

### Post by kitsuneclem on 2011-03-26
> **aaaaalex said:**
> Seems you are trying to get the package from a PPA Archive. Are yo sure taht one is working well? Maybe disable it for the time being to kep things simple. 

Also there seems to be something wrong with cups-ppdc... 

What happens if you try to clean your apt cache with ```
sudo apt-get clean
sudo apt-get install --reinstall cups-ppdc
sudo apt-get install wine
```
 ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 32.5kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main cups-ppdc i386 1.4.4-6ubuntu2.3 [32.5kB]
Fetched 32.5kB in 0s (59.7kB/s)
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 failed to read on buffer copy for files list for package `cups-ppdc': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
```
freezes at 95%

---

### Post by aaaaalex on 2011-03-26
I can only speculate... Maybe somebody else can answer this. Also you could try the #ubuntu irc channel... If you can install x-chat that is...

Sorry dude.

---

### Post by kitsuneclem on 2011-03-26
> **aaaaalex said:**
> I can only speculate... Maybe somebody else can answer this. Also you could try the #ubuntu irc channel... If you can install x-chat that is...

Sorry dude.
actualy Ive just noticed i cant install anything all ive been able to install so far is emenecence and skype

---

### Post by aaaaalex on 2011-03-26
Somehow your apt is broken. Just occured to me:

In Synaptic there is an option to 'Fix Broken Packages'. Can you try that?

---

