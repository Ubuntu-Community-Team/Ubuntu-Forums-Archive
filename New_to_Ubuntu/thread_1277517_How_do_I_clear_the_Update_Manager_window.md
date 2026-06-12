---
title: "How do I clear the Update Manager window?"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by bwallum on 2009-09-28
Hi

I have a file shown in Update Manager window that will not install. It appears to not have dependency files with it.

How can I clear this item from the list?

---

### Post by grturner on 2009-09-28
well... if you open synaptic package and find that package within synaptic, you can lock the version from within, and then it will *never* show up under update manager, though if they ever fix the dependencies you would never know and not update it.

---

### Post by philinux on 2009-09-28
> **bwallum said:**
> Hi

I have a file shown in Update Manager window that will not install. It appears to not have dependency files with it.

How can I clear this item from the list?

Would be easier to fix with the information from apt. Either screenshot of update manager or from terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bwallum on 2009-09-28
> **philinux said:**
> Would be easier to fix with the information from apt. Either screenshot of update manager or from terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

bob@bob-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_GB              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_GB                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_GB              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_GB        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Translation-en_GB          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Translation-en_GB    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Translation-en_GB      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Translation-en_GB    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_GB      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_GB  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release.gpg            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Translation-en_GB 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Translation-en_GB
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release                          
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ubuntu-desktop
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by cb951303 on 2009-09-28
I would try: uninstall ubuntu-desktop > update && upgrade > reinstall ubuntu-desktop

---

### Post by philinux on 2009-09-28
> **cb951303 said:**
> I would try: uninstall ubuntu-desktop > update && upgrade > reinstall ubuntu-desktop

Yep that will do it or run synaptic and click custom filters then upgradable upstream. Mark all upgrades.

By the way BobWallum your posting in the wrong forum.
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

---

### Post by bwallum on 2009-09-28
> **philinux said:**
> By the way BobWallum your posting in the wrong forum.

Oops, thought it was a general question...

Anyway I have taken the plunge and upon reading in synaptic that the upgrade changed to Ubuntu Software Centre from Ubuntu Store I decided to upgrade through synaptic.

I guessed that you would have said that seeing the explanation. All appears well and I now have nice Departments in my Ubuntu Software Centre (except that it's spelt wrong of course, another job for I18N :))

Thanks all for the steers...

---

