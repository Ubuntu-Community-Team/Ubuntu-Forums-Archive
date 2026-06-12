---
title: "Don't understand what is said in my terminal?"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by DayLite on 2011-05-05
I pasted in the terminal to install openshot. I don't understand the reason given why it cannot be installed or how to fix it:confused:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openshot : Depends: melt but it is not going to be installed
            Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable
            Depends: python-pygoocanvas but it is not going to be installed
E: Broken packages

```

---

### Post by K_45 on 2011-05-05
```
sudo apt-get install -f
```

Something is broken somewhere . . .

---

### Post by DayLite on 2011-05-05
> **K_45 said:**
> ```
sudo apt-get install -f
```Something is broken somewhere . . .
Now, what do I do?

```
joan@joan-desktop:~$ sudo apt-get install -f
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-utils libdbus-glib1.0-cil librsvg2-2.18-cil
  cairo-dock-plug-ins-integration libicns1 python-numeric libpng12-dev
  python-utidylib python-mpd libtidy-0.99-0 python-tz xulrunner-2.0-mozjs
  python-feedparser python-rsvg python-dateutil libwnck2.20-cil
  libswfdec-0.8-0 dockmanager python-wxversion python-evolution libpodofo0.8.0
  python-wxgtk2.8 libdbus1.0-cil cairo-dock-plug-ins-data libetpan13
  libgnomedesktop2.20-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
joan@joan-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
joan@joan-desktop:~$ y
y: command not found
joan@joan-desktop:~$ 

```

---

### Post by sadaruwan12 on 2011-05-05
> **DayLite said:**
> Now, what do I do?

```
joan@joan-desktop:~$ sudo apt-get install -f
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-utils libdbus-glib1.0-cil librsvg2-2.18-cil
  cairo-dock-plug-ins-integration libicns1 python-numeric libpng12-dev
  python-utidylib python-mpd libtidy-0.99-0 python-tz xulrunner-2.0-mozjs
  python-feedparser python-rsvg python-dateutil libwnck2.20-cil
  libswfdec-0.8-0 dockmanager python-wxversion python-evolution libpodofo0.8.0
  python-wxgtk2.8 libdbus1.0-cil cairo-dock-plug-ins-data libetpan13
  libgnomedesktop2.20-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
joan@joan-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
joan@joan-desktop:~$ y
y: command not found
joan@joan-desktop:~$ 

```

Bro it seems like you don't know much about the terminal usage any way use these commands and see.

Code:
```
sudo apt-get autoremove
```

This will remove those residual packages in your system after that use this command below to find out if any dependencies are broken.

Code:
```
sudo apt-get check openshot
```

If not run the below command to install your package openshot

Code:
```
sudo apt-get install openshot
```

If it shows any broken dependencies run the command below.

Code:
```
sudo apt-get install -f openshot
```

Please tell what happened after doing these steps.

And use these links to get some knowledge on the terminal as Linux user you must have good understanding on how the terminal works and how to use the commands correctly hope this helps.

[Book 1]("https://help.ubuntu.com/community/UsingTheTerminal")
[Book 2]("http://beginlinux.com/twitter/1094-the-beginners-guide-to-the-ubuntu-terminal")

---

### Post by DayLite on 2011-05-05
> **sadaruwan12 said:**
> Bro it seems like you don't know much about the terminal usage any way use these commands and see.

Code:
```
sudo apt-get autoremove
```This will remove those residual packages in your system after that use this command below to find out if any dependencies are broken.

Code:
```
sudo apt-get check openshot
```If not run the below command to install your package openshot

Code:
```
sudo apt-get install openshot
```If it shows any broken dependencies run the command below.

Code:
```
sudo apt-get install -f openshot
```Please tell what happened after doing these steps.

[]("http://beginlinux.com/twitter/1094-the-beginners-guide-to-the-ubuntu-terminal")

Now what do I do? This was what was written in my terminal:

```
joan@joan-desktop:~$ sudo apt-get autoremove
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cairo-dock-plug-ins-data cairo-dock-plug-ins-integration dockmanager
  libdbus-glib1.0-cil libdbus1.0-cil libetpan13 libgnomedesktop2.20-cil
  libicns1 libpng12-dev libpodofo0.8.0 librsvg2-2.18-cil libswfdec-0.8-0
  libtidy-0.99-0 libwnck2.20-cil mesa-utils python-dateutil python-evolution
  python-feedparser python-mpd python-numeric python-rsvg python-tz
  python-utidylib python-wxgtk2.8 python-wxversion xulrunner-2.0-mozjs
0 upgraded, 0 newly installed, 26 to remove and 62 not upgraded.
After this operation, 65.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 210667 files and directories currently installed.)
Removing cairo-dock-plug-ins-integration ...
Removing cairo-dock-plug-ins-data ...
Removing dockmanager ...
Removing libdbus-glib1.0-cil ...
Removing libdbus-glib1.0-cil from Mono
Removing libdbus1.0-cil ...
Removing libdbus1.0-cil from Mono
Removing libetpan13 ...
Removing libgnomedesktop2.20-cil ...
Removing libgnomedesktop2.20-cil from Mono
Removing libicns1 ...
Removing libpng12-dev ...
Removing libpodofo0.8.0 ...
Removing librsvg2-2.18-cil ...
Removing librsvg2-2.18-cil from Mono
Removing libswfdec-0.8-0 ...
Removing python-utidylib ...
Removing libtidy-0.99-0 ...
Removing libwnck2.20-cil ...
Removing libwnck2.20-cil from Mono
Removing mesa-utils ...
Removing python-dateutil ...
Removing python-evolution ...
Removing python-feedparser ...
Removing python-mpd ...
Removing python-numeric ...
Removing python-rsvg ...
Removing python-tz ...
Removing xulrunner-2.0-mozjs ...
Removing python-wxversion ...
Removing python-wxgtk2.8 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...
joan@joan-desktop:~$ 
joan@joan-desktop:~$ sudo apt-get check openshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
joan@joan-desktop:~$ sudo apt-get install openshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openshot : Depends: melt but it is not going to be installed
            Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable
            Depends: python-pygoocanvas but it is not going to be installed
E: Broken packages
joan@joan-desktop:~$ sudo apt-get install -f openshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openshot : Depends: melt but it is not going to be installed
            Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable
            Depends: python-pygoocanvas but it is not going to be installed
E: Broken packages
joan@joan-desktop:~$ sudo apt-get install -f openshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openshot : Depends: melt but it is not going to be installed
            Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable
            Depends: python-pygoocanvas but it is not going to be installed
E: Broken packages
joan@joan-desktop:~$ 

```

---

### Post by DayLite on 2011-05-05
While I am awaiting your reply, I went to the Ubuntu Software Center and attempted to install OpenShot. This is the detail why it couldn't be installed.

> The following packages have unmet dependencies:

openshot: Depends: python (>= 2.5) but 2.7.1-0ubuntu5 is to be installed

---

### Post by Rubi1200 on 2011-05-05
Give this a shot and see if it helps:

Go to System > Administration > Software Sources or alternatively > Synaptic Package Manager > Repositories and uncheck the proposed and backports options. Then, hit the Reload button to refresh the sources list. Close the tab and/or Synaptic and then run these commands in the terminal:

```
sudo apt-get update

sudo apt--get install -f

sudo dpkg --configure -a

sudo apt-get install openshot
```

Let me know what happens please.

---

### Post by DayLite on 2011-05-05
> **Rubi1200 said:**
> Give this a shot and see if it helps:

Go to System > Administration > Software Sources or alternatively > Synaptic Package Manager > Repositories and uncheck the proposed and backports options. Then, hit the Reload button to refresh the sources list. Close the tab and/or Synaptic and then run these commands in the terminal:

```
sudo apt-get update

sudo apt--get install -f

sudo dpkg --configure -a

sudo apt-get install openshot
```Let me know what happens please.

I did what you said:

```
joan@joan-desktop:~$ sudo apt-get update
[sudo] password for joan: 
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [197 B]                          
Get:2 http://dl.google.com stable Release [1,347 B]                            
Get:3 http://dl.google.com stable/main i386 Packages [764 B]                   
Hit http://packages.medibuntu.org natty InRelease                              
Ign http://archive.canonical.com natty InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://us.archive.ubuntu.com lucid-backports InRelease                     
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com natty Release.gpg                             
Ign http://us.archive.ubuntu.com natty-security InRelease                      
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Hit http://packages.medibuntu.org natty/free Sources                           
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://archive.canonical.com natty Release                                 
Hit http://extras.ubuntu.com natty Release                                     
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://us.archive.ubuntu.com natty-security Release.gpg                    
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://packages.medibuntu.org natty/non-free Sources                       
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty-updates Release                         
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Hit http://us.archive.ubuntu.com natty-security Release                        
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://ppa.launchpad.net natty Release                                     
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com natty-security/restricted Sources             
Hit http://us.archive.ubuntu.com natty-security/main Sources                   
Hit http://us.archive.ubuntu.com natty-security/multiverse Sources             
Hit http://us.archive.ubuntu.com natty-security/universe Sources               
Hit http://us.archive.ubuntu.com natty-security/main i386 Packages             
Hit http://us.archive.ubuntu.com natty-security/restricted i386 Packages       
Hit http://us.archive.ubuntu.com natty-security/universe i386 Packages         
Hit http://us.archive.ubuntu.com natty-security/multiverse i386 Packages       
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://us.archive.ubuntu.com natty-security/main TranslationIndex          
Ign http://us.archive.ubuntu.com natty-security/multiverse TranslationIndex    
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://us.archive.ubuntu.com natty-security/restricted TranslationIndex    
Ign http://us.archive.ubuntu.com natty-security/universe TranslationIndex      
Ign http://archive.canonical.com natty/partner Translation-en                  
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://dl.google.com stable/main Translation-en                            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://us.archive.ubuntu.com natty-security/main Translation-en_US         
Ign http://us.archive.ubuntu.com natty-security/main Translation-en            
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en      
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en      
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en_US     
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en        
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Fetched 2,308 B in 10s (222 B/s)                                               
Reading package lists... Done
joan@joan-desktop:~$ sudo apt--get install -f
sudo: apt--get: command not found
joan@joan-desktop:~$ sudo apt--get install -f
sudo: apt--get: command not found
joan@joan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 59 not upgraded.
joan@joan-desktop:~$ sudo dpkg --configure -a
joan@joan-desktop:~$ sudo dpkg -configure -a
dpkg: error: unknown option -o

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
joan@joan-desktop:~$ sudo apt-get install openshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openshot : Depends: melt but it is not going to be installed
            Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable
            Depends: python-pygoocanvas but it is not going to be installed
E: Broken packages
joan@joan-desktop:~$ 

```

I also noticed under 'update' under Software Sources that Pre-released updates (natty-proposed) and Unsupported updates (Unsupported updates (natty- backports) were not checked.

---

### Post by jramshu on 2011-05-05
It also looks like you may need to run this, since I notice the "59 not upgraded."

```
sudo apt-get dist-upgrade
```Then post the output.

EDIT: I don't think the "sudo apt--get install -f" will work. I should look like this:

```
sudo apt-get install -f
```From what I can tell the above command "fixes" the dependency tree.

EDIT 2: My bad I see in the output you used the above refenced command.

---

### Post by DayLite on 2011-05-05
> **jramshu said:**
> It also looks like you may need to run this, since I notice the "59 not upgraded."

```
sudo apt-get dist-upgrade
```Then post the output.

EDIT: I don't think the "sudo apt--get install -f" will work. I should look like this:

```
sudo apt-get install -f
```From what I can tell the above command "fixes" the dependency tree.

EDIT 2: My bad I see in the output you used the above refenced command.

```
joan@joan-desktop:~$ sudo apt-get dist-upgrade
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  gnome-media libgnome-media0 pulseaudio pulseaudio-esound-compat
  ubuntu-desktop
The following NEW packages will be installed:
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-0.5 gir1.2-unity-3.0
The following packages have been kept back:
  alsa-utils bluez-alsa eog firefox firefox-globalmenu font-manager
  gcj-4.4-jre-lib gdb gedit gnome-mplayer gstreamer0.10-alsa kdelibs4c2a
  libasound2 libasound2-plugins libcanberra0 libdb4.7-java-gcj libgcj-bc
  libgcj10 libportaudio2 mencoder mplayer openjdk-6-jre rdesktop
  seamonkey-browser xulrunner-1.9.2
The following packages will be upgraded:
  bamfdaemon gnome-media-common gnome-session gnome-session-bin
  gnome-session-common gwibber-service gwibber-service-facebook
  gwibber-service-identica gwibber-service-twitter language-selector
  language-selector-common language-selector-gnome libbamf0 liblircclient0
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libsmbclient
  libsyncdaemon-1.0-1 libwbclient0 pulseaudio-utils python-ubuntuone-client
  samba samba-common samba-common-bin smbclient ubuntuone-client
  ubuntuone-client-gnome winbind
29 upgraded, 3 newly installed, 5 to remove and 25 not upgraded.
Need to get 0 B/35.9 MB of archives.
After this operation, 3,592 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 208672 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gnome-media ...
Removing libgnome-media0 ...
Removing pulseaudio-esound-compat ...
Removing pulseaudio ...
 * PulseAudio configured for per-user sessions
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
(Reading database ... 208525 files and directories currently installed.)
Preparing to replace libbamf0 0.2.90-0ubuntu2 (using .../libbamf0_0.2.90-0ubuntu3_i386.deb) ...
Unpacking replacement libbamf0 ...
Preparing to replace bamfdaemon 0.2.90-0ubuntu2 (using .../bamfdaemon_0.2.90-0ubuntu3_i386.deb) ...
Unpacking replacement bamfdaemon ...
Preparing to replace language-selector-gnome 0.33 (using .../language-selector-gnome_0.34_all.deb) ...
Unpacking replacement language-selector-gnome ...
Preparing to replace language-selector-common 0.33 (using .../language-selector-common_0.34_all.deb) ...
Unpacking replacement language-selector-common ...
Selecting previously deselected package gir1.2-dbusmenu-glib-0.4.
Unpacking gir1.2-dbusmenu-glib-0.4 (from .../gir1.2-dbusmenu-glib-0.4_0.4.3-0ubuntu3_i386.deb) ...
Selecting previously deselected package gir1.2-dee-0.5.
Unpacking gir1.2-dee-0.5 (from .../gir1.2-dee-0.5_0.5.18-0ubuntu1_i386.deb) ...
Selecting previously deselected package gir1.2-unity-3.0.
Unpacking gir1.2-unity-3.0 (from .../gir1.2-unity-3.0_3.8.4-0ubuntu1_i386.deb) ...
Preparing to replace gnome-media-common 2.31.6-0ubuntu2 (using .../gnome-media-common_2.32.0-0ubuntu7_all.deb) ...
Unpacking replacement gnome-media-common ...
Preparing to replace gnome-session-bin 2.32.1-0ubuntu19 (using .../gnome-session-bin_2.32.1-0ubuntu20_i386.deb) ...
Unpacking replacement gnome-session-bin ...
Preparing to replace gnome-session 2.32.1-0ubuntu19 (using .../gnome-session_2.32.1-0ubuntu20_all.deb) ...
Unpacking replacement gnome-session ...
Preparing to replace gnome-session-common 2.32.1-0ubuntu19 (using .../gnome-session-common_2.32.1-0ubuntu20_all.deb) ...
Unpacking replacement gnome-session-common ...
Preparing to replace gwibber-service 3.0.0.1-0ubuntu2 (using .../gwibber-service_3.0.0.1-0ubuntu3_all.deb) ...
Unpacking replacement gwibber-service ...
Preparing to replace gwibber-service-facebook 3.0.0.1-0ubuntu2 (using .../gwibber-service-facebook_3.0.0.1-0ubuntu3_all.deb) ...
Unpacking replacement gwibber-service-facebook ...
Preparing to replace gwibber-service-identica 3.0.0.1-0ubuntu2 (using .../gwibber-service-identica_3.0.0.1-0ubuntu3_all.deb) ...
Unpacking replacement gwibber-service-identica ...
Preparing to replace gwibber-service-twitter 3.0.0.1-0ubuntu2 (using .../gwibber-service-twitter_3.0.0.1-0ubuntu3_all.deb) ...
Unpacking replacement gwibber-service-twitter ...
Preparing to replace language-selector 0.33 (using .../language-selector_0.34_all.deb) ...
Unpacking replacement language-selector ...
Preparing to replace libpulse-mainloop-glib0 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1 (using .../libpulse-mainloop-glib0_1%3a0.9.22+stable-queue-24-g67d18-0ubuntu3_i386.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Preparing to replace pulseaudio-utils 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1 (using .../pulseaudio-utils_1%3a0.9.22+stable-queue-24-g67d18-0ubuntu3_i386.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace libpulse-browse0 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1 (using .../libpulse-browse0_1%3a0.9.22+stable-queue-24-g67d18-0ubuntu3_i386.deb) ...
Unpacking replacement libpulse-browse0 ...
Preparing to replace libpulse0 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1 (using .../libpulse0_1%3a0.9.22+stable-queue-24-g67d18-0ubuntu3_i386.deb) ...
Unpacking replacement libpulse0 ...
Preparing to replace ubuntuone-client-gnome 1.6.1-0ubuntu3 (using .../ubuntuone-client-gnome_1.6.2-0ubuntu1_i386.deb) ...
Unpacking replacement ubuntuone-client-gnome ...
Preparing to replace libsyncdaemon-1.0-1 1.6.1-0ubuntu3 (using .../libsyncdaemon-1.0-1_1.6.2-0ubuntu1_i386.deb) ...
Unpacking replacement libsyncdaemon-1.0-1 ...
Preparing to replace ubuntuone-client 1.6.1-0ubuntu3 (using .../ubuntuone-client_1.6.2-0ubuntu1_all.deb) ...
Unpacking replacement ubuntuone-client ...
Preparing to replace python-ubuntuone-client 1.6.1-0ubuntu3 (using .../python-ubuntuone-client_1.6.2-0ubuntu1_all.deb) ...
Unpacking replacement python-ubuntuone-client ...
Preparing to replace winbind 2:3.5.8~dfsg-1ubuntu2 (using .../winbind_2%3a3.5.8~dfsg-1ubuntu2.1_i386.deb) ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Unpacking replacement winbind ...
Preparing to replace samba 2:3.5.8~dfsg-1ubuntu2 (using .../samba_2%3a3.5.8~dfsg-1ubuntu2.1_i386.deb) ...
nmbd stop/waiting
smbd stop/waiting
Unpacking replacement samba ...
Preparing to replace libwbclient0 2:3.5.8~dfsg-1ubuntu2 (using .../libwbclient0_2%3a3.5.8~dfsg-1ubuntu2.1_i386.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace smbclient 2:3.5.8~dfsg-1ubuntu2 (using .../smbclient_2%3a3.5.8~dfsg-1ubuntu2.1_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common-bin 2:3.5.8~dfsg-1ubuntu2 (using .../samba-common-bin_2%3a3.5.8~dfsg-1ubuntu2.1_i386.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace samba-common 2:3.5.8~dfsg-1ubuntu2 (using .../samba-common_2%3a3.5.8~dfsg-1ubuntu2.1_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace liblircclient0 0.8.7-0ubuntu4 (using .../liblircclient0_0.8.7-0ubuntu4.1_i386.deb) ...
Unpacking replacement liblircclient0 ...
Preparing to replace libsmbclient 2:3.5.8~dfsg-1ubuntu2 (using .../libsmbclient_2%3a3.5.8~dfsg-1ubuntu2.1_i386.deb) ...
Unpacking replacement libsmbclient ...
Processing triggers for libglib2.0-0 ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for python-support ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Setting up bamfdaemon (0.2.90-0ubuntu3) ...
Rebuilding /usr/share/applications/bamf.index...
Setting up libbamf0 (0.2.90-0ubuntu3) ...
Setting up language-selector-common (0.34) ...
Setting up language-selector-gnome (0.34) ...
Setting up gir1.2-dbusmenu-glib-0.4 (0.4.3-0ubuntu3) ...
Setting up gir1.2-dee-0.5 (0.5.18-0ubuntu1) ...
Setting up gir1.2-unity-3.0 (3.8.4-0ubuntu1) ...
Setting up gnome-media-common (2.32.0-0ubuntu7) ...
Setting up gnome-session-bin (2.32.1-0ubuntu20) ...
Setting up gnome-session-common (2.32.1-0ubuntu20) ...
Setting up gnome-session (2.32.1-0ubuntu20) ...
Setting up gwibber-service (3.0.0.1-0ubuntu3) ...
Setting up language-selector (0.34) ...
Setting up libpulse0 (1:0.9.22+stable-queue-24-g67d18-0ubuntu3) ...
Setting up libpulse-mainloop-glib0 (1:0.9.22+stable-queue-24-g67d18-0ubuntu3) ...
Setting up libpulse-browse0 (1:0.9.22+stable-queue-24-g67d18-0ubuntu3) ...
Setting up pulseaudio-utils (1:0.9.22+stable-queue-24-g67d18-0ubuntu3) ...
Setting up python-ubuntuone-client (1.6.2-0ubuntu1) ...
Installing new version of config file /etc/xdg/ubuntuone/syncdaemon.conf ...
Installing new version of config file /etc/xdg/ubuntuone/logging.conf ...
Setting up ubuntuone-client (1.6.2-0ubuntu1) ...
Setting up libsyncdaemon-1.0-1 (1.6.2-0ubuntu1) ...
Setting up ubuntuone-client-gnome (1.6.2-0ubuntu1) ...
Setting up libwbclient0 (2:3.5.8~dfsg-1ubuntu2.1) ...
Setting up samba-common (2:3.5.8~dfsg-1ubuntu2.1) ...
Setting up winbind (2:3.5.8~dfsg-1ubuntu2.1) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 
Setting up samba-common-bin (2:3.5.8~dfsg-1ubuntu2.1) ...
Setting up samba (2:3.5.8~dfsg-1ubuntu2.1) ...
Installing new version of config file /etc/init/smbd.conf ...
smbd start/running, process 9987
nmbd start/running, process 10016
Setting up smbclient (2:3.5.8~dfsg-1ubuntu2.1) ...
Setting up liblircclient0 (0.8.7-0ubuntu4.1) ...
Setting up libsmbclient (2:3.5.8~dfsg-1ubuntu2.1) ...
Processing triggers for python-central ...
Setting up gwibber-service-twitter (3.0.0.1-0ubuntu3) ...
Setting up gwibber-service-facebook (3.0.0.1-0ubuntu3) ...
Setting up gwibber-service-identica (3.0.0.1-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for python-central ...
joan@joan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libgladeui-1-9
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
joan@joan-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libgladeui-1-9
0 upgraded, 0 newly installed, 1 to remove and 25 not upgraded.
After this operation, 2,138 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 208558 files and directories currently installed.)
Removing libgladeui-1-9 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
joan@joan-desktop:~$ 

```

---

### Post by jramshu on 2011-05-05
Now try and see if it gives anymore errors. 
```
sudo apt-get update
sudo apt-get upgrade
```Post output.

EDIT: I must say that output looks much better. Your getting there.

---

### Post by DayLite on 2011-05-05
> **jramshu said:**
> Now try and see if it gives anymore errors. 
```
sudo apt-get update
sudo apt-get upgrade
```Post output.

EDIT: I must say that output looks much better. Your getting there.

Please keep on helping me. I have nobody except you to give me support.

```
joan@joan-desktop:~$ sudo apt-get update
[sudo] password for joan: 
Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.canonical.com natty InRelease                               
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://dl.google.com stable InRelease                                      
Hit http://packages.medibuntu.org natty InRelease                              
Hit http://extras.ubuntu.com natty Release                                     
Ign http://dl.google.com stable InRelease                                      
Hit http://ppa.launchpad.net natty Release.gpg                                 
Get:1 http://dl.google.com stable Release.gpg [197 B]                          
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://ppa.launchpad.net natty Release                                     
Hit http://packages.medibuntu.org natty/free Sources                           
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Get:2 http://dl.google.com stable Release.gpg [197 B]                          
Hit http://archive.canonical.com natty Release                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://packages.medibuntu.org natty/non-free Sources                       
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://us.archive.ubuntu.com lucid-backports InRelease                     
Ign http://us.archive.ubuntu.com natty-security InRelease                      
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Get:3 http://dl.google.com stable Release [1,347 B]                  
Ign http://packages.medibuntu.org natty/free TranslationIndex             
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://us.archive.ubuntu.com natty-security Release.gpg                    
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://us.archive.ubuntu.com natty-updates Release                         
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://dl.google.com stable/main i386 Packages [1,055 B]                 
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://us.archive.ubuntu.com natty-security Release                        
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/main i386 Packages            
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages      
Hit http://us.archive.ubuntu.com natty/universe i386 Packages        
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com natty/main TranslationIndex         
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources    
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com natty-security/restricted Sources             
Hit http://us.archive.ubuntu.com natty-security/main Sources                   
Hit http://us.archive.ubuntu.com natty-security/multiverse Sources             
Hit http://us.archive.ubuntu.com natty-security/universe Sources     
Hit http://us.archive.ubuntu.com natty-security/main i386 Packages   
Hit http://us.archive.ubuntu.com natty-security/restricted i386 Packages       
Hit http://us.archive.ubuntu.com natty-security/universe i386 Packages         
Hit http://us.archive.ubuntu.com natty-security/multiverse i386 Packages       
Ign http://us.archive.ubuntu.com natty-security/main TranslationIndex          
Ign http://us.archive.ubuntu.com natty-security/multiverse TranslationIndex    
Ign http://us.archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/universe TranslationIndex
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://us.archive.ubuntu.com natty-security/main Translation-en_US         
Ign http://us.archive.ubuntu.com natty-security/main Translation-en            
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en      
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en      
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en_US     
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en        
Ign http://dl.google.com stable/main TranslationIndex                          
Get:6 http://dl.google.com stable/main i386 Packages [764 B]
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en
Fetched 4,907 B in 32s (152 B/s)
Reading package lists... Done
joan@joan-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  alsa-utils bluez-alsa eog firefox firefox-globalmenu font-manager
  gcj-4.4-jre-lib gdb gedit gnome-mplayer gstreamer0.10-alsa kdelibs4c2a
  libasound2 libasound2-plugins libcanberra0 libdb4.7-java-gcj libgcj-bc
  libgcj10 libportaudio2 mencoder mplayer openjdk-6-jre rdesktop
  seamonkey-browser xulrunner-1.9.2
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
joan@joan-desktop:~$ 

```

---

### Post by jramshu on 2011-05-05
I saw on another output is was saying some dependencies were not needed and needed to be removed. So try this:

```
sudo apt-get autoremove
```Still trying to figure out the 25 not upgraded. And again let's see the ouput, or I should just say always show the output. 

:lolflag:


EDIT: Oops again, I see you already used the auto-remove too.

---

### Post by jramshu on 2011-05-05
Ok. Looks like you may have to do this again and see if it upgrades the packages "kept back"

```
sudo apt-get update && sudo apt-get dist-upgrade
```

This just groups the commands together by the way.

---

### Post by DayLite on 2011-05-05
> **jramshu said:**
> Ok. Looks like you may have to do this again and see if it upgrades the packages "kept back"

```
sudo apt-get update && sudo apt-get dist-upgrade
```This just groups the commands together by the way.

```
joan@joan-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for joan: 
Ign http://archive.canonical.com natty InRelease
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://us.archive.ubuntu.com lucid-backports InRelease                     
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://extras.ubuntu.com natty Release.gpg                                 
Ign http://us.archive.ubuntu.com natty-security InRelease                      
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Hit http://packages.medibuntu.org natty InRelease                              
Hit http://archive.canonical.com natty Release                                 
Hit http://extras.ubuntu.com natty Release                                     
Get:1 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]           
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://archive.canonical.com natty/partner Sources                         
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://us.archive.ubuntu.com natty-security Release.gpg                    
Hit http://packages.medibuntu.org natty/free Sources                           
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty Release                                 
Get:2 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]             
Hit http://packages.medibuntu.org natty/non-free Sources                       
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://us.archive.ubuntu.com natty-security Release                        
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/main Sources                            
Ign http://dl.google.com stable InRelease                                      
Get:3 http://dl.google.com stable Release.gpg [197 B]                          
Get:4 http://dl.google.com stable Release.gpg [197 B]                          
Get:5 http://dl.google.com stable Release [1,347 B]                            
Ign http://archive.canonical.com natty/partner Translation-en_US               
Get:6 http://dl.google.com stable Release [1,347 B]                            
Get:7 http://dl.google.com stable/main i386 Packages [1,055 B]                 
Ign http://archive.canonical.com natty/partner Translation-en                  
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Ign http://dl.google.com stable/main TranslationIndex                          
Get:8 http://dl.google.com stable/main i386 Packages [764 B]                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Get:9 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]     
Get:10 http://us.archive.ubuntu.com natty-updates/main Sources [18.4 kB]       
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release                                     
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Hit http://ppa.launchpad.net natty Release                                     
Ign http://extras.ubuntu.com natty/main Translation-en                         
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Get:11 http://us.archive.ubuntu.com natty-updates/multiverse Sources [14 B]    
Get:12 http://us.archive.ubuntu.com natty-updates/universe Sources [5,310 B]   
Get:13 http://us.archive.ubuntu.com natty-updates/main i386 Packages [72.7 kB] 
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:14 http://us.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:15 http://us.archive.ubuntu.com natty-updates/universe i386 Packages [23.2 kB]
Get:16 http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages [14 B]
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com natty-security/restricted Sources             
Hit http://us.archive.ubuntu.com natty-security/main Sources                   
Hit http://us.archive.ubuntu.com natty-security/multiverse Sources             
Hit http://us.archive.ubuntu.com natty-security/universe Sources               
Hit http://us.archive.ubuntu.com natty-security/main i386 Packages             
Hit http://us.archive.ubuntu.com natty-security/restricted i386 Packages       
Hit http://us.archive.ubuntu.com natty-security/universe i386 Packages         
Hit http://us.archive.ubuntu.com natty-security/multiverse i386 Packages       
Ign http://us.archive.ubuntu.com natty-security/main TranslationIndex          
Ign http://us.archive.ubuntu.com natty-security/multiverse TranslationIndex    
Ign http://us.archive.ubuntu.com natty-security/restricted TranslationIndex    
Ign http://us.archive.ubuntu.com natty-security/universe TranslationIndex      
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://us.archive.ubuntu.com natty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/main Translation-en
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en
Ign http://packages.medibuntu.org natty/free Translation-en_US
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_US
Ign http://packages.medibuntu.org natty/non-free Translation-en
Fetched 152 kB in 21s (7,093 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  alsa-utils bluez-alsa eog firefox firefox-globalmenu font-manager
  gcj-4.4-jre-lib gdb gedit gnome-mplayer gstreamer0.10-alsa kdelibs4c2a
  libasound2 libasound2-plugins libcanberra0 libdb4.7-java-gcj libgcj-bc
  libgcj10 libportaudio2 mencoder mplayer openjdk-6-jre rdesktop
  seamonkey-browser xulrunner-1.9.2
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
joan@joan-desktop:~$ 

```

:confused:

---

### Post by jramshu on 2011-05-05
It seems some dependencies are missing to get the ones that are kept back to update. I'm looking in to it. Don't get frustrated, at least it's not spitting out all those errors anymore. Hang in there this is a simple fix.

---

### Post by jramshu on 2011-05-05
Let's try this:
```
sudo apt-get check
```


EDIT:You may also want to try and see if the update manager can resolve this.

---

### Post by DayLite on 2011-05-05
Changes :cry: Now I don't have sound and my no sound menu.

playback_auto Failed

---

### Post by jramshu on 2011-05-05
That's what you get after running "sudo apt-get check"? That should have just check for broken dependencies. 

Did you check the update manager?

---

### Post by el_koraco on 2011-05-05
> **DayLite said:**
> Changes :cry: Now I don't have sound and my no sound menu.

playback_auto Failed

That's because it removed pulseaudio for some reason. The sound server. Reinstall it by running: 

```
sudo apt-get install gnome-media libgnome-media0 pulseaudio pulseaudio-esound-compat
```

---

### Post by jramshu on 2011-05-05
el-koraco can you help us out here with updating the "kept" packages?

Thanks

---

### Post by el_koraco on 2011-05-05
Packages are kept back when their upgrading might cause some system discrepancies. Not a problem in itself and i don't believe this is the cause for the problems here.

---

### Post by el_koraco on 2011-05-05
Daylite, after you've reinstalled pulseaudio, run 

```
sudo dpkg --configure -a
```

followed by ```
sudo apt-get install -f
```

several times. 

Then try to install openshot. Sometimes all you have to do is run the fixing commands several times.

---

### Post by DayLite on 2011-05-05
> **el_koraco said:**
> That's because it removed pulseaudio for some reason. The sound server. Reinstall it by running: 

```
sudo apt-get install gnome-media libgnome-media0 pulseaudio pulseaudio-esound-compat
```

I don't know what happened.  I rebooted around three times and also checked my sounds by booting into windows...had sound.

Another boot into Ubuntu around two more times and my sound came back.

---

### Post by jramshu on 2011-05-05
> **el_koraco said:**
> Packages are kept back when their upgrading might cause some system discrepancies. Not a problem in itself and i don't believe this is the cause for the problems here.

I figured the kept back packages shouldn't be a problem. 

Thanks for the quick answer.

---

### Post by DayLite on 2011-05-05
> **el_koraco said:**
> Daylite, after you've reinstalled pulseaudio, run 

```
sudo dpkg --configure -a
```followed by ```
sudo apt-get install -f
```several times. 

Then try to install openshot. Sometimes all you have to do is run the fixing commands several times.

I did what you said. Still no change.

```
joan@joan-desktop:~$ sudo dpkg --configure -a
[sudo] password for joan: 
joan@joan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
joan@joan-desktop:~$ sudo dpkg --configure -a
joan@joan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
joan@joan-desktop:~$ sudo dpkg --configure -a
joan@joan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
joan@joan-desktop:~$ sudo dpkg --configure -a
joan@joan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
joan@joan-desktop:~$ 

```

---

### Post by jramshu on 2011-05-05
DayLite,

Don't worry about the "kept back" packages, for now. You wanted openshot I believe.
Let's see if you can get it since your machine isn't spitting out all those errors.

```
sudo apt-get install openshot
```

---

### Post by el_koraco on 2011-05-05
> **DayLite said:**
> I don't know what happened.  I rebooted around three times and also checked my sounds by booting into windows...had sound.

Another boot into Ubuntu around two more times and my sound came back.

Well, this might be a lesson worth learning. Linux systems communicate with your sound cards through several "sound servers". One of them is pulseaudio, the central server which takes care of the sound for you in Ubuntu. The next time an update offers to remove it, don't go through with it. 

Why the dist-upgrade removed pulseaudio, I don't know. I'm  kinda guessing that you might be having problems with the mirror you're downloading packages from. it looks like there have been updates, but not all of them have come through. So do this. After you've run the "dpkg" and "apt-get install -f" commands i mentioned earlier, go to the Software Center, Edit, Software sources. You'll see on the bottom the server you're downloading from. Select "other", and then select best server. Let it finish checking and choose the server for you. It will then reload the information. 

Then do 

```
sudo apt-get update && sudo apt-get install openshot 
```

Let's see if that solves any of the issues.

---

### Post by el_koraco on 2011-05-05
> **DayLite said:**
> I did what you said. Still no change.
[/CODE]

Sure there is, now we know there shouldn't be any more broken packages :D

---

### Post by DayLite on 2011-05-05
> **el_koraco said:**
> Well, this might be a lesson worth learning. Linux systems communicate with your sound cards through several "sound servers". One of them is pulseaudio, the central server which takes care of the sound for you in Ubuntu. The next time an update offers to remove it, don't go through with it. 

Why the dist-upgrade removed pulseaudio, I don't know. I'm  kinda guessing that you might be having problems with the mirror you're downloading packages from. it looks like there have been updates, but not all of them have come through. So do this. After you've run the "dpkg" and "apt-get install -f" commands i mentioned earlier, go to the Software Center, Edit, Software sources. You'll see on the bottom the server you're downloading from. Select "other", and then select best server. Let it finish checking and choose the server for you. It will then reload the information. 

Then do 

```
sudo apt-get update && sudo apt-get install openshot 
```Let's see if that solves any of the issues.

I selected the best server, like you suggested,(it downloads much faster!) Then I ran in the terminal:

```
joan@joan-desktop:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
joan@joan-desktop:~$ sudo apt-get install -f
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
joan@joan-desktop:~$ sudo apt-get update && sudo apt-get install openshot
Ign http://mirrors.us.kernel.org natty InRelease
Ign http://mirrors.us.kernel.org natty-updates InRelease                       
Ign http://mirrors.us.kernel.org natty-security InRelease                      
Hit http://mirrors.us.kernel.org natty Release.gpg                             
Ign http://dl.google.com stable InRelease                                      
Hit http://mirrors.us.kernel.org natty-updates Release.gpg                     
Hit http://mirrors.us.kernel.org natty-security Release.gpg                    
Hit http://mirrors.us.kernel.org natty Release                                 
Ign http://dl.google.com stable InRelease                                      
Hit http://mirrors.us.kernel.org natty-updates Release                         
Hit http://mirrors.us.kernel.org natty-security Release                        
Get:1 http://dl.google.com stable Release.gpg [197 B]                          
Hit http://mirrors.us.kernel.org natty/restricted Sources                      
Hit http://mirrors.us.kernel.org natty/main Sources                            
Hit http://mirrors.us.kernel.org natty/multiverse Sources                      
Hit http://mirrors.us.kernel.org natty/universe Sources                        
Hit http://mirrors.us.kernel.org natty/main i386 Packages                      
Hit http://mirrors.us.kernel.org natty/restricted i386 Packages                
Hit http://mirrors.us.kernel.org natty/universe i386 Packages                  
Hit http://mirrors.us.kernel.org natty/multiverse i386 Packages                
Ign http://mirrors.us.kernel.org natty/main TranslationIndex                   
Ign http://mirrors.us.kernel.org natty/multiverse TranslationIndex             
Ign http://mirrors.us.kernel.org natty/restricted TranslationIndex             
Ign http://mirrors.us.kernel.org natty/universe TranslationIndex               
Hit http://mirrors.us.kernel.org natty-updates/restricted Sources              
Hit http://mirrors.us.kernel.org natty-updates/main Sources                    
Hit http://mirrors.us.kernel.org natty-updates/multiverse Sources              
Hit http://mirrors.us.kernel.org natty-updates/universe Sources                
Hit http://mirrors.us.kernel.org natty-updates/main i386 Packages              
Hit http://mirrors.us.kernel.org natty-updates/restricted i386 Packages        
Hit http://mirrors.us.kernel.org natty-updates/universe i386 Packages          
Ign http://archive.canonical.com natty InRelease                               
Get:2 http://dl.google.com stable Release.gpg [197 B]                          
Hit http://mirrors.us.kernel.org natty-updates/multiverse i386 Packages        
Ign http://us.archive.ubuntu.com lucid-backports InRelease                     
Ign http://mirrors.us.kernel.org natty-updates/main TranslationIndex           
Ign http://mirrors.us.kernel.org natty-updates/multiverse TranslationIndex     
Ign http://mirrors.us.kernel.org natty-updates/restricted TranslationIndex     
Ign http://mirrors.us.kernel.org natty-updates/universe TranslationIndex       
Hit http://mirrors.us.kernel.org natty-security/restricted Sources             
Hit http://mirrors.us.kernel.org natty-security/main Sources                   
Hit http://mirrors.us.kernel.org natty-security/multiverse Sources             
Hit http://mirrors.us.kernel.org natty-security/universe Sources               
Hit http://mirrors.us.kernel.org natty-security/main i386 Packages             
Ign http://extras.ubuntu.com natty InRelease                                   
Hit http://mirrors.us.kernel.org natty-security/restricted i386 Packages       
Hit http://mirrors.us.kernel.org natty-security/universe i386 Packages         
Hit http://mirrors.us.kernel.org natty-security/multiverse i386 Packages       
Ign http://mirrors.us.kernel.org natty-security/main TranslationIndex          
Ign http://mirrors.us.kernel.org natty-security/multiverse TranslationIndex    
Ign http://mirrors.us.kernel.org natty-security/restricted TranslationIndex    
Ign http://mirrors.us.kernel.org natty-security/universe TranslationIndex      
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://packages.medibuntu.org natty InRelease                              
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Get:3 http://dl.google.com stable Release [1,347 B]                            
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.canonical.com natty Release                                 
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://extras.ubuntu.com natty Release                                     
Hit http://packages.medibuntu.org natty/free Sources                           
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://mirrors.us.kernel.org natty/main Translation-en_US                  
Ign http://mirrors.us.kernel.org natty/main Translation-en                     
Ign http://mirrors.us.kernel.org natty/multiverse Translation-en_US            
Ign http://mirrors.us.kernel.org natty/multiverse Translation-en               
Ign http://mirrors.us.kernel.org natty/restricted Translation-en_US            
Ign http://mirrors.us.kernel.org natty/restricted Translation-en               
Ign http://mirrors.us.kernel.org natty/universe Translation-en_US              
Hit http://packages.medibuntu.org natty/non-free Sources                       
Ign http://mirrors.us.kernel.org natty/universe Translation-en                 
Ign http://mirrors.us.kernel.org natty-updates/main Translation-en_US          
Ign http://mirrors.us.kernel.org natty-updates/main Translation-en             
Ign http://mirrors.us.kernel.org natty-updates/multiverse Translation-en_US    
Ign http://mirrors.us.kernel.org natty-updates/multiverse Translation-en       
Ign http://mirrors.us.kernel.org natty-updates/restricted Translation-en_US    
Ign http://mirrors.us.kernel.org natty-updates/restricted Translation-en       
Ign http://mirrors.us.kernel.org natty-updates/universe Translation-en_US      
Ign http://mirrors.us.kernel.org natty-updates/universe Translation-en         
Ign http://mirrors.us.kernel.org natty-security/main Translation-en_US         
Ign http://mirrors.us.kernel.org natty-security/main Translation-en            
Ign http://mirrors.us.kernel.org natty-security/multiverse Translation-en_US   
Ign http://mirrors.us.kernel.org natty-security/multiverse Translation-en      
Ign http://mirrors.us.kernel.org natty-security/restricted Translation-en_US   
Ign http://mirrors.us.kernel.org natty-security/restricted Translation-en      
Ign http://mirrors.us.kernel.org natty-security/universe Translation-en_US     
Get:4 http://dl.google.com stable Release [1,347 B]                            
Ign http://mirrors.us.kernel.org natty-security/universe Translation-en        
Get:5 http://dl.google.com stable/main i386 Packages [1,055 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Get:6 http://dl.google.com stable/main i386 Packages [764 B]                   
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Hit http://archive.canonical.com natty/partner Sources                         
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net natty Release.gpg                       
Hit http://ppa.launchpad.net natty Release.gpg                       
Hit http://ppa.launchpad.net natty Release     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Hit http://ppa.launchpad.net natty/main i386 Packages                
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_US
Ign http://packages.medibuntu.org natty/non-free Translation-en
Fetched 4,907 B in 14s (345 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openshot : Depends: melt but it is not going to be installed
            Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable
            Depends: python-pygoocanvas but it is not going to be installed
E: Broken packages
joan@joan-desktop:~$ 

```

Same as before, I can't install OpenShot or any other video editor.

---

### Post by Dutch70 on 2011-05-05
Try updating through update manager once, see if it installs the other 25 packages.

Also, what version of Python do you have installed?

---

### Post by Jesus_Valdez on 2011-05-05
Have you had added some ppa? followed some instructions on some website?

Last time I had a problem similar to yours (but with another software) I solve it going into Synaptic, looking for the packages that didn't want to install and try to install them, or if they are installed downgrading (package -> force version on synaptic).

surely if you start looking for python-mlt3, python-mlt2 or melt you will find the problem.

---

### Post by DayLite on 2011-05-05
> **Dutch70 said:**
> Try updating through update manager once, see if it installs the other 25 packages.

Also, what version of Python do you have installed?

Where do I find out about what version I have?
 I have ran the update manager.  Many programs were listed but when I tried to check them for download, I couldn't. It also said 'there is no upgrades to install'.

---

### Post by Dutch70 on 2011-05-05
The only way I know is to open synaptic, search for python & see what it says there. 

I really don't know anything about this, but I think this gives  your best clue.
```
The following packages have unmet dependencies:

openshot: Depends: python (>= 2.5) but 2.7.1-0ubuntu5 is to be installed
```

See if you can find anything useful in the comments at the bottom of this link.
[[COLOR="RoyalBlue"]http://www.makeuseof.com/tag/openshot-finally-excellent-video-editor-linux/[/COLOR]]("http://www.makeuseof.com/tag/openshot-finally-excellent-video-editor-linux/")

Have you tried getting it from their site? 
[[COLOR="RoyalBlue"]http://www.openshot.org/download/[/COLOR]]("http://www.openshot.org/download/")

*Until you get this figured out, you may want to try PiTiVi or Kdenlive.*

---

### Post by dcsoldschool53 on 2011-05-05
Here is a website that you can goto.

[http://packages.ubuntu.com](http://packages.ubuntu.com)

Now scroll down to where you see "Search" and put the name of the depends that you need for Openshot. Click your OS too. Download and load them. then try loading Openshot again.

---

### Post by DayLite on 2011-05-05
> **Dutch70 said:**
> The only way I know is to open synaptic, search for python & see what it says there. 

I really don't know anything about this, but I think this gives  your best clue.
```
The following packages have unmet dependencies:

openshot: Depends: python (>= 2.5) but 2.7.1-0ubuntu5 is to be installed
```See if you can find anything useful in the comments at the bottom of this link.
[[COLOR=RoyalBlue]http://www.makeuseof.com/tag/openshot-finally-excellent-video-editor-linux/[/COLOR]]("http://www.makeuseof.com/tag/openshot-finally-excellent-video-editor-linux/")

Have you tried getting it from their site? 
[[COLOR=RoyalBlue]http://www.openshot.org/download/[/COLOR]]("http://www.openshot.org/download/")

*Until you get this figured out, you may want to try PiTiVi or Kdenlive.*

It says installed 
python version 2.7.1-Oubuntu5
python-xlib 0.14+20091101-1 
python-apt-common 0.7.100.3ubuntu6
python-numpy 1:1.5.1-1ubuntu2
python-egenix-mxtools 3.1.3-4build1
python-poppler 0.12.1-1ubuntu1
python-webkit 1.1.8-1ubuntu2
python-zope.interface 3.6.1-Oubuntu4
python-apt 0.7.100.3ubuntu6

I have a lot more python, must I list all?
> *you may want to try PiTiVi or Kdenlive.*

I did try.  Same as OpenShot, won't install.


The following packages have unmet dependencies:

pitivi: Depends: python-gtk2 (>= 2.14) but 2.22.0-0ubuntu1 is to be installed
        Depends: python-cairo (>= 1.0.0) but 1.8.8-1ubuntu1 is to be installed

---

### Post by DayLite on 2011-05-05
> **dcsoldschool53 said:**
> Here is a website that you can goto.

[http://packages.ubuntu.com](http://packages.ubuntu.com)

Now scroll down to where you see "Search" and put the name of the depends that you need for Openshot. Click your OS too. Download and load them. then try loading Openshot again.

fontconfig
generic font configuration library - support binaries
librsvg2-common
SAX-based renderer library for SVG files (extra runtime)
melt
command line media player and video editor
python (>= 2.5)
interactive high-level object-oriented language (default version)
python-glade2
GTK+ bindings: Glade support
python-gtk2
Python bindings for the GTK+ widget set
python-imaging
Python Imaging Library
python-mlt3
multimedia framework (python bindings)
or python-mlt2
Package not available
python-pygoocanvas
GooCanvas Python bindings
python-support (>= 0.90.0)
automated rebuilding support for Python modules
python-xdg
Python library to access freedesktop.org standards
frei0r-plugins
minimalistic plugin API for video effects, plugins collection
openshot-doc
Help manual for OpenShot Video Editor

---

### Post by jtarin on 2011-05-05
This [ppa ]("http://www.openshot.org/ppa/")should be added to your sources list......it list it as being for your version of Ubuntu 11.04. Instructions for adding are on the page. Need help post back. I'm not guaranteeing you won't have python problems but it's the latest stable version for 11.04. If you want the developers version go [here]("https://launchpad.net/~openshot.developers/+archive/ppa").

---

### Post by DayLite on 2011-05-06
> **jtarin said:**
> This [ppa ]("http://www.openshot.org/ppa/")should be added to your sources list......it list it as being for your version of Ubuntu 11.04. Instructions for adding are on the page. Need help post back. I'm not guaranteeing you won't have python problems but it's the latest stable version for 11.04. If you want the developers version go [here]("https://launchpad.net/~openshot.developers/+archive/ppa").

Thank you for your help. I already had followed the instructions on that page and also have the PPA.  Still doesn't install with the same message.

---

### Post by jramshu on 2011-05-06
Is this a clean install or an upgrade from another version?

EDIT: The reason I ask is it's possible to get a bad burn on the disk. If you don't have a lot of stuff on there it may be worth re-downloading it and starting fresh. Possibly reverting to 10.04 LTS. This seems like a bug to me. IMHO

EDIT 2: Everywhere I have read this problem is usually resolved with the sudo apt-get update, then sudo apt-get dist-upgrade. Maybe using aptitude may work. Gone this far might as well try it.

```
sudo aptitude update
sudo aptitude dist-upgrade
```

EDIT 3: When it gets to the part where it asks you Y/n, hit n and abort. Then post the output. It may try to remove your pulse audio. If so you will have to put a "-d" flag in there to prevent it.

---

### Post by QLee on 2011-05-06
It might be useful to check DayLite's sources list, is there some reason that lucid-backports are included in what appears to be a Natty install?

---

### Post by Elfy on 2011-05-06
Hijack posts removed - have your thread back Daylite.

---

### Post by DayLite on 2011-05-06
> **jramshu said:**
> Is this a clean install or an upgrade from another version?
.
  The problem with everything originates from Upgrading to 11.04, (from 10.10) it froze at Setting up udisks (1.0.2-4ubuntul) Only 3 minutes were left! I had to shut the computer down and reboot. So all the programs were on my computer and the only thing left was installing them. It never cleaned up the old files.

---

### Post by DayLite on 2011-05-06
> **forestpiskie said:**
> Hijack posts removed - have your thread back Daylite.

Thank you :D I am already confused enough without any additional confusion added to it.  I do understand the frustration the 'Hijacker' is feeling. Crying out for help sometimes blinds one to be considerate of others.

Thanks, I appreciate your alertness to come to my aid.

---

### Post by el_koraco on 2011-05-06
> **QLee said:**
> It might be useful to check DayLite's sources list, is there some reason that lucid-backports are included in what appears to be a Natty install?

good idea. DayLite, open a terminal and type 

```
less  /etc/apt/sources.list >> list
```This will make a text file named "list" in your home folder. Paste the contents here. I'm not gonna be in, but it might give some clues to other trying to help you.

---

### Post by Elfy on 2011-05-06
> **DayLite said:**
> Thank you :D I am already confused enough without any additional confusion added to it.  I do understand the frustration the 'Hijacker' is feeling. Crying out for help sometimes blinds one to be considerate of others.

Thanks, I appreciate your alertness to come to my aid.

Welcome - next time use the report button and aid will come sooner. This time someone else did so.

Good luck.

---

### Post by DayLite on 2011-05-06
> **QLee said:**
> It might be useful to check DayLite's sources list, is there some reason that lucid-backports are included in what appears to be a Natty install?

[IMG]http://inlinethumb35.webshots.com/44962/2093947860056553245S425x425Q85.jpg[/IMG]

[IMG]http://inlinethumb57.webshots.com/47096/2731359620056553245S600x600Q85.jpg[/IMG]

---

### Post by jramshu on 2011-05-06
> **DayLite said:**
> The problem with everything originates from Upgrading to 11.04, (from 10.10) it froze at Setting up udisks (1.0.2-4ubuntul) Only 3 minutes were left! I had to shut the computer down and reboot. So all the programs were on my computer and the only thing left was installing them. It never cleaned up the old files.

This has been reported several times, the part where the upgrade to 11.04 froze at the end. I'll have to look and see if a solution has been found. 

Still looking and it looks like a bug has been reported.

EDIT: I haven't found any solution to this yet. Most who have encountered it have done a clean install, just to save time. Not telling you to do this though. I will keep looking and may run across a workaround.

---

### Post by jramshu on 2011-05-06
Ok. Just read in another post of yours that you backed up your /home to flash. Have you considered a clean install? I know you are frustrated since the other thread is a week old. 

[http://ubuntuforums.org/showthread.php?t=1743474](http://ubuntuforums.org/showthread.php?t=1743474)

---

### Post by DayLite on 2011-05-06
> **el_koraco said:**
> good idea. DayLite, open a terminal and type 

```
less  /etc/apt/sources.list >> list
```This will make a text file named "list" in your home folder. Paste the contents here. I'm not gonna be in, but it might give some clues to other trying to help you.

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.us.kernel.org/ubuntu/ natty main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.us.kernel.org/ubuntu/ natty-updates main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.us.kernel.org/ubuntu/ natty universe
deb http://mirrors.us.kernel.org/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.us.kernel.org/ubuntu/ natty multiverse
deb http://mirrors.us.kernel.org/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

deb http://mirrors.us.kernel.org/ubuntu/ natty-security main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ natty-security restricted main multiverse universe #Added by software-properties
deb http://mirrors.us.kernel.org/ubuntu/ natty-security universe
deb http://mirrors.us.kernel.org/ubuntu/ natty-security multiverse

deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository
deb http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu natty main
deb-src http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu natty main
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.us.kernel.org/ubuntu/ natty main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.us.kernel.org/ubuntu/ natty-updates main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.us.kernel.org/ubuntu/ natty universe
deb http://mirrors.us.kernel.org/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.us.kernel.org/ubuntu/ natty multiverse
deb http://mirrors.us.kernel.org/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

deb http://mirrors.us.kernel.org/ubuntu/ natty-security main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ natty-security restricted main multiverse universe #Added by software-properties
deb http://mirrors.us.kernel.org/ubuntu/ natty-security universe
deb http://mirrors.us.kernel.org/ubuntu/ natty-security multiverse

deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository
deb http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu natty main
deb-src http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu natty main
```

---

### Post by DayLite on 2011-05-06
> **forestpiskie said:**
> Welcome - next time use the report button and aid will come sooner. This time someone else did so.

Good luck.

Where is the report button?

---

### Post by jerome1232 on 2011-05-06
under the Avatar, has an Exclamation mark and says report abuse.

---

### Post by DayLite on 2011-05-06
> **jramshu said:**
> Ok. Just read in another post of yours that you backed up your /home to flash. Have you considered a clean install? I know you are frustrated since the other thread is a week old. 

[http://ubuntuforums.org/showthread.php?t=1743474](http://ubuntuforums.org/showthread.php?t=1743474)

I did copy all from my home folder to my external drive. I am not confidant that I did copy the hidden files. I have my hard drive with two partitions, XP and Ubuntu. I am not sure that if I attempted a fresh install that I won't erase my XP partition. I am struggling to learn how to correct the problems, but my brain gets overwhelmed and 'shuts down', sort of.

Just want to express how I appreciate all your support, time and help.:)

---

### Post by DayLite on 2011-05-06
> **jerome1232 said:**
> under the Avatar, has an Exclamation mark and says report abuse.

Oh, I didn't understand what the 'report' was about.  I thought you were talking about my topic to get more people to see it.  I didn't realize it was to report the 'intruder'

---

### Post by jerome1232 on 2011-05-06
It's really a "get the mods attention button", you can describe exactly why your reporting a thread/post.

Enough of this off topic stuff though :p

---

### Post by jtarin on 2011-05-06
(If this suggestion has been mentioned....Sorry)
Remove the lines that refer to Lucid......they are absolutely no use to you. 
Check your /var/cache/apt/archives/partial (if it exist) and remove any files you find there and try again.

---

### Post by DayLite on 2011-05-06
> **brad1138 said:**
> DayLite, do you happen to have Kdenlive installed? I do and I found another post by someone w/11.04 that installed it and then could not install openshot, just a thought. Hopefully someone will chime in here to let me know which one of my ideas are going in the right direction and which are crap :)

Brad

No, I don't have kdenlive installed. My OpenShot was working great in Ubuntu 10.10. On my upgrade to 11.04 I lost it all.

I suggest you open your own thread because each thread helps only_** one**_ individual. Trying to post to two people on one thread leads to confusion.

---

### Post by jramshu on 2011-05-07
Try
```
sudo apt-get clean
```
This is supposed to clean out  /var/cache/apt/archives/partial and a few others, except the locked files. 

As far as dual booting with XP and removing it accidently, you would have to select manually setting up the partitions when installing.

---

### Post by Linux_junkie on 2011-05-07
Hi, I've read all the comments people  have put  to try and get this problem sorted for you.   If you really want to upgrade to Natty I would install it from scratch and not do an upgrade from a previous version.  There's always problem upgrading from previous version even in MS-Windows!

Copy contents of your home directory to a CD-RW or USB memory stick.

Install from Ubuntu CD

Select install alongside other OS (should not remove XP)

Once installed simply copy home directory from CD-RW or USB memory stick to home directory on HD.

Once installed 11.04 it should now allow you to install Openbox.

Hope this helps.

---

### Post by robert shearer on 2011-05-07
When my Natty install started acting weird with packages not being updated I re-downloaded the natty iso image and burnt a new disc.

So far so good. I had intended to make a fresh install and re-inserted the cd intending to reboot and run live.

I was distracted and the cd was mounted by the running Natty install causing the window to open that asked did I want to open the package manager as the cd had software updates.

So just out of curiosity I checked 'open' and let it run it's course.
The problem packages were updated and all has been fine since. I did not have to reinstall.

Not saying that this will fix your problem just that it may be worth a try if you do get to the fresh install stage.

cheers, Bob.

---

### Post by DayLite on 2011-05-07
> **robert shearer said:**
> When my Natty install started acting weird with packages not being updated I re-downloaded the natty iso image and burnt a new disc.

So far so good. I had intended to make a fresh install and re-inserted the cd intending to reboot and run live.

I was distracted and the cd was mounted by the running Natty install causing the window to open that asked did I want to open the package manager as the cd had software updates.

So just out of curiosity I checked 'open' and let it run it's course.
The problem packages were updated and all has been fine since. I did not have to reinstall.

Not saying that this will fix your problem just that it may be worth a try if you do get to the fresh install stage.

cheers, Bob.
This was interesting.  I have an install CD.  When you began, before you was distracted, did you click on 'test' or 'install' ?

---

### Post by DayLite on 2011-05-07
> **jramshu said:**
> Try
```
sudo apt-get clean
```This is supposed to clean out  /var/cache/apt/archives/partial and a few others, except the locked files. 


What about the possibility of erasing programs I installed in wine? When you say, "_a few others_", that makes me uneasy.

---

### Post by jramshu on 2011-05-07
Clean clears the caches for the repositories. Open a terminal type:
```
man apt-get
```Use spacebar and go to the section that describes what clean does.

Here it is instead:

```
clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(1) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

```

I said and others so I wouldn't have to list the paths to the two folders mentioned above.

---

### Post by jramshu on 2011-05-07
> **DayLite said:**
> This was interesting.  I have an install CD.  When you began, before you was distracted, did you click on 'test' or 'install' ?

Here is what he said:

"I was distracted and the cd was mounted by the running Natty _install_  causing the window to open that asked did I want to open the package  manager as the cd had software updates."

---

### Post by DayLite on 2011-05-07
> **jramshu said:**
> Here is what he said:

"I was distracted and the cd was mounted by the running Natty _install_  causing the window to open that asked did I want to open the package  manager as the cd had software updates."

I still am not clear as to what is said :confused:

"**running Natty**" Does that mean you were still on your 'active Ubuntu' and inserted the live CD and were going to shut down and have it then reboot to the live CD?

---

### Post by jramshu on 2011-05-07
I am just assuming exactly what he did. It looks like he booted the livecd to do a clean install, it detected that Natty was already installed and offered to just update the outdated files. So to make it short, insert disk, restart, click install. See what happens, nothing changes until it gets to where it sets up the partition. From what I remember, the installation checks for currently installed OS's.

---

### Post by DayLite on 2011-05-07
> **jramshu said:**
> I am just assuming exactly what he did. It looks like he booted the livecd to do a clean install, it detected that Natty was already installed and offered to just update the outdated files. So to make it short, insert disk, restart, click install. See what happens, nothing changes until it gets to where it sets up the partition. From what I remember, the installation checks for currently installed OS's.

Thanks, I'll try it.

 I am having a frustrating time with Natty.  Every time I shut down my computer and then reboot, I have **no sound**, I have to reboot into repair mode, fix broken files, reboot into XP (has sound), then shut down the PC and do all sorts of things, haven't a clue what helps:confused: I have sound now, but next time I may not.

Wish I left well enough alone and never installed Natty.

---

### Post by K_45 on 2011-05-07
I would clean install 10.04 LTS if it worked.

---

### Post by DayLite on 2011-05-07
> **K_45 said:**
> I would clean install 10.04 LTS if it worked.

I'm tempted with reservations :(

---

### Post by Thewhistlingwind on 2011-05-07
Seeing how no one bothered to tell you what the output actually means.

Most packages have "dependencies" that is, stuff they use to run. (So that they don't have to redo someone elses work to implement functionality.) In this case, your package manager can't install the packages required to give you the dependencies you need to install your program. With this in mind you should try and focus on a solution to install those packages. (You may need those specific versions in fact.) Linux users traditionally call this "Dependency hell"

PS. Have fun.

---

### Post by robert shearer on 2011-05-07
> **DayLite said:**
> I still am not clear as to what is said :confused:

"**running Natty**" Does that mean you were still on your '**active Ubuntu**' and inserted the live CD and were going to shut down and have it then reboot to the live CD?

Yes, **correct  :) **.  Just insert the cd and it will detect and ask if you want to open the package manager. Accept this and see what happens...

---

### Post by henz103 on 2011-05-08
Remove the PPA of OpenShot then try to install again.

---

### Post by DayLite on 2011-05-08
> **jramshu said:**
> I am just assuming exactly what he did. It looks like he booted the livecd to do a clean install, it detected that Natty was already installed and offered to just update the outdated files. So to make it short, insert disk, restart, click install. See what happens, nothing changes until it gets to where it sets up the partition. From what I remember, the installation checks for currently installed OS's.

I thought I was following what you said. I put in the live CD then shut down my computer. It rebooted to the CD, clicked, 'install', nothing happened so I chose to install alongside and it began to install!

I now have three partitions! 1.Windows XP 2.Natty (messed up upgrade) and 3. Natty fresh install.

Everything ran smoothly, all my programs installed, including OpenShot. I can still access the Natty upgrade while in the 'fresh install'. This 'fresh install' is not buggy.

When I boot into the upgrade one I have no sound and to get it back I have to boot into the repair mode, what a pain.

---

### Post by DayLite on 2011-05-08
> **henz103 said:**
> Remove the PPA of OpenShot then try to install again.

I did do that and it didn't help.

---

### Post by DayLite on 2011-05-09
> **robert shearer said:**
> Yes, **correct  :) **.  Just insert the cd and it will detect and ask if you want to open the package manager. Accept this and see what happens...

I did and I opened package manager.  Then what :confused:

It didn't take any other action or offer to update :(

---

### Post by DayLite on 2011-05-16
> **DayLite said:**
> I thought I was following what you said. I put in the live CD then shut down my computer. It rebooted to the CD, clicked, 'install', nothing happened so I chose to install alongside and it began to install!

I now have three partitions! 1.Windows XP 2.Natty (messed up upgrade) and 3. Natty fresh install.

Everything ran smoothly, all my programs installed, including OpenShot. I can still access the Natty upgrade while in the 'fresh install'. This 'fresh install' is not buggy.


**[SIZE=3][COLOR=Red]HELP[/COLOR][/SIZE]**:shock: I just discovered that my fresh install was installed on my external hard drive!
When it is disconnected I get an error message.

>  error: No such device: 70d123e41af-8099-e268c2bb3e.grub rescue>__

---

### Post by jtarin on 2011-05-16
> **DayLite said:**
> **[SIZE=3][COLOR=Red]HELP[/COLOR][/SIZE]**:shock: I just discovered that my fresh install was installed on my external hard drive!
When it is disconnected I get an error message.That's normal....don't be shocked.:P

---

### Post by DayLite on 2011-05-17
> **jtarin said:**
> That's normal....don't be shocked.:P

Solution please :confused:

How do I boot into Windows XP or my "upgraded Ubuntu 11.04, when I am not connected to my external drive?

---

### Post by Paddy Landau on 2011-05-17
Did you intend to install on the external hard drive or your internal drive?

---

### Post by DayLite on 2011-05-17
> **Paddy Landau said:**
> Did you intend to install on the external hard drive or your internal drive?

I was attempting to install it side by side by my XP and my upgraded 11.04 (that the upgrade went wrong). I did not expect it to be installed on my external drive. Finding that out was a shock.

---

### Post by Paddy Landau on 2011-05-17
So, to clarify (in case I misunderstood):

[LIST]
[*]You have XP and a bad installation of 11.04 on your hard drive.
[*]You have a working installation of 11.04 on your external drive.
[/LIST]
What you want:

[LIST]
[*]XP and a working installation of 11.04 on your hard drive.
[*]Remove 11.04 from your external drive.
[/LIST]
Here's the first suggested step.

[LIST=1]
[*]Back up any and all data.
[/LIST]
My suggestions are to do as follows.

[LIST]
[*]Remove 11.04 from your external drive
[*]Install 11.04 on your internal drive
[*]Restore grub
[/LIST]
My suggestions how to do this are as follows. (Did you remember to back up your data?)

[LIST=1]
[*]Remove your external hard drive.
[*]Boot from a Live CD.
[*]Plug in your external hard drive.
[*]Start GParted to look at your external drive.
[*]As required, delete partitions and expand remaining ones in your external drive.
[*]Dismount and remove your external hard drive.
[*]Install 11.04 on your hard drive *replacing* your existing 11.04.
[/LIST]
That should do it. Let me know if I have misunderstood anything.

---

