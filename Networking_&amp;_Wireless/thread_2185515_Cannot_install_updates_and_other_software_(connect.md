---
title: "Cannot install updates and other software (connection failed)"
date: 2013-11-03
forum: Networking &amp; Wireless
---

### Post by nisargshah on 2013-11-03
I have Ubuntu Gnome 13.10 32-bit. Whenever I try to download updates, it always fails and the update manager gives an error saying 'Failed to download updates. Check your connection'. Happened the same when I try to install new software using apt from terminal. Here's the log when I tried installing qt-sdk -

```
nisarg@nisarg-ThinkPad-T61:~$ sudo apt-get install qt-sdk
[sudo] password for nisarg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cmake cmake-data emacsen-common git git-core git-man libapr1 libaprutil1
  libbotan-1.10-0 libdrm-dev libgl1-mesa-dev libglu1-mesa-dev libkms1
  libphonon-dev libphonon4 libpthread-stubs0 libpthread-stubs0-dev
  libqt4-designer libqt4-dev libqt4-dev-bin libqt4-help libqt4-opengl
  libqt4-opengl-dev libqt4-qt3support libqt4-scripttools libqt4-svg
  libqt4-test libqt53d5 libqt5clucene5 libqt5concurrent5 libqt5core5
  libqt5dbus5 libqt5declarative5 libqt5designer5 libqt5designercomponents5
  libqt5gui5 libqt5help5 libqt5location5 libqt5network5 libqt5opengl5
  libqt5opengl5-dev libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5quickparticles5 libqt5quicktest5 libqt5script5 libqt5sensors5
  libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5v8-5 libqt5webkit5
  libqt5widgets5 libqt5xml5 libqtwebkit-dev libqtwebkit4 libserf1 libsvn1
  libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev
  libxcb-glx0-dev libxcb-icccm4 libxcb-image0 libxcb-render-util0 libxcb-sync0
  libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxxf86vm-dev mesa-common-dev phonon-backend-null qmlscene qt4-designer
  qt4-dev-tools qt4-doc qt4-doc-html qt4-linguist-tools qt4-qmake qt5-default
  qt5-qmake qtbase5-dev qtbase5-dev-tools qtcreator qtcreator-doc
  qtdeclarative5-dev subversion x11proto-core-dev x11proto-damage-dev
  x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev
  x11proto-kb-dev x11proto-xext-dev x11proto-xf86vidmode-dev
  xorg-sgml-doctools xtrans-dev
Suggested packages:
  codeblocks eclipse git-daemon-run git-daemon-sysvinit git-doc git-el
  git-email git-gui gitk gitweb git-arch git-bzr git-cvs git-svn
  libmysqlclient-dev libpq-dev libsqlite3-dev unixodbc-dev libxcb-doc
  libxext-doc libqt4-dbg libqt4-webkit-dbg libqt4-xmlpatterns-dbg
  qt-assistant-compat kdelibs5-data ubuntu-sdk qtquick1-5-dev
  qtquick1-5-dev-tools subversion-tools db5.1-util
The following NEW packages will be installed:
  cmake cmake-data emacsen-common git git-core git-man libapr1 libaprutil1
  libbotan-1.10-0 libdrm-dev libgl1-mesa-dev libglu1-mesa-dev libkms1
  libphonon-dev libphonon4 libpthread-stubs0 libpthread-stubs0-dev
  libqt4-designer libqt4-dev libqt4-dev-bin libqt4-help libqt4-opengl
  libqt4-opengl-dev libqt4-qt3support libqt4-scripttools libqt4-svg
  libqt4-test libqt53d5 libqt5clucene5 libqt5concurrent5 libqt5core5
  libqt5dbus5 libqt5declarative5 libqt5designer5 libqt5designercomponents5
  libqt5gui5 libqt5help5 libqt5location5 libqt5network5 libqt5opengl5
  libqt5opengl5-dev libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5quickparticles5 libqt5quicktest5 libqt5script5 libqt5sensors5
  libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5v8-5 libqt5webkit5
  libqt5widgets5 libqt5xml5 libqtwebkit-dev libqtwebkit4 libserf1 libsvn1
  libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev
  libxcb-glx0-dev libxcb-icccm4 libxcb-image0 libxcb-render-util0 libxcb-sync0
  libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxxf86vm-dev mesa-common-dev phonon-backend-null qmlscene qt-sdk
  qt4-designer qt4-dev-tools qt4-doc qt4-doc-html qt4-linguist-tools qt4-qmake
  qt5-default qt5-qmake qtbase5-dev qtbase5-dev-tools qtcreator qtcreator-doc
  qtdeclarative5-dev subversion x11proto-core-dev x11proto-damage-dev
  x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev
  x11proto-kb-dev x11proto-xext-dev x11proto-xf86vidmode-dev
  xorg-sgml-doctools xtrans-dev
0 upgraded, 105 newly installed, 0 to remove and 45 not upgraded.
Need to get 59.7 MB/230 MB of archives.
After this operation, 646 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://archive.ubuntu.com/ubuntu/ saucy/universe qt4-doc-html all 4:4.8.4+dfsg-0ubuntu18
  Connection failed [IP: 91.189.92.156 80]
Err http://archive.ubuntu.com/ubuntu/ saucy/universe qtcreator i386 2.7.1-0ubuntu10
  Connection failed [IP: 91.189.92.177 80]
0% [Waiting for headers]

```

My internet connection does work as I can browse the internet without any hassles. Help me how to solve this problem. Thanks in advance.

---

### Post by l.k.1234 on 2013-11-03
Can you please post you apt.conf. You find it in /etc/apt/apt.conf. Maybe you have a configuration problem.

And can you use ftp? If not you have a firewall problem.

---

### Post by nisargshah on 2013-11-03
I do not have a apt.conf file.
```
nisarg@nisarg-ThinkPad-T61:~$ cat /etc/apt/apt.conf
cat: /etc/apt/apt.conf: No such file or directory
```

I have not installed any firewall.

---

### Post by l.k.1234 on 2013-11-03
It seems like the urls apt-get is trying to download from are wrong. What happens if you do apt-get update?

---

### Post by nisargshah on 2013-11-03
Update:
Yesterday I installed **python-matplotlib** and the installation went fine. (No luck with **qt-sdk** though)
The software updates still fail to download.
*sudo apt-get update* stuck midway -
```
nisarg@nisarg-ThinkPad-T61:~$ sudo apt-get update
[sudo] password for nisarg: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security InRelease                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release    
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release [49.6 kB]                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Sources                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Sources [18.3 kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Sources [14 B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Sources [3,861 B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Sources [14 B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main i386 Packages [49.1 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]  
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe i386 Packages [18.1 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse i386 Packages [14 B] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease
100% [Waiting for headers]
```

---

