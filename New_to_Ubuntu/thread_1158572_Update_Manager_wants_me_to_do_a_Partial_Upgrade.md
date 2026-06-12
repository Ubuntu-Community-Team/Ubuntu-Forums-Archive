---
title: "Update Manager wants me to do a Partial Upgrade?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Zenmij on 2009-05-13
Has there just been an enormous amount of updates realeased? 

I just noticed my hard drive going into overdrive, the only time it usually does this when idle is when the update manager is working. So sure enough it just popped up and there as an update for just about every app and lib. And it recommends I do a partial upgrade??

What is this?

---

### Post by whoop on 2009-05-13
What version are you running?
Type in terminal:
```

cat /etc/issue

```

---

### Post by Zenmij on 2009-05-13
```
Ubuntu 9.04 \n \l
```

---

### Post by whoop on 2009-05-13
You can run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
Hit "n" for now (so you don't do the patial upgrade), **Don't** hit Enter or "y". Dist-upgrade will output what the partial upgrade is trying to upgrade.

---

### Post by Zenmij on 2009-05-13
Looks like it might have been QT4. I don't even use it, so I safely marked it for uninstallation and theres now just a number of miscellaneous openGL fixes. Its gotten rid of the partial upgrade message anyway so thanks.

```
apturl compizconfig-backend-gconf ekiga gnome-about gnome-desktop-data
  libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa
  libglu1-mesa-dev libgnome-desktop-2-11 libical0 mesa-common-dev mesa-utils
  wine
```

Thats what is being upgraded now, bit I assume if I hadn't removed QT4 - it would have included the enormous list that required partial upgrade.

---

### Post by whoop on 2009-05-13
As long as there isn't a partial upgrade. I always check partial upgrades with apt-get dist-upgrade. Just to make sure the upgrade doesn't (try) remove anything crucial.

---

### Post by Zenmij on 2009-05-13
Big Thanks whoop, see above message :D

---

### Post by Zenmij on 2009-05-14
m

---

### Post by waltclay on 2009-05-17
I have the partial update problem.

sudo apt-get update
resulted in:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

sudo apt-get dist-upgrade
I chose N to decline upgrade

Still have partial update problem.

---

### Post by CPImmanuel on 2009-05-18
I have the same problem. Here is what I get when I try the suggestions stated in this other forums:
paul@paul-laptopT61320G:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for paul: 
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release.gpg
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Translation-en_US     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Packages              
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources                    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Fetched 308B in 1s (188B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  akregator ark cairo-dock-plug-ins dolphin dragonplayer gwenview kaddressbook
  kalgebra kalzium kamera kate kde-window-manager kde-zeroconf kdebase-bin
  kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5
  kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdemultimedia-kio-plugins
  kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs5
  kdewebdev-kde4 kdm kfilereplace-kde4 kfind kgeography khelpcenter4
  kimagemapeditor-kde4 klinkstatus-kde4 klipper kmag kmail kmix kmousetool
  knotes konqueror konqueror-nsplugins konsole kontact kopete korganizer krdc
  krfb ksnapshot ksysguard ktimetracker ktouch kwalletmanager kwrite libkcddb4
  libkdecorations4 libkdeedu4 libkdepim4 libkholidays4 libkleo4 libkonq5
  libkpgp4 libksieve4 libkwineffects1 libmimelib4 libokularcore1 linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  nvidia-common okular okular-extra-backends python-kde4 systemsettings
0 upgraded, 0 newly installed, 0 to remove and 79 not upgraded.
paul@paul-laptopT61320G:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release.gpg                      
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages          
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Fetched 308B in 0s (349B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
W: You may want to run apt-get update to correct these problems



Any comments? or ideas? 

Thanks, 
Paul

---

### Post by cariboo on 2009-05-18
Could you please enclose the output of the commands you ran in [noparse]```
 
```[/noparse] tags, many people will not bother reading such a long post.

---

### Post by CPImmanuel on 2009-05-18
Sorry... Did not mean to include that much info.. Here is the abbreviated response that I got from the commands:
From the apt-get update:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
W: You may want to run apt-get update to correct these problems
Reading package lists... Done. 

Other than this, I get the partial update error when I try to run update manager. It tells me that the error may be temporary and to try again later. I have been getting this error for three days, so I have to assume that it is not a transient error. 

Thanks. 

Paul

---

### Post by bacardiandwatermelon on 2009-05-18
I think this should do the trick..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9423A34CCA967634
```

[http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/](http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/)

---

### Post by CPImmanuel on 2009-05-18
Thanks... That fixed the problem of getting errors with apt update, but trying to use the Update manager still gives me the following message:
---------------------------
Could not calculate the upgrade



An unresolvable problem occurred while calculating the upgrade.



 This can be caused by:

 * Upgrading to a pre-release version of Ubuntu

 * Running the current pre-release version of Ubuntu

 * Unofficial software packages not provided by Ubuntu



This is most likely a transient problem, please try again later.
-----------------------------

Any ideas?
Thanks, Paul

---

### Post by waltclay on 2009-05-23
And so it goes with help in the ubuntu community: nowhere.

---

### Post by raymondh on 2009-05-23
> **waltclay said:**
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

Hello Waltclay,

Is the above the problem?  If not, please post any new error ... maybe in a new thread.

In a terminal, type (or copy/paste) and enter

```

 gpg --keyserver subkeys.pgp.net --recv 60D11217247D1CFF
```

The next command is

```
 gpg --export --armor 60D11217247D1CFF | sudo apt-key add - 
```

Then,

```
sudo apt-get update
sudo apt-get upgrade
```

Hope this helps you.

Regards,

---

