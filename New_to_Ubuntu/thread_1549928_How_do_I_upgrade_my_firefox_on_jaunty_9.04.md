---
title: "How do I upgrade my firefox on jaunty 9.04?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Spacestationmax on 2010-08-10
How do I upgrade my firefox on jaunty 9.04

---

### Post by kr651129 on 2010-08-10
```
$>sudo apt-get upgrade firefox
```

---

### Post by snowpine on 2010-08-10
Use the Update Manager (to do a full update of your system) or the following terminal commands:

```
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by lovinglinux on 2010-08-10
What version do you have and what version you are looking for?

To update from the repositories ( current version is 3.6.8 ):

```
sudo apt-get update
sudo apt-get upgrade
```

You can also do it from "System >> Administration >> Update Manager".

---

### Post by Spacestationmax on 2010-08-10
I'm confused the mozilla that loads from my toolbar is version 3.0.13

> **lovinglinux said:**
> What version do you have and what version you are looking for?

To update from the repositories ( current version is 3.6.8 ):

```
sudo apt-get update
sudo apt-get upgrade
```

You can also do it from "System >> Administration >> Update Manager".

this is what happens
:
==================================
max@EeePC901:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://www.array.org](http://www.array.org) jaunty Release.gpg                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty Release.gpg                                     
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Translation-en_US                          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty Release                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                              
Ign [http://www.array.org](http://www.array.org) jaunty/main Translation-en_US                         
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                        
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Err [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages                                   
  403 Forbidden
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://www.array.org](http://www.array.org) jaunty Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://www.array.org](http://www.array.org) jaunty/main Packages
Hit [http://www.array.org](http://www.array.org) jaunty/main Sources
W: Failed to fetch [http://apt.boxee.tv/dists/jaunty/main/binary-i386/Packages](http://apt.boxee.tv/dists/jaunty/main/binary-i386/Packages)  403 Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.


=========================

max@EeePC901:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  adobe-flashplugin
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

==========================

---

### Post by lovinglinux on 2010-08-10
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Spacestationmax on 2010-08-10
1
File name: /usr/lib/adobe-flashplugin/libflashplayer.so
Shockwave Flash 10.0 r32

2
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.13)
Gecko/2009080315 Ubuntu/9.04 (jaunty) Firefox/3.0.13

3
 WOW! I just copy and pasted all of those commands at once and it worked like a batch file in DOS ... Linux is awesome.

===================
Ubuntu Architecture

Linux EeePC901 2.6.28-12-netbook-eeepc #43 SMP Mon Apr 27 16:06:05 MDT 2009 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Firefox Packages

firefox						install
firefox-3.0					install
firefox-3.0-branding				install
firefox-3.0-gnome-support			install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `firefox-3.0'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

array-jaunty.list
array-jaunty.list.save

Flash packages

adobe-flashplugin				install
flashplugin-installer				install

Plugin locations

/usr/lib/adobe-flashplugin/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by Elfy on 2010-08-10
off topic posts removed

---

### Post by lovinglinux on 2010-08-10
> **Spacestationmax said:**
> 1
File name: /usr/lib/adobe-flashplugin/libflashplayer.so
Shockwave Flash 10.0 r32

2
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.13)
Gecko/2009080315 Ubuntu/9.04 (jaunty) Firefox/3.0.13

3
 WOW! I just copy and pasted all of those commands at once and it worked like a batch file in DOS ... Linux is awesome.


Run the following commands. They will remove firefox and adobe-flashplugin (you have two flash plugins installed), then update your system and install firefox and flash again, this time the correct versions.

```
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-installer
sudo apt-get purge firefox
sudo apt-get purge firefox-3.0
sudo rm -f /var/cache/apt/archives/firefox*
sudo apt-get update
sudo apt-get install firefox
sudo apt-get install flashplugin-installer
sudo apt-get upgrade
```

Please let me know if you get the correct versions.

---

### Post by Spacestationmax on 2010-08-10
Result:

==========================
max@EeePC901:~$ sudo apt-get purge adobe-flashplugin
[sudo] password for max: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flashplugin*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 10.4MB disk space will be freed.
Do you want to continue [Y/n]? y
Y
(Reading database ... 154805 files and directories currently installed.)
Removing adobe-flashplugin ...
==============================

Now what?

---

### Post by Spacestationmax on 2010-08-10
> **Spacestationmax said:**
> 

Now what?
I guess it only did that first command... will continue were I left off

---

### Post by lovinglinux on 2010-08-10
> **Spacestationmax said:**
> Result:

==========================
max@EeePC901:~$ sudo apt-get purge adobe-flashplugin
[sudo] password for max: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flashplugin*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 10.4MB disk space will be freed.
Do you want to continue [Y/n]? y
Y
(Reading database ... 154805 files and directories currently installed.)
Removing adobe-flashplugin ...
==============================

Now what?

You have executed only the first command. Run the rest too.

---

### Post by Spacestationmax on 2010-08-10
max@EeePC901:~$ sudo apt-get install flashplugin-installer
[sudo] password for max: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.2kB of archives.
After this operation, 180kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse flashplugin-installer 10.0.22.87ubuntu2 [19.2kB]
Fetched 19.2kB in 0s (39.0kB/s)            
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 154753 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.0.22.87ubuntu2_i386.deb) ...
Setting up flashplugin-installer (10.0.22.87ubuntu2) ...
Downloading...
--2010-08-10 19:32:31--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87.orig.tar.gz)
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3968445 (3.8M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.0.22.87.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1%  141K 27s
    50K .......... .......... .......... .......... ..........  2%  461K 17s
   100K .......... .......... .......... .......... ..........  3%  573K 14s
   150K .......... .......... .......... .......... ..........  5%  768K 11s
   200K .......... .......... .......... .......... ..........  6%  989K 10s
   250K .......... .......... .......... .......... ..........  7%  747K 9s
   300K .......... .......... .......... .......... ..........  9% 1.53M 8s
   350K .......... .......... .......... .......... .......... 10% 1.08M 7s
   400K .......... .......... .......... .......... .......... 11%  996K 7s
   450K .......... .......... .......... .......... .......... 12% 1.34M 6s
   500K .......... .......... .......... .......... .......... 14% 1.18M 6s
   550K .......... .......... .......... .......... .......... 15% 1.56M 5s
   600K .......... .......... .......... .......... .......... 16% 1.69M 5s
   650K .......... .......... .......... .......... .......... 18%  945K 5s
   700K .......... .......... .......... .......... .......... 19% 1.11M 5s
   750K .......... .......... .......... .......... .......... 20% 1.31M 4s
   800K .......... .......... .......... .......... .......... 21% 1.46M 4s
   850K .......... .......... .......... .......... .......... 23% 1.56M 4s
   900K .......... .......... .......... .......... .......... 24% 1.86M 4s
   950K .......... .......... .......... .......... .......... 25% 1.54M 4s
  1000K .......... .......... .......... .......... .......... 27% 1.58M 3s
  1050K .......... .......... .......... .......... .......... 28% 1.52M 3s
  1100K .......... .......... .......... .......... .......... 29% 1.69M 3s
  1150K .......... .......... .......... .......... .......... 30% 1.87M 3s
  1200K .......... .......... .......... .......... .......... 32% 1.54M 3s
  1250K .......... .......... .......... .......... .......... 33%  982K 3s
  1300K .......... .......... .......... .......... .......... 34% 1.87M 3s
  1350K .......... .......... .......... .......... .......... 36% 1.48M 3s
  1400K .......... .......... .......... .......... .......... 37%  255K 3s
  1450K .......... .......... .......... .......... .......... 38% 18.3M 3s
  1500K .......... .......... .......... .......... .......... 39% 16.4M 3s
  1550K .......... .......... .......... .......... .......... 41% 18.8M 2s
  1600K .......... .......... .......... .......... .......... 42% 17.0M 2s
  1650K .......... .......... .......... .......... .......... 43% 16.0M 2s
  1700K .......... .......... .......... .......... .......... 45% 17.6M 2s
  1750K .......... .......... .......... .......... .......... 46% 1.30M 2s
  1800K .......... .......... .......... .......... .......... 47%  260K 2s
  1850K .......... .......... .......... .......... .......... 49%  484K 2s
  1900K .......... .......... .......... .......... .......... 50%  547K 2s
  1950K .......... .......... .......... .......... .......... 51%  618K 2s
  2000K .......... .......... .......... .......... .......... 52%  857K 2s
  2050K .......... .......... .......... .......... .......... 54%  815K 2s
  2100K .......... .......... .......... .......... .......... 55% 1022K 2s
  2150K .......... .......... .......... .......... .......... 56% 1.01M 2s
  2200K .......... .......... .......... .......... .......... 58% 1.16M 2s
  2250K .......... .......... .......... .......... .......... 59% 1.29M 2s
  2300K .......... .......... .......... .......... .......... 60% 1021K 2s
  2350K .......... .......... .......... .......... .......... 61% 1.66M 2s
  2400K .......... .......... .......... .......... .......... 63% 1.87M 2s
  2450K .......... .......... .......... .......... .......... 64% 1.72M 1s
  2500K .......... .......... .......... .......... .......... 65% 1.35M 1s
  2550K .......... .......... .......... .......... .......... 67% 1.17M 1s
  2600K .......... .......... .......... .......... .......... 68% 1.94M 1s
  2650K .......... .......... .......... .......... .......... 69% 1.62M 1s
  2700K .......... .......... .......... .......... .......... 70% 1.43M 1s
  2750K .......... .......... .......... .......... .......... 72% 1.70M 1s
  2800K .......... .......... .......... .......... .......... 73% 1.16M 1s
  2850K .......... .......... .......... .......... .......... 74% 1.01M 1s
  2900K .......... .......... .......... .......... .......... 76% 1.30M 1s
  2950K .......... .......... .......... .......... .......... 77% 1.49M 1s
  3000K .......... .......... .......... .......... .......... 78% 1.31M 1s
  3050K .......... .......... .......... .......... .......... 79% 1.17M 1s
  3100K .......... .......... .......... .......... .......... 81%  996K 1s
  3150K .......... .......... .......... .......... .......... 82% 1.58M 1s
  3200K .......... .......... .......... .......... .......... 83% 1.25M 1s
  3250K .......... .......... .......... .......... .......... 85% 1.19M 1s
  3300K .......... .......... .......... .......... .......... 86%  987K 1s
  3350K .......... .......... .......... .......... .......... 87% 1.62M 0s
  3400K .......... .......... .......... .......... .......... 89% 1.69M 0s
  3450K .......... .......... .......... .......... .......... 90% 1.17M 0s
  3500K .......... .......... .......... .......... .......... 91%  853K 0s
  3550K .......... .......... .......... .......... .......... 92% 1.17M 0s
  3600K .......... .......... .......... .......... .......... 94% 1.08M 0s
  3650K .......... .......... .......... .......... .......... 95% 1.52M 0s
  3700K .......... .......... .......... .......... .......... 96% 1009K 0s
  3750K .......... .......... .......... .......... .......... 98% 1.28M 0s
  3800K .......... .......... .......... .......... .......... 99% 1.25M 0s
  3850K .......... .......... .....                           100% 1.31M=3.7s

2010-08-10 19:32:35 (1.01 MB/s) - `./adobe-flashplugin_10.0.22.87.orig.tar.gz' saved [3968445/3968445]

Download done.
Flash Plugin installed.


max@EeePC901:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
max@EeePC901:~$ 

===========================
So is that it?
Again thanks so much for the help

---

### Post by lovinglinux on 2010-08-10
> **Spacestationmax said:**
> max@EeePC901:~$ sudo apt-get install flashplugin-installer
[sudo] password for max: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.2kB of archives.
After this operation, 180kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse flashplugin-installer 10.0.22.87ubuntu2 [19.2kB]
Fetched 19.2kB in 0s (39.0kB/s)            
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 154753 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.0.22.87ubuntu2_i386.deb) ...
Setting up flashplugin-installer (10.0.22.87ubuntu2) ...
Downloading...
--2010-08-10 19:32:31--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87.orig.tar.gz)
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3968445 (3.8M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.0.22.87.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1%  141K 27s
    50K .......... .......... .......... .......... ..........  2%  461K 17s
   100K .......... .......... .......... .......... ..........  3%  573K 14s
   150K .......... .......... .......... .......... ..........  5%  768K 11s
   200K .......... .......... .......... .......... ..........  6%  989K 10s
   250K .......... .......... .......... .......... ..........  7%  747K 9s
   300K .......... .......... .......... .......... ..........  9% 1.53M 8s
   350K .......... .......... .......... .......... .......... 10% 1.08M 7s
   400K .......... .......... .......... .......... .......... 11%  996K 7s
   450K .......... .......... .......... .......... .......... 12% 1.34M 6s
   500K .......... .......... .......... .......... .......... 14% 1.18M 6s
   550K .......... .......... .......... .......... .......... 15% 1.56M 5s
   600K .......... .......... .......... .......... .......... 16% 1.69M 5s
   650K .......... .......... .......... .......... .......... 18%  945K 5s
   700K .......... .......... .......... .......... .......... 19% 1.11M 5s
   750K .......... .......... .......... .......... .......... 20% 1.31M 4s
   800K .......... .......... .......... .......... .......... 21% 1.46M 4s
   850K .......... .......... .......... .......... .......... 23% 1.56M 4s
   900K .......... .......... .......... .......... .......... 24% 1.86M 4s
   950K .......... .......... .......... .......... .......... 25% 1.54M 4s
  1000K .......... .......... .......... .......... .......... 27% 1.58M 3s
  1050K .......... .......... .......... .......... .......... 28% 1.52M 3s
  1100K .......... .......... .......... .......... .......... 29% 1.69M 3s
  1150K .......... .......... .......... .......... .......... 30% 1.87M 3s
  1200K .......... .......... .......... .......... .......... 32% 1.54M 3s
  1250K .......... .......... .......... .......... .......... 33%  982K 3s
  1300K .......... .......... .......... .......... .......... 34% 1.87M 3s
  1350K .......... .......... .......... .......... .......... 36% 1.48M 3s
  1400K .......... .......... .......... .......... .......... 37%  255K 3s
  1450K .......... .......... .......... .......... .......... 38% 18.3M 3s
  1500K .......... .......... .......... .......... .......... 39% 16.4M 3s
  1550K .......... .......... .......... .......... .......... 41% 18.8M 2s
  1600K .......... .......... .......... .......... .......... 42% 17.0M 2s
  1650K .......... .......... .......... .......... .......... 43% 16.0M 2s
  1700K .......... .......... .......... .......... .......... 45% 17.6M 2s
  1750K .......... .......... .......... .......... .......... 46% 1.30M 2s
  1800K .......... .......... .......... .......... .......... 47%  260K 2s
  1850K .......... .......... .......... .......... .......... 49%  484K 2s
  1900K .......... .......... .......... .......... .......... 50%  547K 2s
  1950K .......... .......... .......... .......... .......... 51%  618K 2s
  2000K .......... .......... .......... .......... .......... 52%  857K 2s
  2050K .......... .......... .......... .......... .......... 54%  815K 2s
  2100K .......... .......... .......... .......... .......... 55% 1022K 2s
  2150K .......... .......... .......... .......... .......... 56% 1.01M 2s
  2200K .......... .......... .......... .......... .......... 58% 1.16M 2s
  2250K .......... .......... .......... .......... .......... 59% 1.29M 2s
  2300K .......... .......... .......... .......... .......... 60% 1021K 2s
  2350K .......... .......... .......... .......... .......... 61% 1.66M 2s
  2400K .......... .......... .......... .......... .......... 63% 1.87M 2s
  2450K .......... .......... .......... .......... .......... 64% 1.72M 1s
  2500K .......... .......... .......... .......... .......... 65% 1.35M 1s
  2550K .......... .......... .......... .......... .......... 67% 1.17M 1s
  2600K .......... .......... .......... .......... .......... 68% 1.94M 1s
  2650K .......... .......... .......... .......... .......... 69% 1.62M 1s
  2700K .......... .......... .......... .......... .......... 70% 1.43M 1s
  2750K .......... .......... .......... .......... .......... 72% 1.70M 1s
  2800K .......... .......... .......... .......... .......... 73% 1.16M 1s
  2850K .......... .......... .......... .......... .......... 74% 1.01M 1s
  2900K .......... .......... .......... .......... .......... 76% 1.30M 1s
  2950K .......... .......... .......... .......... .......... 77% 1.49M 1s
  3000K .......... .......... .......... .......... .......... 78% 1.31M 1s
  3050K .......... .......... .......... .......... .......... 79% 1.17M 1s
  3100K .......... .......... .......... .......... .......... 81%  996K 1s
  3150K .......... .......... .......... .......... .......... 82% 1.58M 1s
  3200K .......... .......... .......... .......... .......... 83% 1.25M 1s
  3250K .......... .......... .......... .......... .......... 85% 1.19M 1s
  3300K .......... .......... .......... .......... .......... 86%  987K 1s
  3350K .......... .......... .......... .......... .......... 87% 1.62M 0s
  3400K .......... .......... .......... .......... .......... 89% 1.69M 0s
  3450K .......... .......... .......... .......... .......... 90% 1.17M 0s
  3500K .......... .......... .......... .......... .......... 91%  853K 0s
  3550K .......... .......... .......... .......... .......... 92% 1.17M 0s
  3600K .......... .......... .......... .......... .......... 94% 1.08M 0s
  3650K .......... .......... .......... .......... .......... 95% 1.52M 0s
  3700K .......... .......... .......... .......... .......... 96% 1009K 0s
  3750K .......... .......... .......... .......... .......... 98% 1.28M 0s
  3800K .......... .......... .......... .......... .......... 99% 1.25M 0s
  3850K .......... .......... .....                           100% 1.31M=3.7s

2010-08-10 19:32:35 (1.01 MB/s) - `./adobe-flashplugin_10.0.22.87.orig.tar.gz' saved [3968445/3968445]

Download done.
Flash Plugin installed.


max@EeePC901:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
max@EeePC901:~$ 

===========================
So is that it?
Again thanks so much for the help

Unless you haven't posted all the output of the terminal, you are still skipping commands. Please copy one line from the command list and execute it, then copy the next one and execute it, until have executed all commands I suggested.

---

### Post by Spacestationmax on 2010-08-10
=====================
oops dont know what happened there... here we go again
====================

1 sudo apt-get purge adobe-flashplugin 
2 sudo apt-get purge flashplugin-installer
3 sudo apt-get purge firefox
4 sudo apt-get purge firefox-3.0
5 sudo rm -f /var/cache/apt/archives/firefox*
6 sudo apt-get update
7 sudo apt-get install firefox
8 sudo apt-get install flashplugin-installer
9 sudo apt-get upgrade

===========================
1

max@EeePC901:~$ sudo apt-get purge adobe-flashplugin
[sudo] password for max: 6 sudo apt-get update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
max@EeePC901:~$ 

======================
2

max@EeePC901:~$ sudo apt-get purge flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
max@EeePC901:~$ 

===================
3

max@EeePC901:~$ sudo apt-get purge firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firefox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 154752 files and directories currently installed.)
Removing firefox ...
max@EeePC901:~$ 

=====================================
4

max@EeePC901:~$ sudo apt-get purge firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firefox-3.0* firefox-3.0-branding*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 3875kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 154749 files and directories currently installed.)
Removing firefox-3.0 ...
Purging configuration files for firefox-3.0 ...
Removing firefox-3.0-branding ...
Processing triggers for menu ...
max@EeePC901:~$ 

======================================
5

max@EeePC901:~$ sudo rm -f /var/cache/apt/archives/firefox*

======================================
6

max@EeePC901:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Get:1 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [189B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://www.array.org](http://www.array.org) jaunty Release.gpg                                    
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty Release.gpg                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Translation-en_US                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Get:2 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release [10.5kB]                     
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty Release                                         
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Ign [http://www.array.org](http://www.array.org) jaunty/main Translation-en_US                         
Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                              
Err [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages                                   
  403 Forbidden
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                        
Get:3 [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages [4167B]   
Hit [http://www.array.org](http://www.array.org) jaunty Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources         
Get:4 [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources [1732B]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages           
Hit [http://www.array.org](http://www.array.org) jaunty/main Packages                         
Hit [http://www.array.org](http://www.array.org) jaunty/main Sources
Fetched 16.6kB in 2s (5852B/s)
W: Failed to fetch [http://apt.boxee.tv/dists/jaunty/main/binary-i386/Packages](http://apt.boxee.tv/dists/jaunty/main/binary-i386/Packages)  403 Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.
max@EeePC901:~$ 

======================================
7

max@EeePC901:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-3.0 firefox-3.0-branding
Suggested packages:
  ubufox firefox-3.0-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  firefox firefox-3.0 firefox-3.0-branding
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1158kB of archives.
After this operation, 4002kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main firefox-3.0-branding 3.0.8+nobinonly-0ubuntu3 [202kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main firefox-3.0 3.0.8+nobinonly-0ubuntu3 [887kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main firefox 3.0.8+nobinonly-0ubuntu3 [69.1kB]
Fetched 1158kB in 2s (535kB/s)
Selecting previously deselected package firefox-3.0-branding.
(Reading database ... 154637 files and directories currently installed.)
Unpacking firefox-3.0-branding (from .../firefox-3.0-branding_3.0.8+nobinonly-0ubuntu3_i386.deb) ...
Selecting previously deselected package firefox-3.0.
Unpacking firefox-3.0 (from .../firefox-3.0_3.0.8+nobinonly-0ubuntu3_i386.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.0.8+nobinonly-0ubuntu3_all.deb) ...
Processing triggers for menu ...
Setting up firefox-3.0-branding (3.0.8+nobinonly-0ubuntu3) ...
Setting up firefox-3.0 (3.0.8+nobinonly-0ubuntu3) ...
Please restart all running instances of firefox-3.0, or you will experience problems.

Setting up firefox (3.0.8+nobinonly-0ubuntu3) ...
max@EeePC901:~$ 

================================
8

max@EeePC901:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core liblzo1 gstreamer0.10-plugins-ugly
  linux-headers-2.6.28-11 libsdl-gfx1.2-4 comerr-dev libxmlrpc-c3 python-pyogg
  libkrb5-dev python2.4-minimal python2.4 libnss3-dev libldap2-dev libtre4
  python-serial python-ogg python-pam python-openssl python-editobj
  libsdl-sound1.2 gstreamer0.10-ffmpeg libcurl3
  linux-headers-2.6.28-11-generic libssl-dev libmozjs-dev python-pyopenssl
  libnspr4-dev zlib1g-dev libcal3d12 libswfdec-0.8-0 python-sqlite libmozjs0d
  libsidplay1 libkadm55 libfaad-dev xsel libode0debian1 python-twisted-bin
  libidn11-dev libcurl4-openssl-dev libfaac0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.2kB of archives.
After this operation, 180kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 154753 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.0.22.87ubuntu2_i386.deb) ...
Setting up flashplugin-installer (10.0.22.87ubuntu2) ...
Downloading...
--2010-08-10 22:13:54--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87.orig.tar.gz)
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3968445 (3.8M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.0.22.87.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1%  120K 32s
    50K .......... .......... .......... .......... ..........  2%  440K 20s
   100K .......... .......... .......... .......... ..........  3%  403K 16s
   150K .......... .......... .......... .......... ..........  5%  588K 14s
   200K .......... .......... .......... .......... ..........  6%  816K 12s
   250K .......... .......... .......... .......... ..........  7%  568K 11s
   300K .......... .......... .......... .......... ..........  9% 1.09M 9s
   350K .......... .......... .......... .......... .......... 10%  660K 9s
   400K .......... .......... .......... .......... .......... 11% 1.21M 8s
   450K .......... .......... .......... .......... .......... 12%  912K 7s
   500K .......... .......... .......... .......... .......... 14% 1.12M 7s
   550K .......... .......... .......... .......... .......... 15% 1.28M 6s
   600K .......... .......... .......... .......... .......... 16% 1.23M 6s
   650K .......... .......... .......... .......... .......... 18% 1.09M 6s
   700K .......... .......... .......... .......... .......... 19%  775K 6s
   750K .......... .......... .......... .......... .......... 20% 1.26M 5s
   800K .......... .......... .......... .......... .......... 21% 1.62M 5s
   850K .......... .......... .......... .......... .......... 23% 1006K 5s
   900K .......... .......... .......... .......... .......... 24% 1.14M 5s
   950K .......... .......... .......... .......... .......... 25% 1.11M 4s
  1000K .......... .......... .......... .......... .......... 27% 1.64M 4s
  1050K .......... .......... .......... .......... .......... 28% 1.57M 4s
  1100K .......... .......... .......... .......... .......... 29% 1.03M 4s
  1150K .......... .......... .......... .......... .......... 30% 1.08M 4s
  1200K .......... .......... .......... .......... .......... 32% 1.50M 4s
  1250K .......... .......... .......... .......... .......... 33% 1.33M 3s
  1300K .......... .......... .......... .......... .......... 34% 1.75M 3s
  1350K .......... .......... .......... .......... .......... 36% 1.81M 3s
  1400K .......... .......... .......... .......... .......... 37% 1.25M 3s
  1450K .......... .......... .......... .......... .......... 38% 1.11M 3s
  1500K .......... .......... .......... .......... .......... 39% 1.47M 3s
  1550K .......... .......... .......... .......... .......... 41% 1.63M 3s
  1600K .......... .......... .......... .......... .......... 42% 1.51M 3s
  1650K .......... .......... .......... .......... .......... 43% 2.02M 3s
  1700K .......... .......... .......... .......... .......... 45% 1.50M 2s
  1750K .......... .......... .......... .......... .......... 46% 1.34M 2s
  1800K .......... .......... .......... .......... .......... 47% 1.72M 2s
  1850K .......... .......... .......... .......... .......... 49% 1.75M 2s
  1900K .......... .......... .......... .......... .......... 50% 1.79M 2s
  1950K .......... .......... .......... .......... .......... 51% 1.84M 2s
  2000K .......... .......... .......... .......... .......... 52% 2.15M 2s
  2050K .......... .......... .......... .......... .......... 54% 1.36M 2s
  2100K .......... .......... .......... .......... .......... 55% 2.02M 2s
  2150K .......... .......... .......... .......... .......... 56% 1.27M 2s
  2200K .......... .......... .......... .......... .......... 58% 2.28M 2s
  2250K .......... .......... .......... .......... .......... 59% 2.25M 2s
  2300K .......... .......... .......... .......... .......... 60% 2.21M 2s
  2350K .......... .......... .......... .......... .......... 61% 2.00M 1s
  2400K .......... .......... .......... .......... .......... 63% 2.22M 1s
  2450K .......... .......... .......... .......... .......... 64% 2.06M 1s
  2500K .......... .......... .......... .......... .......... 65% 2.21M 1s
  2550K .......... .......... .......... .......... .......... 67% 1.85M 1s
  2600K .......... .......... .......... .......... .......... 68% 1.89M 1s
  2650K .......... .......... .......... .......... .......... 69% 1.84M 1s
  2700K .......... .......... .......... .......... .......... 70% 2.63M 1s
  2750K .......... .......... .......... .......... .......... 72% 1.44M 1s
  2800K .......... .......... .......... .......... .......... 73% 1.43M 1s
  2850K .......... .......... .......... .......... .......... 74% 1.89M 1s
  2900K .......... .......... .......... .......... .......... 76% 2.18M 1s
  2950K .......... .......... .......... .......... .......... 77% 1.77M 1s
  3000K .......... .......... .......... .......... .......... 78% 1.97M 1s
  3050K .......... .......... .......... .......... .......... 79% 1.89M 1s
  3100K .......... .......... .......... .......... .......... 81% 2.13M 1s
  3150K .......... .......... .......... .......... .......... 82%  142K 1s
  3200K .......... .......... .......... .......... .......... 83% 6.68M 1s
  3250K .......... .......... .......... .......... .......... 85% 18.7M 1s
  3300K .......... .......... .......... .......... .......... 86% 13.9M 0s
  3350K .......... .......... .......... .......... .......... 87% 15.7M 0s
  3400K .......... .......... .......... .......... .......... 89% 5.94M 0s
  3450K .......... .......... .......... .......... .......... 90% 5.83M 0s
  3500K .......... .......... .......... .......... .......... 91% 6.34M 0s
  3550K .......... .......... .......... .......... .......... 92% 6.29M 0s
  3600K .......... .......... .......... .......... .......... 94% 7.68M 0s
  3650K .......... .......... .......... .......... .......... 95% 21.2M 0s
  3700K .......... .......... .......... .......... .......... 96% 20.5M 0s
  3750K .......... .......... .......... .......... .......... 98%  914K 0s
  3800K .......... .......... .......... .......... .......... 99%  137K 0s
  3850K .......... .......... .....                           100%  233K=3.7s

2010-08-10 22:14:03 (1.01 MB/s) - `./adobe-flashplugin_10.0.22.87.orig.tar.gz' saved [3968445/3968445]

Download done.
Flash Plugin installed.

max@EeePC901:~$ 

=================================
9

max@EeePC901:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
max@EeePC901:~$ 
===================================

Ok...

===================================

Shockwave Flash

    File name: /usr/lib/flashplugin-installer/libflashplayer.so
    Shockwave Flash 10.0 r22

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.13) Gecko/2009080315 Ubuntu/9.04 (jaunty) Firefox/3.0.8

====================================
Ubuntu Architecture

Linux EeePC901 2.6.28-12-netbook-eeepc #43 SMP Mon Apr 27 16:06:05 MDT 2009 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Firefox Packages

firefox						install
firefox-3.0					install
firefox-3.0-branding				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `firefox-3.0'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

array-jaunty.list
array-jaunty.list.save

Flash packages

flashplugin-installer				install

Plugin locations


/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

====================

Hmmm what do you think???

---

### Post by lovinglinux on 2010-08-10
> **Spacestationmax said:**
> Hmmm what do you think???

Everything went OK. The only problem is that it doesn't want to update to the latest version of Firefox.

Anyway, the following will fix this issue:

```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
```

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

```
sudo apt-get update
```

```
sudo apt-get install firefox-mozilla-build
```

This will install Firefox 3.6.8 from Ubuntuzilla repository.

---

### Post by Spacestationmax on 2010-08-10
Great!

The welcome page is advising me to update Flash...

How do I get Flash Player 10.1 on here about:plugins says I have     

File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r22

---

### Post by Spacestationmax on 2010-08-10
By the way I'm watching Battlestar G right now.  Oh it just ended, now its "Unsolved Mysteries".... I would be on that show if it wasn't for you and Ubuntu Forums!

---

### Post by lovinglinux on 2010-08-11
> **Spacestationmax said:**
> Great!

The welcome page is advising me to update Flash...

How do I get Flash Player 10.1 on here about:plugins says I have     

File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r22

Get the [deb file from Adobe]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10.1_for_Linux_(.deb)").

Just to be safe, uninstall the current version first.

```
sudo apt-get purge flashplugin-installer
```

---

### Post by Spacestationmax on 2010-08-11
sudo apt-get purge flashplugin-installer

I lose what a windows user would call the contents of my clipboard, or the tid bit of info I copied when I quit firefox.
Its kind of a pain sometimes.

max@EeePC901:~$ sudo apt-get purge flashplugin-installer
[sudo] password for max: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package flashplugin-installer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
max@EeePC901:~$ 

then I clicked the deb file and Package Installer said: 
Error: A later version is already installed 
Detail Tab shows version 10.1.82.76-1

about:plugins in firefox:
    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r22

Good Morning

Lovinglinux you have been very helpful I'm opening a new thread 
[here]("http://ubuntuforums.org/showthread.php?p=9707270#post9707270")

---

### Post by lovinglinux on 2010-08-11
> **Spacestationmax said:**
> sudo apt-get purge flashplugin-installer

I lose what a windows user would call the contents of my clipboard, or the tid bit of info I copied when I quit firefox.
Its kind of a pain sometimes.

max@EeePC901:~$ sudo apt-get purge flashplugin-installer
[sudo] password for max: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package flashplugin-installer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
max@EeePC901:~$ 

then I clicked the deb file and Package Installer said: 
Error: A later version is already installed 
Detail Tab shows version 10.1.82.76-1

about:plugins in firefox:
    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r22

Good Morning

Lovinglinux you have been very helpful I'm opening a new thread 
[here]("http://ubuntuforums.org/showthread.php?p=9707270#post9707270")

```
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-installer
sudo apt-get purge flashplugin-nonfree

```

then execute the deb file to install the latest version.

---

### Post by Spacestationmax on 2010-08-11
Shockwave Flash

    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r82

Thanks you are very tallented

---

### Post by oldsoundguy on 2010-08-11
From what I saw in the past, the repositories will not have the latest version if you are using anything prior to 10.04.  That's just the way they do things. (it may have changed .. BUT):

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

for older Ubuntu versions.  Allows upgrading of everything Mozilla for use on older releases.

---

### Post by snowpine on 2010-08-11
> **oldsoundguy said:**
> From what I saw in the past, the repositories will not have the latest version if you are using anything prior to 10.04.  That's just the way they do things. (it may have changed .. BUT):

It has changed; Ubuntu now "backports" new Firefox to older supported releases, due to Mozilla discontinuing support for 3.0.

---

### Post by lovinglinux on 2010-08-11
> **Spacestationmax said:**
> Shockwave Flash

    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r82

Thanks you are very tallented

I'm glad to help. BTW, you got the latest version released today, which is supposed to fix a (another) critical vulnerability.

---

