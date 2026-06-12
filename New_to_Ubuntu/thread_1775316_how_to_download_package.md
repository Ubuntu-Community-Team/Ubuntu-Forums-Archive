---
title: "how to download package?"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by psihokiller4 on 2011-06-04
well I have a problem:

```
military@military-PC-linux:~$ sudo aptitude install wine1.3
[sudo] password for military: 
žE: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
military@military-PC-linux:~$ sudo aptitude install wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  smbclient 
The following NEW packages will be installed:
  ttf-droid{a} ttf-symbol-replacement-wine1.3{a} ttf-umefont{a} unrar{a} wine1.3 wine1.3-gecko{a} 
The following packages will be REMOVED:
  wisotool{u} 
The following packages will be upgraded:
  cabextract libwbclient0 samba-common ttf-mscorefonts-installer winbind winetricks 
6 packages upgraded, 6 newly installed, 1 to remove and 250 not upgraded.
Need to get 16.5MB/92.3MB of archives. After unpacking 228MB will be used.
The following packages have unmet dependencies:
  smbclient: Depends: samba-common (= 2:3.4.7~dfsg-1ubuntu3.2) but 2:3.4.7~dfsg-1ubuntu3.5 is to be installed.
The following actions will resolve these dependencies:

Upgrade the following packages:
smbclient [2:3.4.7~dfsg-1ubuntu3.2 (now) -> 2:3.4.7~dfsg-1ubuntu3.5 (lucid-updates)]

Score is 120

Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  ttf-droid{a} ttf-symbol-replacement-wine1.3{a} ttf-umefont{a} unrar{a} wine1.3 wine1.3-gecko{a} 
The following packages will be REMOVED:
  wisotool{u} 
The following packages will be upgraded:
  cabextract libwbclient0 samba-common smbclient ttf-mscorefonts-installer winbind winetricks 
7 packages upgraded, 6 newly installed, 1 to remove and 249 not upgraded.
Need to get 28.0MB/104MB of archives. After unpacking 228MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/universe cabextract 1.2-3+lenny1build0.10.04.1 [54.9kB]
Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main ttf-symbol-replacement-wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
  404  Not Found
Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
  404  Not Found
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main smbclient 2:3.4.7~dfsg-1ubuntu3.5
  404  Not Found [IP: 91.189.88.140 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main winbind 2:3.4.7~dfsg-1ubuntu3.5
  404  Not Found [IP: 91.189.88.140 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main samba-common 2:3.4.7~dfsg-1ubuntu3.5
  404  Not Found [IP: 91.189.88.140 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main libwbclient0 2:3.4.7~dfsg-1ubuntu3.5
  404  Not Found [IP: 91.189.88.140 80]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse ttf-mscorefonts-installer 3.2ubuntu0.1 [40.2kB]
Fetched 95.1kB in 0s (161kB/s)                
Preconfiguring packages ...
(Reading database ... 159332 files and directories currently installed.)
Removing wisotool ...
Selecting previously deselected package wine1.3-gecko.
(Reading database ... 159329 files and directories currently installed.)
Unpacking wine1.3-gecko (from .../wine1.3-gecko_1.2.0-0ubuntu1~maverickppa1_i386.deb) ...
Preparing to replace cabextract 1.2-3+lenny1build0.9.10.1 (using .../cabextract_1.2-3+lenny1build0.10.04.1_i386.deb) ...
Unpacking replacement cabextract ...
Preparing to replace winetricks 0.0+20101106-0ubuntu1~lucidppa1 (using .../winetricks_0.0+20110429~ppa1_i386.deb) ...
Unpacking replacement winetricks ...
Selecting previously deselected package ttf-droid.
Unpacking ttf-droid (from .../ttf-droid_1.00~b112+dfsg+1-0ubuntu1_all.deb) ...
Preparing to replace ttf-mscorefonts-installer 3.0 (using .../ttf-mscorefonts-installer_3.2ubuntu0.1_all.deb) ...
Unpacking replacement ttf-mscorefonts-installer ...
Selecting previously deselected package ttf-umefont.
Unpacking ttf-umefont (from .../ttf-umefont_411-1_all.deb) ...
Selecting previously deselected package unrar.
Unpacking unrar (from .../unrar_1%3a3.9.3-1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for fontconfig ...
Processing triggers for python-support ...
Setting up wine1.3-gecko (1.2.0-0ubuntu1~maverickppa1) ...
Setting up cabextract (1.2-3+lenny1build0.10.04.1) ...
Setting up winetricks (0.0+20110429~ppa1) ...
Setting up ttf-droid (1.00~b112+dfsg+1-0ubuntu1) ...
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for DroidSansJapanese, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for DroidSansJapanese-JaH, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-droid

Setting up ttf-mscorefonts-installer (3.2ubuntu0.1) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

All fonts downloaded and installed.

Setting up ttf-umefont (411-1) ...
Setting up unrar (1:3.9.3-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode.

E: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/ttf-symbol-replacement-wine1.3_1.3.19-0ubuntu1~lucid1~ppa1_all.deb: 404  Not Found
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Current status: 253 updates [-4].

```so how do I get that package my self?

I asked google for it and I cant get it from here :S

[http://www.ubuntuupdates.org/packages/show/210098](http://www.ubuntuupdates.org/packages/show/210098)

---

### Post by wolfen69 on 2011-06-04
Do you have synaptic or software center open while trying to get it through terminal? If so, close them.

---

### Post by psihokiller4 on 2011-06-04
no the problem is I first tried with them and I failed well than I closed them so I wouldn't type every detail so I copy paste from terminal

ofc I closed synaptic before I continued with terminal

and I couldn't get package ttf-symbol-replacement-wine1.3 as there's something wrong with server or IDK

---

### Post by wildmanne39 on 2011-06-04
> **psihokiller4 said:**
> no the problem is I first tried with them and I failed well than I closed them so I wouldn't type every detail so I copy paste from terminal

ofc I closed synaptic before I continued with terminal

and I couldn't get package ttf-symbol-replacement-wine1.3 as there's something wrong with server or IDK
Hi, either there server is down or those files are no longer on those that server.

---

### Post by psihokiller4 on 2011-06-05
ok I believe that but how do I get that files than???

---

### Post by dcsoldschool53 on 2011-06-05
[B]What version of ubuntu are you using? Did you add the ppa repository? Because what I don't see in your pasting of the terminal code, is the ppa repository. Try this link [http://www.winehq.org/download/ubuntu ]("http://www.winehq.org/download/ubuntu")
and add the ppa repository. This site will also  tell you how to install wine 3.  Let us know what happens or try this one [https://launchpad.net/~ubuntu-wine/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa?field.series_filter=")




[/B]

---

### Post by IWantFroyo on 2011-06-05
What happens if you run:
```
sudo apt-get update
```

---

### Post by psihokiller4 on 2011-06-05
> **dcsoldschool53 said:**
> [B]What version of ubuntu are you using? Did you add the ppa repository? Because what I don't see in your pasting of the terminal code, is the ppa repository. Try this link [http://www.winehq.org/download/ubuntu ]("http://www.winehq.org/download/ubuntu")
and add the ppa repository. This site will also  tell you how to install wine 3.  Let us know what happens or try this one [https://launchpad.net/~ubuntu-wine/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa?field.series_filter=")




[/B]
woow I get a problem:

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```
```
An error occurred

The following details are provided:
[CODE]E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: Unable to lock the list directory

```[/CODE]
```
An error occurred

The following details are provided:
[CODE]E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```[/CODE]
I tried to add repo:
[I]ppa:ubuntu-wine/ppa

and tried to reload didn't know what's wrons so I started deleting not checked old repos and even deleted the wine repo so I guess I have problems from before maybe a bug did it :S

witch ubuntu 10.04 LTS
[/I]
uname -a
```
Linux military-PC-linux 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux
```




EDIT:

apt-get update
E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list

---

### Post by psihokiller4 on 2011-06-05
[SOLVED]

problem was somewhere else along time before don't know how that I found it now and not before but thanks :)

[http://ubuntuforums.org/showthread.php?t=1776064](http://ubuntuforums.org/showthread.php?t=1776064)

---

