---
title: "update-manager errors and now not functioning"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by mikodo on 2010-02-15
Hello everyone,

I received a kernel update in Karmic today, and now cannot update. If I try using the update manager or click on a Red Circle where the update notification icon is usually, I now get a message like this:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'restricted' is not known on line 9 in source list /etc/apt/sources.list.d/ddebs.list, E:The list of sources could not be read.'

I filed a really quick bug report in Launchpad under update-manager, (I had to leave for work). How can I post a /etc/apt/sources.list for you to see?

Thanks.

---

### Post by Satoru-san on 2010-02-15
```
gksudo gedit /etc/apt/sources.list
```
post this too /etc/apt/sources.list.d/ddebs.list

---

### Post by mikodo on 2010-02-15
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted universe multiverse main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted multiverse universe main
deb [http://ppa.launchpad.net/ubuntuone/beta/ubuntu](http://ppa.launchpad.net/ubuntuone/beta/ubuntu) karmic main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free

---

### Post by mikodo on 2010-02-15
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main 
restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse

---

### Post by mikodo on 2010-02-15
Thank you for your reply Satoru-san. I was hoping posting these list(s) may help people sort out what is going on with my system.

Mike

---

### Post by Satoru-san on 2010-02-15
> deb [http://ppa.launchpad.net/ubuntuone/beta/ubuntu](http://ppa.launchpad.net/ubuntuone/beta/ubuntu) karmic mainyou have a ppa in your sources list o_O

That needs to go away.

EDIT: how long ago did you add that one?

---

### Post by mikodo on 2010-02-15
> **Satoru-san said:**
> you have a ppa in your sources list o_O

That needs to go away.

EDIT: how long ago did you add that one?

I didn't know that it was even there. So, I cannot answer your question about when I added it.

Can it be easily removed?

Thanks.

EDIT     I was playing around with Ubuntu One maybe 5 weeks ago, and didn't totally understand it, so probably it was then that I added it.

---

### Post by Satoru-san on 2010-02-15
yea, ppa's have to be entered in a special way, I dont know how I dont use ubuntu, but you could find it by searching the forums or google.

As far as removing it you can either gedit it with the command ^ or you can nano the file in the terminal and add a # sign to comment it out, dont delete it just in case you choose to add it to ppa you will want to know the repository.

Then you need to sync apt, I cant remember right now, I think apt-get update.

---

### Post by mikodo on 2010-02-15
Hello,

I removed the beta ubuntu one from my sources list. After that it asked me to reload and update and I received this notification:

 E: Type 'restricted' is not known on line 9 in source list /etc/apt/sources.list.d/ddebs.list
E: Unable to lock the list directory

Seems the difficulty remains still with my system.

Thank you.

---

### Post by mikodo on 2010-02-15
> **Satoru-san said:**
> yea, ppa's have to be entered in a special way, I dont know how I dont use ubuntu, but you could find it by searching the forums or google.

As far as removing it you can either gedit it with the command ^ or you can nano the file in the terminal and add a # sign to comment it out, dont delete it just in case you choose to add it to ppa you will want to know the repository.

Then you need to sync apt, I cant remember right now, I think apt-get update.


Woops! I should have waited for your reply it seems; I went ahead and deleted it from the Software Sources. Oh, well.....

---

### Post by Cheezespread on 2010-02-15
the sources.list file has 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main 
restricted universe multiverse 

in different lines. Try deleting the space and correcting them.

And to update the sources using  ```
sudo apt-get update
```

---

### Post by Cheezespread on 2010-02-15
> **mikodo said:**
> deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse
[B]deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main 
restricted universe multiverse[/B]
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse

This one !

---

### Post by mikodo on 2010-02-15
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed main restricted universe multiverse

---

### Post by Cheezespread on 2010-02-15
So , Are you still getting the error when you try to update ?

---

### Post by mikodo on 2010-02-15
> **Cheezespread said:**
> So , Are you still getting the error when you try to update ?

No! The RED icon is gone after clicking on it and trying to find updates. The red icon disappeared and when I went to the regular update manager and updated it performed as it used to reading that everything is up to date.

So, I think that fixed that problem; Thanks

---

### Post by Satoru-san on 2010-02-15
We are glad we could help, mark as solved so others can benifit.

---

### Post by mikodo on 2010-02-15
> **Satoru-san said:**
> We are glad we could help, mark as solved so others can benifit.

You bet I will!

Thank you Satoru-san and Cheezespread.

Mike

---

### Post by mikodo on 2010-02-15
> **Cheezespread said:**
> So , Are you still getting the error when you try to update ?


mikodo@mikodo-desktop:~$ sudo apt-get update
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_US           
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic Release.gpg                                 
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/main Translation-en_US                      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/restricted Translation-en_US                
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/universe Translation-en_US                  
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/multiverse Translation-en_US                
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates Release.gpg                         
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/main Translation-en_US              
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/restricted Translation-en_US        
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/universe Translation-en_US          
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/multiverse Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security Release.gpg                        
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/main Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/restricted Translation-en_US       
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/universe Translation-en_US         
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/multiverse Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release.gpg                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed Release.gpg                        
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/main Translation-en_US             
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/restricted Translation-en_US       
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/universe Translation-en_US         
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/multiverse Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Translation-en_US
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic Release                           
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates Release                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Translation-en_US        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security Release                  
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed Release                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources    
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/main Packages                     
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/restricted Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/universe Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/multiverse Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/restricted Packages      
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/universe Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/main Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/restricted Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/universe Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/multiverse Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/restricted Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/universe Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/multiverse Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/main Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/restricted Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/universe Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/multiverse Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/main Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/restricted Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/main Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/restricted Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/universe Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/multiverse Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/main Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/restricted Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Packages
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/multiverse Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/main Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/restricted Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/universe Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic/multiverse Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/main Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/restricted Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/main Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/restricted Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/universe Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-security/multiverse Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/main Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/restricted Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/universe Packages
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) karmic-proposed/multiverse Packages
Reading package lists... Done
mikodo@mikodo-desktop:~$

---

