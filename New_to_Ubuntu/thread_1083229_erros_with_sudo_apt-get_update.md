---
title: "erros with: sudo apt-get update"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Cesaar on 2009-02-28
I'm trying to install alarm-clock-applet( [http://alarm-clock.pseudoberries.com/#intro]("http://alarm-clock.pseudoberries.com/#intro") )by using the repositories. I added the repositories and the authentication key. so then I ask it to update with ```
sudo apt-get update
```

and I'm getting this:

```
cesar@cesar-laptop:~$ sudo apt-get update
Hit http://mx.archive.ubuntu.com intrepid Release.gpg
Ign http://mx.archive.ubuntu.com intrepid/main Translation-en_US               
Ign http://mx.archive.ubuntu.com intrepid/restricted Translation-en_US         
Hit http://archive.canonical.com intrepid Release.gpg                          
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Hit http://archive.canonical.com intrepid Release                              
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ppa.launchpad.net intrepid Release.gpg                    
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Hit http://ppa.launchpad.net intrepid Release.gpg                    
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Hit http://ppa.launchpad.net intrepid Release.gpg                    
Hit http://archive.canonical.com intrepid/partner Packages                     
Ign http://mx.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://mx.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://mx.archive.ubuntu.com intrepid-updates Release.gpg        
Ign http://mx.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://mx.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://mx.archive.ubuntu.com intrepid Release                    
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release             
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release                        
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://archive.canonical.com intrepid/partner Sources                      
Get:2 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://security.ubuntu.com intrepid-security/restricted Packages        
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://mx.archive.ubuntu.com intrepid-updates Release
Hit http://mx.archive.ubuntu.com intrepid/main Packages
Hit http://mx.archive.ubuntu.com intrepid/restricted Packages
Hit http://ppa.launchpad.net intrepid Release
Hit http://mx.archive.ubuntu.com intrepid/main Sources
Hit http://mx.archive.ubuntu.com intrepid/restricted Sources
Hit http://mx.archive.ubuntu.com intrepid/universe Packages
Hit http://mx.archive.ubuntu.com intrepid/universe Sources
Hit http://mx.archive.ubuntu.com intrepid/multiverse Packages
Hit http://mx.archive.ubuntu.com intrepid/multiverse Sources
Hit http://ppa.launchpad.net intrepid Release
Get:3 http://ppa.launchpad.net intrepid Release [27.6kB]
Ign http://ppa.launchpad.net intrepid/main Packages   
Ign http://ppa.launchpad.net intrepid/main Sources
Ign http://ppa.launchpad.net hardy/main Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/main Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/main Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://mx.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Sources
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Sources
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://mx.archive.ubuntu.com intrepid-updates/multiverse Sources           
Fetched 3B in 6s (0B/s)                                                        
Reading package lists... Done

```

it seems as if it were ignoring (Ign) my requests to update.. not sure if that's what's going on.

Please help me. Thanks ;]

---

### Post by albinootje on 2009-02-28
> **Cesaar said:**
> 
[CODE]cesar@cesar-laptop:~$ sudo apt-get update
Hit http://mx.archive.ubuntu.com intrepid Release.gpg
Ign http://mx.archive.ubuntu.com intrepid/main Translation-en_US               
Ign http://mx.archive.ubuntu.com intrepid/restricted Translation-en_US  

It is probably because there's simply no updates available this time. :)

---

### Post by forger on 2009-03-02
Use the main servers:
```
sudo sed -i 's#http://\S*archive.\ubuntu\.com#http://archive.ubuntu.com#' /etc/apt/sources.list

```
And disable the translation:
```
echo 'APT::Acquire::Translation "none";' | sudo tee -a /etc/apt/apt.conf.d/custom-no-translation
```

Then update:
```
sudo apt-get update
```

---

### Post by Zvezdichko on 2009-03-02
And of course, use apt-get upgrade to upgrade your system. You may as well use aptitude safe-upgrade and aptitude dist-upgrade to fix broken dependencies.

---

