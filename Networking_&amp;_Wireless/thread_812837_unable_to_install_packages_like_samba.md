---
title: "unable to install packages like samba"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by babyrajT on 2008-05-30
Hi All,

I cannot install packages like samba,Firefox mail....When installing samba ,getting an error "The application conflict with other installed softwares ,Switch to synaptic package manager to resolve this" Can any one help me?


Thanks

---

### Post by hal10000 on 2008-05-30
you should start synaptic [COLOR="Red"](ALT+F2 ---> gksudo synaptic)[/COLOR]) and try to remove the package(s) which conflict with Samba (or with other packages you want to install.
The synaptic package manager tells you which other packages are in conflict, and i guess it removes them if you go on.

---

### Post by babyrajT on 2008-05-30
I have checked with synaptic package manager.There is no packages installed named samba.

---

### Post by babyrajT on 2008-05-30
It shows.....



home@home-desktop:~$ sudo apt-get install samba
[sudo] password for nsg:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
home@home-desktop:~$ 



Thanks

---

### Post by phos4us on 2008-05-30
> **babyrajT said:**
> I have checked with synaptic package manager.There is no packages installed named samba.

What happens if you try to install Samba with Synaptic?

Regards
Andrew

---

### Post by phos4us on 2008-05-30
> **babyrajT said:**
> It shows.....



home@home-desktop:~$ sudo apt-get install samba
[sudo] password for nsg:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
home@home-desktop:~$ 



Thanks

This locking issue is typically caused when more than one program used for installing is running. Double check that you do not have any other package managers running.

Regards
Andrew

---

### Post by babyrajT on 2008-05-30
nsg@nsg-desktop:~$ sudo apt-get update
[sudo] password for nsg:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_IN               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Get:2 [http://falcon.landure.fr](http://falcon.landure.fr) feisty Release.gpg [189B]                       
Ign [http://falcon.landure.fr](http://falcon.landure.fr) feisty/amsn Translation-en_IN                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                    
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IN
Hit [http://falcon.landure.fr](http://falcon.landure.fr) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release   
Hit [http://falcon.landure.fr](http://falcon.landure.fr) feisty/amsn Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://falcon.landure.fr](http://falcon.landure.fr) feisty/amsn Sources
Fetched 3B in 2s (1B/s)  
Reading package lists... Done
nsg@nsg-desktop:~$ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has no installation candidate
nsg@nsg-desktop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  samba-common
E: Package samba has no installation candidate
nsg@nsg-desktop:~$

---

### Post by ilrudie on 2008-05-30
```
sudo apt-get install samba-common
```

---

### Post by babyrajT on 2008-05-30
nsg@nsg-desktop:~$ sudo apt-get install samba-common
[sudo] password for nsg:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package samba-common has no installation candidate
nsg@nsg-desktop:~$ 



Thanks

---

### Post by hal10000 on 2008-05-30
It seems as if you didn't activate all package repositories. You can enable repositories with Synaptic --->Settings --->Repositories (or similar) and activate all main restricted universe and multiverse and possibly also the third party repos.

---

### Post by babyrajT on 2008-05-30
Hi,


Its worked .Thanks you so much for this help.Its Highly appretiated

Thanks
BabyrajT

---

