---
title: "memtest error after removing orphaned packages"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by slixz85 on 2011-06-02
memtest 86 error after i uninstalled a bunch of orphaned packages trying to free up space on my flash drive. not sure what package i uninstalled that shouldn't of.



 sudo apt-get update
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) isadora Release.gpg [198B]                 
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_US
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) isadora/main Translation-en_US              
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) isadora/upstream Translation-en_US          
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) isadora/import Translation-en_US            
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release                               
Get:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) isadora Release [7,235B]                   
Hit [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages                     
Err [http://packages.linuxmint.com](http://packages.linuxmint.com) isadora Release                              
  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/kendalltweaver/backports/ubuntu/](http://ppa.launchpad.net/kendalltweaver/backports/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://ppa.launchpad.net/kendalltweaver/peppermint/ubuntu/](http://ppa.launchpad.net/kendalltweaver/peppermint/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/shkn/xnoise/ubuntu/](http://ppa.launchpad.net/shkn/xnoise/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Fetched 7,433B in 1s (7,170B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.linuxmint.com](http://packages.linuxmint.com) isadora Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EE67F3D0FF405B2

W: Failed to fetch [http://packages.linuxmint.com/dists/isadora/Release](http://packages.linuxmint.com/dists/isadora/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
slixz@peppermint ~ $ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liba52-0.7.4 libass4 libaudio2 libavc1394-0 libavcodec52 libavformat52
  libavutil49 libcaca0 libcddb2 libdc1394-22 libdca0 libdirac-decoder0
  libdirac-encoder0 libdvbpsi5 libebml0 libenca0 libfaad2 libgsm1 libiso9660-7
  libkate1 liblircclient0 liblua5.1-0 libmad0 libmatroska0 libmodplug0c2
  libmpcdec3 libmpeg2-4 libmtp8 liboil0.3 libpostproc51 libqtcore4 libqtgui4
  libraw1394-11 libschroedinger-1.0-0 libsdl-image1.2 libshout3 libspeex1
  libswscale0 libtag1-vanilla libtag1c2a libtar libtheora0 libtwolame0
  libupnp3 libv4l-0 libvcdinfo0 libvlc5 libvlccore4 libx11-xcb1
  libxcb-keysyms1 libxcb-randr0 libxcb-shm0 libxcb-xv0 vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse
Suggested packages:
  nas lirc qt4-qtconfig libraw1394-doc speex mozilla-plugin-vlc videolan-doc
The following packages will be REMOVED:
  memtest86+
The following NEW packages will be installed:
  liba52-0.7.4 libass4 libaudio2 libavc1394-0 libavcodec52 libavformat52
  libavutil49 libcaca0 libcddb2 libdc1394-22 libdca0 libdirac-decoder0
  libdirac-encoder0 libdvbpsi5 libebml0 libenca0 libfaad2 libgsm1 libiso9660-7
  libkate1 liblircclient0 liblua5.1-0 libmad0 libmatroska0 libmodplug0c2
  libmpcdec3 libmpeg2-4 libmtp8 liboil0.3 libpostproc51 libqtcore4 libqtgui4
  libraw1394-11 libschroedinger-1.0-0 libsdl-image1.2 libshout3 libspeex1
  libswscale0 libtag1-vanilla libtag1c2a libtar libtheora0 libtwolame0
  libupnp3 libv4l-0 libvcdinfo0 libvlc5 libvlccore4 libx11-xcb1
  libxcb-keysyms1 libxcb-randr0 libxcb-shm0 libxcb-xv0 vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse
0 upgraded, 58 newly installed, 1 to remove and 58 not upgraded.
1 not fully installed or removed.
Need to get 23.0MB/29.0MB of archives.
After this operation, 82.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  liba52-0.7.4 libaudio2 libavutil49 libgsm1 liboil0.3 libschroedinger-1.0-0
  libspeex1 libtheora0 libavcodec52 libavformat52 libcaca0 libcddb2
  libdirac-decoder0 libdirac-encoder0 libdvbpsi5 libebml0 libenca0 libfaad2
  libiso9660-7 libkate1 liblua5.1-0 libmad0 libmatroska0 libmodplug0c2
  libmpcdec3 libmpeg2-4 libmtp8 libpostproc51 libqtcore4 libqtgui4
  libraw1394-11 libsdl-image1.2 libshout3 libswscale0 libtag1-vanilla
  libtag1c2a libtar libtwolame0 libv4l-0 libvcdinfo0 vlc-data libvlccore4
  libvlc5 libx11-xcb1 libxcb-randr0 libxcb-shm0 libxcb-xv0 libass4
  libavc1394-0 libdc1394-22 libdca0 liblircclient0 libupnp3 vlc-nox
  libxcb-keysyms1 vlc vlc-plugin-notify vlc-plugin-pulse
Authentication warning overridden.
Get:1 [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/) lucid/main vlc-data 1.1.4-1~lffl~lucid~ppa1 [7,780kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe liba52-0.7.4 0.7.4-13ubuntu1 [28.6kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libaudio2 1.9.2-3 [81.0kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libavutil49 4:0.5.1-1ubuntu1.1 [93.7kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libgsm1 1.0.13-3 [27.6kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main liboil0.3 0.3.16-1ubuntu2 [133kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libschroedinger-1.0-0 1.0.9.is.1.0.8-0ubuntu1 [202kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libspeex1 1.2~rc1-1ubuntu1 [112kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libtheora0 1.1.1+dfsg.1-3 [358kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libavcodec52 4:0.5.1-1ubuntu1.1 [3,999kB]
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libavformat52 4:0.5.1-1ubuntu1.1 [720kB]
Get:12 [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/) lucid/main libvlccore4 1.1.4-1~lffl~lucid~ppa1 [449kB]
Get:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libcaca0 0.99.beta16-3 [308kB]
Get:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libcddb2 1.3.2-0ubuntu1 [48.5kB]
Get:15 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libdirac-decoder0 1.0.2-2 [313kB]
Get:16 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libdirac-encoder0 1.0.2-2 [387kB]
Get:17 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libdvbpsi5 0.1.6-1 [33.9kB]
Get:18 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libebml0 0.7.7-3.1 [63.7kB]
Get:19 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libenca0 1.12-1 [67.1kB]   
Get:20 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libfaad2 2.7-4 [166kB] 
Get:21 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libiso9660-7 0.81-4 [126kB]
Get:22 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libkate1 0.3.7-3 [40.2kB]
Get:23 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libmad0 0.15.1b-4ubuntu1 [73.0kB]
Get:24 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libmatroska0 0.8.1-1.1 [196kB]
Get:25 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libmpcdec3 1:1.2.2-2.1ubuntu1 [26.5kB]
Get:26 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libmpeg2-4 0.4.1-3 [55.9kB]
Get:27 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libmtp8 1.0.2-1ubuntu1 [140kB]
Get:28 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libpostproc51 4:0.5.1-1ubuntu1.1 [190kB]
Get:29 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libqtcore4 4:4.6.2-0ubuntu5.2 [1,724kB]
Get:30 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libqtgui4 4:4.6.2-0ubuntu5.2 [4,009kB]
Get:31 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libraw1394-11 2.0.4-1ubuntu2 [44.7kB]
Get:32 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libsdl-image1.2 1.2.10-1 [32.6kB]
Get:33 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libshout3 2.2.2-5ubuntu1 [41.4kB]
Get:34 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libswscale0 4:0.5.1-1ubuntu1.1 [230kB]
Get:35 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libtag1-vanilla 1.6.3-0ubuntu1 [241kB]
Get:36 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libtag1c2a 1.6.3-0ubuntu1 [8,468B]
Get:37 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libtar 1.2.11-6 [21.7kB]
Get:38 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libtwolame0 0.3.12-1 [53.6kB]
Get:39 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libv4l-0 0.6.4-1ubuntu1 [95.0kB]
Get:40 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe libvcdinfo0 0.7.23-4ubuntu2 [130kB]
Get:41 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libavc1394-0 0.5.3-1build4 [21.4kB]
Get:42 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main liblircclient0 0.8.6-0ubuntu4.2 [88.8kB]
Fetched 23.0MB in 26s (851kB/s)                                                
Extracting templates from packages: 100%
(Reading database ... 46589 files and directories currently installed.)
Removing memtest86+ ...
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
dpkg: error processing memtest86+ (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 memtest86+
E: Sub-process /usr/bin/dpkg returned an error code (1)
slixz@peppermint ~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  memtest86+
0 upgraded, 0 newly installed, 1 to remove and 58 not upgraded.
1 not fully installed or removed.
After this operation, 467kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 46589 files and directories currently installed.)
Removing memtest86+ ...
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
dpkg: error processing memtest86+ (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 memtest86+
E: Sub-process /usr/bin/dpkg returned an error code (1)






thanks to any help

---

### Post by ohadcn on 2011-06-02
try install it insteed of removing it
(sudo apt-get install memtest86+)

do you need memtest?

---

### Post by slixz85 on 2011-06-02
sorry about that shouldn't of even posted this. i just reinstalled the os already. i was getting a bunch of strange errors. would of took too much time to find out i believe.

---

