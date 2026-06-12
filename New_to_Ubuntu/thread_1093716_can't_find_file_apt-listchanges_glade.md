---
title: "can't find file apt-list/changes glade"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by cousinlucky on 2009-03-11
I just installed Ubuntu 8.04 a few weeks ago. I keep getting a warning message at the beginning of updates that the update software can not find the file apt-list/changes glade. Does anyone know how to fix this problem, please?

---

### Post by oldos2er on 2009-03-11
Can you enter
```
sudo apt-get update && sudo apt-get safe-upgrade
```
into a terminal, and post the output here?

---

### Post by cousinlucky on 2009-03-12
cousinlucky@cousinlucky-desktop:~$ sudo apt-get update && sudo apt-get safe-upgrade
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources
Reading package lists... Done
E: Invalid operation safe-upgrade
cousinlucky@cousinlucky-desktop:~$

---

### Post by oldos2er on 2009-03-15
Oops, probably should've been "sudo apt-get upgrade". Are you still getting the warning?

---

### Post by cousinlucky on 2009-03-15
I'll try the upgrade code because I am still getting the warning every day.

here is what I got:

Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

