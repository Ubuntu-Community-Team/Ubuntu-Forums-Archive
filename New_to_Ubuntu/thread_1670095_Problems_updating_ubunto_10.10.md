---
title: "Problems updating ubunto 10.10"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by richardford1976 on 2011-01-18
Hey all, 


Completely new to Linux but from what i can see its all very promising, I love a new challenge but i have hit my first problem. I want to install all the critical updates but i am getting a message that states "requires installation of untrusted packages" I googled the problem and it seems to be a problem with a "key" being assigned. I run the command "sudo apt-get update" and i needed to check the list for missing keys, However i cant see any in my list below? yet still it wont update. Any Ideas? Please bear with me because i am very new to this,However i am technical, I just havent used Linux before. 


```
richard@richard-P5KC:~$ 
richard@richard-P5KC:~$ sudo apt-get update
[sudo] password for richard: 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                                                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release.gpg                                                                                                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                                                                        
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB                                                                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                                                                           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                                                                           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB                                                                                                               
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB                                                                                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                                                       
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en                                                                                                               
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_GB                                                                                                            
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                                                                                             
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB                                                                                          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                                                                                             
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB                                                                                                                
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                                                                                                     
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB                                                                                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release.gpg                                                                                                                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                                                                                            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB                                                                                                         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                                                                                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB                                                                                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB                                                                                     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                                                                                           
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB                                                                                                              
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en                                                                                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                                                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                                                                                                                      
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB                                                                                                        
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en                                                                                     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB                                                                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en                                                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                                                                                                               
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB                                                                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release.gpg                                                                                                         
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                                                                                         
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_GB                                                                
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en                                                             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_GB                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources                                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages                                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en                                       
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_GB                                    
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en                                         
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_GB                                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release.gpg                                                              
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en                                              
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_GB                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages                                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en                                        
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_GB           
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en              
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_GB           
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en                
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release                                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release                                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release                                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release                                                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main Sources                                                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted Sources                                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe Sources                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse Sources                                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main amd64 Packages                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted amd64 Packages                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe amd64 Packages                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse amd64 Packages                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main Sources                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted Sources                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse Sources                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main amd64 Packages                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted amd64 Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe amd64 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main amd64 Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted amd64 Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe amd64 Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/multiverse amd64 Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/restricted amd64 Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/main amd64 Packages                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/multiverse amd64 Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/universe amd64 Packages                        
Get:1 [http://downloadue.info](http://downloadue.info) maverick Release.gpg                                                 
Ign [http://downloadue.info/repo/](http://downloadue.info/repo/) maverick/all Translation-en                
Ign [http://downloadue.info/repo/](http://downloadue.info/repo/) maverick/all Translation-en_GB             
Ign [http://downloadue.info](http://downloadue.info) maverick Release           
Ign [http://downloadue.info](http://downloadue.info) maverick/all amd64 Packages/DiffIndex
Ign [http://downloadue.info](http://downloadue.info) maverick/all amd64 Packages
Ign [http://downloadue.info](http://downloadue.info) maverick/all amd64 Packages
Hit [http://downloadue.info](http://downloadue.info) maverick/all amd64 Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release.gpg
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/games Translation-en
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/games Translation-en_GB
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/games amd64 Packages
Reading package lists... Done
richard@richard-P5KC:~$
```

---

### Post by cariboo on 2011-01-18
Which repositories are you getting the key errors for?

---

### Post by richardford1976 on 2011-01-19
HI There, 
 
Ive taken a look in system.......Update Manager and i cant see what repositories i am updating. Can you advise where i can find this infomation. cheers.

---

### Post by richardford1976 on 2011-01-19
Anyone, would really appreciate some assistance. Thanks in advance.

---

### Post by richardford1976 on 2011-01-19
Anyone, would really appreciate some assistance. Thanks in advance.

---

### Post by richardford1976 on 2011-01-19
Can anyone help please? Thanks in advance.

---

### Post by richardford1976 on 2011-01-20
Hey all, 

I didnt realise i had doubleposted so many times, Guess i will just have to try and figure this out myself. cheers.

---

### Post by plucky on 2011-01-20
What does ```
sudo apt-get upgrade
``` show you?

---

### Post by richardford1976 on 2011-01-21
Hi There, 

I run the command "sudo apt-get update" it downloaded a ton of updates in the terminal window, It asked to reboot and now doesnt seem to want to come back upto the desktop.

---

### Post by nm_geo on 2011-01-21
Richard,
 
A question when you update are you expecting something to open and install on your computer?  You might need to read up on updating and upgrading.
 
Check out this link
 
[https://help.ubuntu.com/8.04/serverguide/C/apt-get.html](https://help.ubuntu.com/8.04/serverguide/C/apt-get.html)

---

### Post by richardford1976 on 2011-01-22
Welll cant really comment, Im a complete noob when it comes to Linux but willing to learn, I have only ever used windows and dos based pc's(long time ago) Everything in this OS is being learnt from scratch. It looks very good and im enjoying the use of the command line as i feel this will give you a better understandingof the OS (if i knew what the commands did lol) Thanks for the link tho nm_geo, i certanly need to do some reading up on this OS. But i still have a installation that wont boot to the desktop since i updated. any suggestions? i may try a reinstall.

---

