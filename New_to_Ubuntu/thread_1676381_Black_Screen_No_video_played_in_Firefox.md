---
title: "Black Screen/ No video played in Firefox"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by CaronMargarete on 2011-01-27
I use Ubuntu 10 with firefox 3.6.13 on an Acer Aspire 4535 64bit laptop. 

I have a black screen and am unable to watch youtube (or other video's). I have done as suggested on the firefox support site by going through all of the extensions, none seem to conflict when I disable/ enable each in turn. There doesn't seem to be a lot of new information on there and a lot of people stating they have the same problem- hence trying this forum for support. 

I have attempted the last command actionparsnip mentions in Question #134187 on the [Ubuntu Launchpad support site]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/134187"):
> ok this will fix you up:

sudo apt-get --purge remove swfdec-mozilla swfdec-gnome flashplugin-installer libswfdec-0.8-0; sudo apt-get --purge autoremove; sudo apt-get clean; sudo apt-get update; sudo apt-get -y install flashplugin-nonfree

Should be ok
I got this result:
<code>
```
caronmargarete@caronmargarete:~$ sudo apt-get --purge remove swfdec-mozilla swfdec-gnome flashplugin-installer libswfdec-0.8-0; sudo apt-get --purge autoremove; sudo apt-get clean; sudo apt-get update; sudo apt-get -y install flashplugin-nonfree
[sudo] password for caronmargarete: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
Package swfdec-gnome is not installed, so not removed
Package libswfdec-0.8-0 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 lib32ncurses5 nspluginwrapper ia32-libs
  linux-headers-2.6.32-24-generic libc6-i386 lib32gcc1 lib32asound2
  linux-headers-2.6.32-24 lib32z1 lib32stdc++6 lib32v4l-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-installer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 188kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 150437 files and directories currently installed.)
Removing flashplugin-installer ...
Purging configuration files for flashplugin-installer ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ia32-libs* lib32asound2* lib32bz2-1.0* lib32gcc1* lib32ncurses5*
  lib32stdc++6* lib32v4l-0* lib32z1* libc6-i386* linux-headers-2.6.32-24*
  linux-headers-2.6.32-24-generic* nspluginwrapper*
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
After this operation, 258MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 150429 files and directories currently installed.)
Removing nspluginwrapper ...
Removing ia32-libs ...
Purging configuration files for ia32-libs ...
Removing lib32stdc++6 ...
Purging configuration files for lib32stdc++6 ...
Removing lib32asound2 ...
Purging configuration files for lib32asound2 ...
Removing lib32bz2-1.0 ...
Removing lib32gcc1 ...
Purging configuration files for lib32gcc1 ...
Removing lib32ncurses5 ...
Purging configuration files for lib32ncurses5 ...
Removing lib32v4l-0 ...
Purging configuration files for lib32v4l-0 ...
Removing lib32z1 ...
Purging configuration files for lib32z1 ...
Removing libc6-i386 ...
Purging configuration files for libc6-i386 ...
dpkg: warning: while removing libc6-i386, directory '/usr/lib32' not empty so not removed.
Removing linux-headers-2.6.32-24-generic ...
Removing linux-headers-2.6.32-24 ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid Release.gpg
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU [1,813B]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU [2,407B]
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU      
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU [91.6kB]
Get:4 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates Release.gpg [198B]            
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU  
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid Release                                 
Get:5 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates Release [44.7kB]              
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid/main Packages                           
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid/restricted Packages           
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid/main Sources                  
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid/restricted Sources            
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid/universe Packages             
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid/universe Sources              
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid/multiverse Packages           
Hit [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid/multiverse Sources            
Get:6 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates/main Packages [438kB]
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release.gpg    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU
Get:7 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates/restricted Packages [3,267B]  
Get:8 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates/main Sources [175kB]          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release                                 
Get:9 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates/restricted Sources [1,443B]   
Get:10 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates/universe Packages [180kB]    
Hit [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Packages                        
Get:11 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates/universe Sources [64.5kB]    
Get:12 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates/multiverse Packages [8,341B]
Get:13 [http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") lucid-updates/multiverse Sources [4,372B]
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release                        
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/multiverse Sources
Fetched 1,016kB in 4s (226kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1
  lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386 nspluginwrapper
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs lib32asound2-plugins
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree ia32-libs lib32asound2
  lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1
  libc6-i386 nspluginwrapper
0 upgraded, 12 newly installed, 0 to remove and 16 not upgraded.
Need to get 41.8MB of archives.
After this operation, 173MB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main libc6-i386 2.11.1-0ubuntu7.7 [3,837kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main lib32gcc1 1:4.4.3-4ubuntu5 [55.3kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main lib32z1 1:1.2.3.3.dfsg-15ubuntu1 [75.9kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main lib32stdc++6 4.4.3-4ubuntu5 [348kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main lib32asound2 1.0.22-0ubuntu7 [332kB]
Get:6 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main lib32bz2-1.0 1.0.5-4ubuntu0.1 [39.7kB]
Get:7 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main lib32ncurses5 5.7+20090803-2ubuntu3 [187kB]
Get:8 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main lib32v4l-0 0.6.4-1ubuntu1 [76.6kB]
Get:9 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe ia32-libs 2.7ubuntu26 [36.6MB]
Get:10 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse nspluginwrapper 1.2.2-0ubuntu6.10.04.1 [193kB]
Get:11 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse flashplugin-installer 10.1.102.65ubuntu0.10.04.1 [20.0kB]
Get:12 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse flashplugin-nonfree 10.1.102.65ubuntu0.10.04.1 [2,114B]
Fetched 41.8MB in 1min 12s (573kB/s)                                           
Preconfiguring packages ...
Selecting previously deselected package libc6-i386.
(Reading database ... 130434 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.11.1-0ubuntu7.7_amd64.deb) ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.4.3-4ubuntu5_amd64.deb) ...
Selecting previously deselected package lib32z1.
Unpacking lib32z1 (from .../lib32z1_1%3a1.2.3.3.dfsg-15ubuntu1_amd64.deb) ...
Selecting previously deselected package lib32stdc++6.
Unpacking lib32stdc++6 (from .../lib32stdc++6_4.4.3-4ubuntu5_amd64.deb) ...
Selecting previously deselected package lib32asound2.
Unpacking lib32asound2 (from .../lib32asound2_1.0.22-0ubuntu7_amd64.deb) ...
Setting up libc6-i386 (2.11.1-0ubuntu7.7) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package lib32bz2-1.0.
(Reading database ... 130756 files and directories currently installed.)
Unpacking lib32bz2-1.0 (from .../lib32bz2-1.0_1.0.5-4ubuntu0.1_amd64.deb) ...
Selecting previously deselected package lib32ncurses5.
Unpacking lib32ncurses5 (from .../lib32ncurses5_5.7+20090803-2ubuntu3_amd64.deb) ...
Selecting previously deselected package lib32v4l-0.
Unpacking lib32v4l-0 (from .../lib32v4l-0_0.6.4-1ubuntu1_amd64.deb) ...
Selecting previously deselected package ia32-libs.
Unpacking ia32-libs (from .../ia32-libs_2.7ubuntu26_amd64.deb) ...
Selecting previously deselected package nspluginwrapper.
Unpacking nspluginwrapper (from .../nspluginwrapper_1.2.2-0ubuntu6.10.04.1_amd64.deb) ...
Selecting previously deselected package flashplugin-installer.
Unpacking flashplugin-installer (from .../flashplugin-installer_10.1.102.65ubuntu0.10.04.1_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.1.102.65ubuntu0.10.04.1_amd64.deb) ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Setting up lib32gcc1 (1:4.4.3-4ubuntu5) ...

Setting up lib32z1 (1:1.2.3.3.dfsg-15ubuntu1) ...

Setting up lib32asound2 (1.0.22-0ubuntu7) ...

Setting up lib32bz2-1.0 (1.0.5-4ubuntu0.1) ...

Setting up lib32ncurses5 (5.7+20090803-2ubuntu3) ...

Setting up lib32v4l-0 (0.6.4-1ubuntu1) ...

Setting up lib32stdc++6 (4.4.3-4ubuntu5) ...

Setting up ia32-libs (2.7ubuntu26) ...

Setting up nspluginwrapper (1.2.2-0ubuntu6.10.04.1) ...
plugin dirs: :/var/lib/flashplugin-installer/
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Auto-update plugins from /usr/lib64/mozilla/plugins
Looking for plugins in /usr/lib64/mozilla/plugins
Auto-update plugins from /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins
Auto-update plugins from /usr/lib64/firefox/plugins
Looking for plugins in /usr/lib64/firefox/plugins
Auto-update plugins from /var/lib/flashplugin-installer/
Looking for plugins in /var/lib/flashplugin-installer/
Auto-update plugins from /root/.mozilla/plugins
Looking for plugins in /root/.mozilla/plugins

Setting up flashplugin-installer (10.1.102.65ubuntu0.10.04.1) ...
Downloading...
--2011-01-27 13:26:05--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65.orig.tar.gz)
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4888067 (4.7M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.1.102.65.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 6.51K 12m6s
    50K .......... .......... .......... .......... ..........  2% 24.4K 7m35s
   100K .......... .......... .......... .......... ..........  3% 7.88K 8m16s
   150K .......... .......... .......... .......... ..........  4% 24.4K 6m54s
   200K .......... .......... .......... .......... ..........  5% 30.5K 5m58s
   250K .......... .......... .......... .......... ..........  6% 30.5K 5m19s
   300K .......... .......... .......... .......... ..........  7% 40.6K 4m46s
   350K .......... .......... .......... .......... ..........  8% 30.6K 4m25s
   400K .......... .......... .......... .......... ..........  9% 40.7K 4m5s
   450K .......... .......... .......... .......... .......... 10% 60.7K 3m45s
   500K .......... .......... .......... .......... .......... 11% 40.7K 3m32s
   550K .......... .......... .......... .......... .......... 12% 40.7K 3m20s
   600K .......... .......... .......... .......... .......... 13% 61.0K 3m8s
   650K .......... .......... .......... .......... .......... 14% 60.8K 2m57s
   700K .......... .......... .......... .......... .......... 15% 61.0K 2m48s
   750K .......... .......... .......... .......... .......... 16% 61.0K 2m39s
   800K .......... .......... .......... .......... .......... 17% 61.0K 2m32s
   850K .......... .......... .......... .......... .......... 18% 61.1K 2m25s
   900K .......... .......... .......... .......... .......... 19% 13.2K 2m31s
   950K .......... .......... .......... .......... .......... 20% 40.7K 2m26s
  1000K .......... .......... .......... .......... .......... 21% 40.5K 2m22s
  1050K .......... .......... .......... .......... .......... 23% 40.8K 2m17s
  1100K .......... .......... .......... .......... .......... 24% 60.9K 2m12s
  1150K .......... .......... .......... .......... .......... 25% 40.8K 2m9s
  1200K .......... .......... .......... .......... .......... 26% 60.9K 2m4s
  1250K .......... .......... .......... .......... .......... 27% 60.9K 2m0s
  1300K .......... .......... .......... .......... .......... 28% 60.9K 1m56s
  1350K .......... .......... .......... .......... .......... 29% 40.8K 1m53s
  1400K .......... .......... .......... .......... .......... 30% 61.1K 1m49s
  1450K .......... .......... .......... .......... .......... 31%  121K 1m45s
  1500K .......... .......... .......... .......... .......... 32% 61.0K 1m42s
  1550K .......... .......... .......... .......... .......... 33% 61.2K 99s
  1600K .......... .......... .......... .......... .......... 34% 60.8K 96s
  1650K .......... .......... .......... .......... .......... 35% 61.5K 93s
  1700K .......... .......... .......... .......... .......... 36%  120K 90s
  1750K .......... .......... .......... .......... .......... 37% 61.1K 87s
  1800K .......... .......... .......... .......... .......... 38% 61.4K 84s
  1850K .......... .......... .......... .......... .......... 39%  121K 81s
  1900K .......... .......... .......... .......... .......... 40% 61.2K 79s
  1950K .......... .......... .......... .......... .......... 41%  121K 76s
  2000K .......... .......... .......... .......... .......... 42% 61.5K 74s
  2050K .......... .......... .......... .......... .......... 43%  120K 72s
  2100K .......... .......... .......... .......... .......... 45% 61.6K 70s
  2150K .......... .......... .......... .......... .......... 46%  121K 67s
  2200K .......... .......... .......... .......... .......... 47% 61.5K 65s
  2250K .......... .......... .......... .......... .......... 48%  121K 63s
  2300K .......... .......... .......... .......... .......... 49%  121K 61s
  2350K .......... .......... .......... .......... .......... 50% 61.6K 59s
  2400K .......... .......... .......... .......... .......... 51%  121K 57s
  2450K .......... .......... .......... .......... .......... 52%  121K 55s
  2500K .......... .......... .......... .......... .......... 53%  121K 53s
  2550K .......... .......... .......... .......... .......... 54% 61.6K 52s
  2600K .......... .......... .......... .......... .......... 55%  122K 50s
  2650K .......... .......... .......... .......... .......... 56%  121K 48s
  2700K .......... .......... .......... .......... .......... 57%  122K 47s
  2750K .......... .......... .......... .......... .......... 58%  121K 45s
  2800K .......... .......... .......... .......... .......... 59%  121K 43s
  2850K .......... .......... .......... .......... .......... 60% 62.0K 42s
  2900K .......... .......... .......... .......... .......... 61%  122K 40s
  2950K .......... .......... .......... .......... .......... 62%  121K 39s
  3000K .......... .......... .......... .......... .......... 63%  121K 37s
  3050K .......... .......... .......... .......... .......... 64%  122K 36s
  3100K .......... .......... .......... .......... .......... 65%  122K 35s
  3150K .......... .......... .......... .......... .......... 67%  121K 33s
  3200K .......... .......... .......... .......... .......... 68%  122K 32s
  3250K .......... .......... .......... .......... .......... 69%  122K 30s
  3300K .......... .......... .......... .......... .......... 70%  122K 29s
  3350K .......... .......... .......... .......... .......... 71%  122K 28s
  3400K .......... .......... .......... .......... .......... 72%  123K 27s
  3450K .......... .......... .......... .......... .......... 73%  120K 25s
  3500K .......... .......... .......... .......... .......... 74%  124K 24s
  3550K .......... .......... .......... .......... .......... 75%  122K 23s
  3600K .......... .......... .......... .......... .......... 76%  122K 22s
  3650K .......... .......... .......... .......... .......... 77%  122K 21s
  3700K .......... .......... .......... .......... .......... 78%  122K 20s
  3750K .......... .......... .......... .......... .......... 79%  123K 19s
  3800K .......... .......... .......... .......... .......... 80%  122K 17s
  3850K .......... .......... .......... .......... .......... 81%  122K 16s
  3900K .......... .......... .......... .......... .......... 82% 1.84M 15s
  3950K .......... .......... .......... .......... .......... 83%  125K 14s
  4000K .......... .......... .......... .......... .......... 84%  124K 13s
  4050K .......... .......... .......... .......... .......... 85%  123K 12s
  4100K .......... .......... .......... .......... .......... 86%  122K 11s
  4150K .......... .......... .......... .......... .......... 87%  124K 10s
  4200K .......... .......... .......... .......... .......... 89%  123K 9s
  4250K .......... .......... .......... .......... .......... 90% 6.93K 9s
  4300K .......... .......... .......... .......... .......... 91% 2.20M 8s
  4350K .......... .......... .......... .......... .......... 92% 58.9K 7s
  4400K .......... .......... .......... .......... .......... 93%  120K 6s
  4450K .......... .......... .......... .......... .......... 94% 61.3K 5s
  4500K .......... .......... .......... .......... .......... 95%  121K 4s
  4550K .......... .......... .......... .......... .......... 96% 61.5K 3s
  4600K .......... .......... .......... .......... .......... 97%  121K 2s
  4650K .......... .......... .......... .......... .......... 98% 61.5K 1s
  4700K .......... .......... .......... .......... .......... 99%  119K 0s
  4750K .......... .......... ...                             100% 58.7K=88s

2011-01-27 13:27:34 (54.1 KB/s) - `./adobe-flashplugin_10.1.102.65.orig.tar.gz' saved [4888067/4888067]

Download done.
Flash Plugin installed.

Setting up flashplugin-nonfree (10.1.102.65ubuntu0.10.04.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```It hasn't worked either. Suggestions?

Post relates to: [Question #143037]("https://answers.launchpad.net/ubuntu/+question/143037")

---

### Post by CaronMargarete on 2011-01-27
[Solution found!]("https://answers.launchpad.net/ubuntu/+source/flashplugin-nonfree/+question/143037")

And oh so quickly! Turned out that gnash was conflicting with Adobe flash...

---

