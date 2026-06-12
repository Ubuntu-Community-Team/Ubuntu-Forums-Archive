---
title: "Package Manager doesn't work anymore"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by sambando on 2009-01-15
Hi,

      cannot update, remove, anything. Broken filter in synaptic doesn't work, removing the confliting packages doesn't work...

the message: **E: /var/cache/apt/archives/acroread-debian-files_0.0.24medibuntu1.1_i386.deb: trying to overwrite `/usr/bin/acroread', which is also in package acroread**

this is my sourcelist in /etc/apt/

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports universe main multiverse restricted #Added by software-properties
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
#deluge-torrent
deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) intrepid main restricted universe multiverse
deb-src [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) intrepid main restricted universe multiverse
#empathy
deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) intrepid main
deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) intrepid main

 Please, help! I would like to reinstall package manager and/or update manager.

thank you very much

running Intrepid, it


logs:

bruno@bruno-laptop:~$ sudo apt-get -f install        
Reading package lists... Done                        
Building dependency tree                             
Reading state information... Done                    
Correcting dependencies... Done                      
The following extra packages will be installed:      
  acroread-debian-files                              
The following NEW packages will be installed:        
  acroread-debian-files                              
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.                                            
2 not fully installed or removed.                    
Need to get 0B/13.9kB of archives.                   
After this operation, 135kB of additional disk space will be used.                                        
Do you want to continue [Y/n]? y                     
(Reading database ... 229678 files and directories currently installed.)                                  
Unpacking acroread-debian-files (from .../acroread-debian-files_0.0.24medibuntu1.1_i386.deb) ...          
dpkg: error processing /var/cache/apt/archives/acroread-debian-files_0.0.24medibuntu1.1_i386.deb (--unpack):                                                   
 trying to overwrite `/usr/bin/acroread', which is also in package acroread                               
Processing triggers for menu ...                     
Errors were encountered while processing:            
 /var/cache/apt/archives/acroread-debian-files_0.0.24medibuntu1.1_i386.deb                                
E: Sub-process /usr/bin/dpkg returned an error code (1)                                                   
bruno@bruno-laptop:~$ sudo apt-get update            
[sudo] password for bruno:                           
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy Release.gpg                       
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US            
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US      
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy Release                           
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Packages                     
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Packages               
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Packages                     
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs                                                 
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Packages               
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs                                                 
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy Release.gpg   
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/main Translation-en_US                                             
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/restricted Translation-en_US                                       
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/universe Translation-en_US                                         
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/multiverse Translation-en_US                                       
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy Release       
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/main Packages 
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/restricted Packages                                                
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/main Sources  
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/restricted Sources                                                 
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/universe Packages                                                  
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/universe Sources                                                   
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/multiverse Packages                                                
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) gutsy/multiverse Sources                                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US                                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                                              
W: Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs                                  

W: Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs                            

E: Some index files failed to download, they have been ignored, or old ones used instead.                 
bruno@bruno-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  acroread-dictionary-de: Depends: acroread-debian-files (>= 0.0.23) but it is not installed
  acroread-l10n-de: Depends: acroread-debian-files (>= 0.0.23) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by cariboo on 2009-01-15
I can't tell whether you are running Gutsy or Interpid, but your problem has nothing to do with the package manager. Hopefully you backed up your /etc/apt/sources.list before adding all the Gutsy repositories.

The first thing to do ist to go to System-->Administration-->Software Sources. and deselect the CD-Rom. The next thing is to change all the Gutsy references to Intrepid. To do this open gedit as root and edit the /etc/apt/sources.list file. Press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

Use the search and replace function to change all references to Gutsy to Intrepid. Save the file, then in a terminal type:

```
sudo apt-get update
```

This should update your sources list. There are times that the Medibuntu repositories are down, this is what your problem probably is.

Jim

---

### Post by sambando on 2009-01-15
Thanks, cariboo, but it doens't work!

same problem!

any idea?

[]s

---

### Post by alienexplorers on 2009-01-15
Have you tried running from terminal:
> sudo apt-get -f install

---

### Post by sambando on 2009-01-15
Hi, tried this before and now: doesn't work!

thx!

---

### Post by bodhi.zazen on 2009-01-15
It appears you are mixing gutsy and intrepid repositories.

Can you post the entire contents of /etc/apt/sources.list ?

---

### Post by sambando on 2009-01-15
Thx, bodhi.zazen,

this is my source.list

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports universe main restricted multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
#deluge-torrent
deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) intrepid main restricted universe multiverse
deb-src [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) intrepid main restricted universe multiverse
#empathy
deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) intrepid main
deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) intrepid main

---

### Post by sambando on 2009-01-15
The problems seems to be here:

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  acroread-dictionary-de: Depends: acroread-debian-files (>= 0.0.23) but it is not installed
  acroread-l10n-de: Depends: acroread-debian-files (>= 0.0.23) but it is not installed
E: Unmet dependencies. Try using -f.

I wonder if I cannot exclude acroread-related, synaptic can't do it nor repair it

---

### Post by sambando on 2009-01-16
I've just use sudo apt-cdrom add

and then apt-get update

received this message:

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by sambando on 2009-01-16
another messag when trying to use package manager

E: /var/cache/apt/archives/acroread-debian-files_0.0.24medibuntu1.1_i386.deb: trying to overwrite `/usr/bin/acroread', which is also in package acroread

---

