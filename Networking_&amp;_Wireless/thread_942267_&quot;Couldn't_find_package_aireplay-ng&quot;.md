---
title: "&quot;Couldn't find package aireplay-ng&quot;"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by jijin on 2008-10-09
I'm trying to follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=514723") on how to use aircrack but I've stopped before I can begin. Apt-get can't find aireplay-ng. it does install all the rest if I take just aireplay-ng out. 

EDIT: It can't find airodump-ng or airmon-ng either.

```
jijin@pinja:~$ sudo apt-get install aircrack-ng aireplay-ng airmon-ng airodump-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aireplay-ng
```

result of apt-get update to see the repos I have:


```
jijin@pinja:~$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://packages.medibuntu.org hardy Release.gpg                            
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg                   
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://archive.canonical.com hardy Release                                 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com hardy-proposed Release.gpg                    
Ign http://us.archive.ubuntu.com hardy-proposed/restricted Translation-en_US   
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://repository.cairo-dock.org hardy Release.gpg                         
Ign http://repository.cairo-dock.org hardy/cairo-dock Translation-en_US        
Ign http://us.archive.ubuntu.com hardy-proposed/main Translation-en_US         
Ign http://us.archive.ubuntu.com hardy-proposed/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com hardy-proposed/universe Translation-en_US     
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://security.ubuntu.com hardy-security/main Packages                    
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://us.archive.ubuntu.com hardy-backports Release                       
Hit http://us.archive.ubuntu.com hardy-proposed Release                        
Ign http://repository.cairo-dock.org hardy Release                             
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/main Sources                            
Hit http://us.archive.ubuntu.com hardy/restricted Sources                      
Hit http://us.archive.ubuntu.com hardy/universe Packages                       
Ign http://repository.cairo-dock.org hardy/cairo-dock Packages                 
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/multiverse Sources            
Hit http://us.archive.ubuntu.com hardy-updates/main Packages         
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages   
Hit http://us.archive.ubuntu.com hardy-updates/main Sources          
Hit http://repository.cairo-dock.org hardy/cairo-dock Packages       
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources    
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://packages.medibuntu.org hardy Release
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages           
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages             
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy-proposed/restricted Packages            
Hit http://us.archive.ubuntu.com hardy-proposed/main Packages                  
Hit http://us.archive.ubuntu.com hardy-proposed/multiverse Packages            
Hit http://us.archive.ubuntu.com hardy-proposed/universe Packages              
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
```

Any thoughts?

---

### Post by Heero_Yuy_X on 2009-12-02
I don't remember what was the repository for the aircrack-ng but check it again, it might be the problem...

Airodump-ng, aireplay-ng, airmon-ng are all installed when you install aircrack-ng automatically..

If that doesn't work, try purging aircrack-ng and installing it again ( after you checked for the right repository of course.. )

---

### Post by ramoj02 on 2009-12-07
> **jijin said:**
> I'm trying to follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=514723") on how to use aircrack but I've stopped before I can begin. Apt-get can't find aireplay-ng. it does install all the rest if I take just aireplay-ng out. 

EDIT: It can't find airodump-ng or airmon-ng either.

```
jijin@pinja:~$ sudo apt-get install aircrack-ng aireplay-ng airmon-ng airodump-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aireplay-ng
```

result of apt-get update to see the repos I have:


```
jijin@pinja:~$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://packages.medibuntu.org hardy Release.gpg                            
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg                   
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://archive.canonical.com hardy Release                                 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com hardy-proposed Release.gpg                    
Ign http://us.archive.ubuntu.com hardy-proposed/restricted Translation-en_US   
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://repository.cairo-dock.org hardy Release.gpg                         
Ign http://repository.cairo-dock.org hardy/cairo-dock Translation-en_US        
Ign http://us.archive.ubuntu.com hardy-proposed/main Translation-en_US         
Ign http://us.archive.ubuntu.com hardy-proposed/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com hardy-proposed/universe Translation-en_US     
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://security.ubuntu.com hardy-security/main Packages                    
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://us.archive.ubuntu.com hardy-backports Release                       
Hit http://us.archive.ubuntu.com hardy-proposed Release                        
Ign http://repository.cairo-dock.org hardy Release                             
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/main Sources                            
Hit http://us.archive.ubuntu.com hardy/restricted Sources                      
Hit http://us.archive.ubuntu.com hardy/universe Packages                       
Ign http://repository.cairo-dock.org hardy/cairo-dock Packages                 
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/multiverse Sources            
Hit http://us.archive.ubuntu.com hardy-updates/main Packages         
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages   
Hit http://us.archive.ubuntu.com hardy-updates/main Sources          
Hit http://repository.cairo-dock.org hardy/cairo-dock Packages       
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources    
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://packages.medibuntu.org hardy Release
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages           
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages             
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy-proposed/restricted Packages            
Hit http://us.archive.ubuntu.com hardy-proposed/main Packages                  
Hit http://us.archive.ubuntu.com hardy-proposed/multiverse Packages            
Hit http://us.archive.ubuntu.com hardy-proposed/universe Packages              
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
```

Any thoughts?

Just type <sudo apt-get install aircrack-ng>
then... <sudo apt-get install macchanger> (this is optional)

---

### Post by Heero_Yuy_X on 2009-12-08
> **ramoj02 said:**
> Just type <sudo apt-get install aircrack-ng>
then... <sudo apt-get install macchanger> (this is optional)

Exactly, the other packages needed in the tutorial are installed automatically...

---

