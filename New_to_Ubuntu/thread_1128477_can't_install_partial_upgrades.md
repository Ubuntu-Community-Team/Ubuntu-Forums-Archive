---
title: "can't install partial upgrades"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Matt26 on 2009-04-17
whenever i start the update manager now i get a message that says:

[B][I]Not all updates can be installed

Run a partial upgrade, to install as many upgrades as possible[/I][/B]

when i choose the run the partial upgrade it appears to start the process then the window that shows the progress of the upgrade closes after the first step of the upgrade is done and nothing happens.

any ideas on how to fix this?

thanks.

---

### Post by taurus on 2009-04-17
Close down the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by 73ckn797 on 2009-04-17
Maybe cannot fix but run in terminal:

```
sudo apt-get update
```

Then

```
sudo apt-get upgrade
```

See if that helps/ I have had similar issues.

---

### Post by Matt26 on 2009-04-17
> **taurus said:**
> Close down the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```

thanks, that helped- now i get this error message when i try to check for new updates (and there are still 2 updates grayed out that i can't select):

***W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634***

---

### Post by taurus on 2009-04-17
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)
[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA#Adding a PPA's keys to your system](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA#Adding a PPA's keys to your system)

---

### Post by Matt26 on 2009-04-17
thanks for the posts, but i am having difficult find the ppa page specific to my situation- any assistance would be greatly appreciated.

---

### Post by trlkly on 2009-04-17
Take a look at the file /etc/apt/sources.list. (Open it with Applications > Accessories > Text Editor). Look for the line that mentions "ppa.launchpad.net/". After the /, you should find the name of the ppa(s) you need. (My guess is it's do-core).

Look up the ppa(s) you found on [http://www.launchpad.net](http://www.launchpad.net), where you'll find the GPG key. Follow the instructions to install it.

---

### Post by Matt26 on 2009-04-18
> **trlkly said:**
> Take a look at the file /etc/apt/sources.list. (Open it with Applications > Accessories > Text Editor). Look for the line that mentions "ppa.launchpad.net/". After the /, you should find the name of the ppa(s) you need. (My guess is it's do-core).

Look up the ppa(s) you found on [http://www.launchpad.net](http://www.launchpad.net), where you'll find the GPG key. Follow the instructions to install it.

thanks, i followed those instructions and i am no longer getting that error message when i check for updates, however i still have 2 updates that are grayed out which i can't select- they are KDE related updates.

any ideas?

---

### Post by trlkly on 2009-04-18
Try updating using Synaptic. (System > Administration > Synaptic Package Manager) Just push the "Mark All Upgrades" button, and then the Apply Button.

It's been a while since I've done this, so you may get an error message, but I think it will be a more informative one, telling you what other things you need to install.

The only other thing I can think to do is to uninstall and reinstall the offending packages. Hopefully, they aren't an integral part of KDE, if you have to do that.

---

### Post by Matt26 on 2009-04-19
> **trlkly said:**
> Try updating using Synaptic. (System > Administration > Synaptic Package Manager) Just push the "Mark All Upgrades" button, and then the Apply Button.

It's been a while since I've done this, so you may get an error message, but I think it will be a more informative one, telling you what other things you need to install.

The only other thing I can think to do is to uninstall and reinstall the offending packages. Hopefully, they aren't an integral part of KDE, if you have to do that.

thanks for the suggestion- i tried that but the Apply button was still grayed out, so i don't think it actually set anything to be upgraded..

am i missing something?

---

### Post by taurus on 2009-04-19
Post the outputs of these two commands.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Matt26 on 2009-04-26
> **taurus said:**
> Post the outputs of these two commands.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

here is the output for each command.

```
sudo apt-get update
```
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Translation-en_CA               
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_CA            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_CA
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Translation-en_CA [3750B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Translation-en_CA           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_CA         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release.gpg
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Translation-en_CA [2731B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Translation-en_CA [3750B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_CA 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release                      
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Sources               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Sources         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 10.2kB in 1s (10.1kB/s)
Reading package lists... Done

```
sudo apt-get dist-upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  kdelibs-bin kdelibs5
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by Matt26 on 2009-04-28
> **Matt26 said:**
> here is the output for each command.

```
sudo apt-get update
```
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Translation-en_CA               
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_CA            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_CA
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Translation-en_CA [3750B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Translation-en_CA           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_CA         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release.gpg
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Translation-en_CA [2731B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Translation-en_CA [3750B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_CA 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release                      
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Sources               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Sources         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 10.2kB in 1s (10.1kB/s)
Reading package lists... Done

```
sudo apt-get dist-upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  kdelibs-bin kdelibs5
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

can anyone help with this?

thanks.

---

