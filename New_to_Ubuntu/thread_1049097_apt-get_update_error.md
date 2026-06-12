---
title: "apt-get update error??"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by ReWS on 2009-01-24
Hi anyone. 
I had installed ubuntu on my old laptop Thinkpad T41 for about 6 month ago, and ill get tired of my CPU use age was over 70% all of the time. then i found out that is was X.org that causes these problems and ill goggled my problem to find a solution. but in this solution they said that I should add these two lines to my source list in /etc/apt/sources.list.

the lines i added was:
deb [http://debian.uni-c.dk/debian/](http://debian.uni-c.dk/debian/) etch main contrib non-free
deb-src [http://debian.uni-c.dk/debian/](http://debian.uni-c.dk/debian/) etch main contrib non-free

and now when i run my apt-get update my log looks like this


mainframe@mainframe-laptop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_DK            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_DK        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_DK  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_DK  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_DK    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_DK                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_DK            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_DK             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                      
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14,2kB]          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                  
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages [14,8kB]       
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources [37B]              
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid Release.gpg                
Get:5 [http://debian.uni-c.dk](http://debian.uni-c.dk) etch Release.gpg [386B]
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/main Translation-en_DK
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/restricted Translation-en_DK
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/multiverse Translation-en_DK
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/universe Translation-en_DK
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/main Translation-en_DK
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/restricted Translation-en_DK
Ign [http://debian.uni-c.dk](http://debian.uni-c.dk) etch/main Translation-en_DK
Ign [http://debian.uni-c.dk](http://debian.uni-c.dk) etch/contrib Translation-en_DK
Ign [http://debian.uni-c.dk](http://debian.uni-c.dk) etch/non-free Translation-en_DK
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_DK
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/universe Translation-en_DK
Get:6 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid Release [65,9kB]
Get:7 [http://debian.uni-c.dk](http://debian.uni-c.dk) etch Release [58,2kB]
Get:8 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates Release [51,2kB]
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/main Packages 
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/restricted Packages
Ign [http://debian.uni-c.dk](http://debian.uni-c.dk) etch Release                                        
Hit [http://debian.uni-c.dk](http://debian.uni-c.dk) etch/main Packages                                  
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/main Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/universe Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/universe Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://debian.uni-c.dk](http://debian.uni-c.dk) etch/contrib Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://debian.uni-c.dk](http://debian.uni-c.dk) etch/non-free Packages
Hit [http://debian.uni-c.dk](http://debian.uni-c.dk) etch/main Sources
Hit [http://debian.uni-c.dk](http://debian.uni-c.dk) etch/contrib Sources
Hit [http://debian.uni-c.dk](http://debian.uni-c.dk) etch/non-free Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/universe Packages
Fetched 205kB in 2s (73,6kB/s)
Reading package lists... Done
W: GPG error: [http://debian.uni-c.dk](http://debian.uni-c.dk) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems


Ill tried anything and i tried google it for 2 days now and no solution, so please help me.

Henrik Petersen
Denmark

---

### Post by SunnyRabbiera on 2009-01-24
etch is different, so no wonder if you are having issues.
etch is debian, not ubuntu and even though they are similar the two dont exactly share the same libraries.

---

### Post by billgoldberg on 2009-01-24
Just remove those from the sources.list

and run apt-get update

---

### Post by SOULRiDER on 2009-01-24
Its a PGP error.
[http://osterman.com/wordpress/2007/09/08/debian-apt-get-update-fails-with-no_pubkey-a70daf536070d3a1](http://osterman.com/wordpress/2007/09/08/debian-apt-get-update-fails-with-no_pubkey-a70daf536070d3a1)

I dont think you want that repo in there though.

---

