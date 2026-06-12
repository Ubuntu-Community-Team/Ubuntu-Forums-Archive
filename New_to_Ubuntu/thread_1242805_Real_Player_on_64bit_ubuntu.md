---
title: "Real Player on 64bit ubuntu"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2009-08-17
Hi, 
am having alot of trouble installing real player on this 64bit computer, I've tried both the . deb package and the .bin package...

While trying to install the .deb package using the command: 

sudo dpkg -i RealPlayer11GOLD.deb

I got this error message:

package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 RealPlayer11GOLD.deb


I also tried the .bin package, this seemed to work but when i try to open real player from the Applications - sound & video - Realplayer 11, I got this error message: Could not launch 'RealPlayer 11' Failed to execute child process "realplay" (No such file or directory).

Any help at all would be very welcome...

---

### Post by oldos2er on 2009-08-17
Realplayer 10 is in the Medibuntu repository; so if you have that enabled you can run ```
sudo apt-get update && sudo apt-get install realplayer
```

 If you don't have Medibuntu enabled, see [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by LowSky on 2009-08-17
here is the link to the 64 bit verison
[http://packages.medibuntu.org/pool/non-free/r/realplay/realplayer_11.0.0-0.2medibuntu2_amd64.deb](http://packages.medibuntu.org/pool/non-free/r/realplay/realplayer_11.0.0-0.2medibuntu2_amd64.deb)

enjoy

---

### Post by agkrish on 2010-01-08
I get the following message after running the command:

arun@arun-laptop:~$ sudo apt-get update && sudo apt-get install realplayer
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic Release.gpg
Ign [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/main Translation-en_US                 
Ign [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/main Translation-en_US         
Ign [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/restricted Translation-en_US   
Ign [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/universe Translation-en_US     
Ign [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US   
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic Release                                
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates Release                        
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/main Packages                          
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/main Sources                           
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/restricted Packages            
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/universe Sources               
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://kw.archive.ubuntu.com](http://kw.archive.ubuntu.com) karmic-updates/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [923B]                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg                          
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_US
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages
Fetched 3,652B in 2s (1,359B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate


what do i do ?

---

### Post by 3rdalbum on 2010-01-08
> **agkrish said:**
> 
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate


what do i do ?

Doesn't the w32codecs (or in your case, w64codecs) play all Real files? Including those old ones that RealPlayer doesn't play?

Assuming you have the Medibuntu repository activated, just install the "non-free-codecs" package (sudo apt-get install non-free-codecs) and you're done.

---

### Post by razif omar on 2010-01-14
Hello!
I`m using ubuntu 9.10

i`ve install real player from apt with this command
sudo apt-get install realplayer, 
also from sypnatic pakage manager.
But my realplayer still not working!
help me!

---

### Post by running_rabbit07 on 2010-01-14
> **3rdalbum said:**
> Doesn't the w32codecs (or in your case, w64codecs) play all Real files? Including those old ones that RealPlayer doesn't play?

Assuming you have the Medibuntu repository activated, just install the "non-free-codecs" package (sudo apt-get install non-free-codecs) and you're done.

When I came to Ubuntu, I brought over a gig of RealPlayer vids and all of them are easily opened with VLC and MoviePlayer after adding ubuntu-restricted-extras. I haven't been able to get realplayer working with Ubuntu, but I am guilty of not trying very hard.

---

