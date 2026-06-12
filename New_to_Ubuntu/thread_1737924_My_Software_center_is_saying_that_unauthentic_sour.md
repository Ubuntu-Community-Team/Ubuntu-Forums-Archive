---
title: "My Software center is saying that unauthentic source, please help, iv been cracking"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by pranjal_dude007 on 2011-04-24
the software center doesnt let me download and keeps saying restricted and cant download due to unauthentic source, im a beginner in ubuntu. my version is 10.10 please help iv been breaking my head for 3 days

---

### Post by Elfy on 2011-04-24
Please open a terminal and run these commands - paste the outputs. Please also use code tags - that is put [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse]at the end.

```
sudo apt-get update
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

---

### Post by pranjal_dude007 on 2011-04-24
Err [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_IN           
  Unable to connect to 192.168.100.10:3128:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
  Could not connect to 192.168.100.10:3128 (192.168.100.10). - connect (110: Connection timed out)
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
  Unable to connect to 192.168.100.10:3128:
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN           
  Unable to connect to 192.168.100.10:3128:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                         
  Could not connect to 192.168.100.10:3128 (192.168.100.10). - connect (110: Connection timed out)
Err [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
  Unable to connect to 192.168.100.10:3128:
Err [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_IN             
  Unable to connect to 192.168.100.10:3128:
Err [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
  Unable to connect to 192.168.100.10:3128:
Err [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_IN         
  Unable to connect to 192.168.100.10:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Could not connect to 192.168.100.10:3128 (192.168.100.10). - connect (110: Connection timed out)
Err [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/) maverick/main Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/) maverick/main Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en     
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Unable to connect to 192.168.100.10:3128:
Ign [http://deb.opera.com](http://deb.opera.com) stable Release
Ign [http://deb.opera.com](http://deb.opera.com) stable Release
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release.gpg
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_IN
  Unable to connect to 192.168.100.10:3128:
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
  Unable to connect to 192.168.100.10:3128:
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources
  Unable to connect to 192.168.100.10:3128:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources
  Unable to connect to 192.168.100.10:3128:
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/main i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
  Unable to connect to 192.168.100.10:3128:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  Unable to connect to 192.168.100.10:3128:
Err [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
  Unable to connect to 192.168.100.10:3128:
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
  Unable to connect to 192.168.100.10:3128:
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/restricted i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/main i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/multiverse i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/universe i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
  Unable to connect to 192.168.100.10:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
  Unable to connect to 192.168.100.10:3128:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to 192.168.100.10:3128 (192.168.100.10). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to 192.168.100.10:3128 (192.168.100.10). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to 192.168.100.10:3128 (192.168.100.10). - connect (110: Connection timed out)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/Release.gpg](http://packages.medibuntu.org/dists/maverick/Release.gpg)  Could not connect to 192.168.100.10:3128 (192.168.100.10). - connect (110: Connection timed out)

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en.bz2](http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en_IN.bz2](http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en.bz2](http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en_IN.bz2](http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.canonical.com/dists/maverick/Release.gpg](http://archive.canonical.com/dists/maverick/Release.gpg)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/Release.gpg)  Could not connect to 192.168.100.10:3128 (192.168.100.10). - connect (110: Connection timed out)

W: Failed to fetch [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release.gpg](http://deb.opera.com/opera/dists/stable/Release.gpg)  Could not connect to 192.168.100.10:3128 (192.168.100.10). - connect (110: Connection timed out)

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/i18n/Translation-en.bz2](http://deb.opera.com/opera/dists/stable/non-free/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/i18n/Translation-en_IN.bz2](http://deb.opera.com/opera/dists/stable/non-free/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/Release.gpg](http://deb.opera.com/opera-beta/dists/stable/Release.gpg)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/non-free/i18n/Translation-en.bz2](http://deb.opera.com/opera-beta/dists/stable/non-free/i18n/Translation-en.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/non-free/i18n/Translation-en_IN.bz2](http://deb.opera.com/opera-beta/dists/stable/non-free/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/source/Sources.gz](http://packages.medibuntu.org/dists/maverick/free/source/Sources.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/maverick/non-free/source/Sources.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/maverick/non-free/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/dists/maverick/partner/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Unable to connect to 192.168.100.10:3128:

E: Some index files failed to download, they have been ignored, or old ones used instead.
pranjal@pranjal-HP-Mini-210:~$

---

### Post by AlexDudko on 2011-04-24
Do you have an Ubuntu mirror located in your local network? If not - your Internet connection is probably not properly setup.

---

### Post by earthpigg on 2011-04-24
What is unique or unusual about your internet connection?

**OR**

What crazy thing did you do?

---

