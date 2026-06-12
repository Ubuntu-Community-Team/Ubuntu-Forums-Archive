---
title: "installing gdm2 setup"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Primus1 on 2010-06-27
Wanting to install gdm2setup in Lucid so I can easily change login screen etc. Ran this:

[INDENT]sudo add-apt-repository ppa:gdm2setup/gdm2setup
 sudo apt-get update
 sudo apt-get install python-gdm2setup


Which gave this:


dave@dave-desktop:~$ sudo add-apt-repository ppa:gdm2setup/gdm2setup
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 33E1C2F5E880004C06B6696B1780999033C3C104
gpg: requesting key 33C3C104 from hkp server keyserver.ubuntu.com
sudo apt-get update
sudo apt-get install python-gdm2setup
gpg: key 33C3C104: public key "Launchpad GDM2Setup" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
dave@dave-desktop:~$ sudo apt-get update
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]
Ign [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/) lucid/main Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg                             
Get: 2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB [62.9kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/gdm2setup/ppa/ubuntu/](http://ppa.launchpad.net/gdm2setup/ppa/ubuntu/) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_GB
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_GB              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Get: 4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB [2,332B]
Get: 5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB [33.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get: 6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB [37.7kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release                         
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Get: 7 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [603B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 195kB in 1s (178kB/s)
W: Failed to fetch [http://ppa.launchpad.net/gdm2setup/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gdm2setup/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
dave@dave-desktop:~$ sudo apt-get install python-gdm2setup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace libprocessui4 libtaskmanager4 libqimageblitz4
  libkscreensaver5 libsolidcontrolifaces4 plasma-widgets-workspace
  libplasma-geolocation-interface4 libksgrd4 kdebase-workspace-bin
  libkworkspace4 libplasmagenericshell4 libkfontinst4 libkephal4
  kdebase-workspace-data ksysguardd libplasmaclock4 libweather-ion4
  kdebase-workspace-kgreet-plugins libsolidcontrol4
  libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  python-gdm2setup
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 26.7kB of archives.
After this operation, 197kB of additional disk space will be used.
Get: 1 [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/) lucid/main python-gdm2setup 0.5.3-lucid-1 [26.7kB]
Fetched 26.7kB in 0s (100kB/s)      
Selecting previously deselected package python-gdm2setup.
(Reading database ... 157567 files and directories currently installed.)
Unpacking python-gdm2setup (from .../python-gdm2setup_0.5.3-lucid-1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
Setting up python-gdm2setup (0.5.3-lucid-1) ...

Processing triggers for python-support ...
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
dave@dave-desktop:~$ 



#######################


Looks worrying, have I done something wrong, or is it ok?

[/INDENT]

---

### Post by cariboo on 2010-06-27
Check you /etc/apt/sources.list. according to this error:

> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages 

You have duplicate sources in the file.

---

### Post by Primus1 on 2010-06-28
Hi, I ran "apt-get update" like it suggested in the last line. Is the problem corrected now?

---

