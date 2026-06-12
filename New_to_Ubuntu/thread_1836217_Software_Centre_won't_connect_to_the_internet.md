---
title: "Software Centre won't connect to the internet"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by eversilentone on 2011-08-30
Browsing is fine, albeit a slow 2mb, but still more than enough to download Skype.  Is there any way I can check the connection with the Software Centre?  I should add that I can't download *anything*, not just Skype.

---

### Post by ubudog on 2011-08-30
Strange... you can browse the web fine?

I have a 5MB connection here, I used to have a 2MB connection, and it worked OK.  May I ask what ISP you use?

---

### Post by eversilentone on 2011-08-30
I'm with Virgin and live in Edinburgh.  I've just managed to download POL and Skype through Synaptic, which is working fine.  Very strange!  I'd like to try and get it sorted!

EDIT: scratch that: they're old versions and it won't update them :(
EDIT 2: In fact, it not only says there's no connection (when there is, hence why I can post this...) but it says that it failed because it would have to install from an untrusted source?  Very confused and kinda frustrated :(

---

### Post by ubudog on 2011-08-30
Ah, open your Software Sources (by going into Software Center, then clicking on the Edit tab, then Software Sources).  Can you please post a screenshot of the "Other Software" tab?  

Also, does it give you an option to allow the untrusted source?  And, did you add a software source lately?

---

### Post by eversilentone on 2011-08-31
Here's the screenie:
[ATTACH]201151[/ATTACH]

It doesn't give me the option to accept the untrusted source :(  And I did add the PPA for WINE but have since deleted it (having read that that might be the problem) but still no change in the SC.

---

### Post by saltmarshlamb on 2011-08-31
Can you open a terminal, run this and post the output please

```
sudo apt-get update 
```

---

### Post by eriktheblu on 2011-08-31
The 3rd check box down (labeled Independent) I think should do the trick.

---

### Post by eversilentone on 2011-08-31
Ok so I'm a very impatient person... I reinstalled Ubuntu and the SC works.  Except now the update part doesn't?  It again says I'm not connected yet I clearly am - very confused!  Right now I can't play mp3s without the right downloads (which seems strange as I thought Banshee could do that without further downloads?).

I typed in the code in the terminal and here's what I got:


> Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB [74.5 kB]      
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB [73.4 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_GB               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB [2,259 B]
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB [4,982 B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:5 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:6 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:7 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,215 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 158 kB in 42s (3,719 B/s)
Reading package lists... Done

I hope that makes sense to someone?!

EDIT: here are screenshots for what I'm trying to install/update, the permission request (which I complete) and the error message I get:
[ATTACH]201164[/ATTACH]
[ATTACH]201165[/ATTACH]
[ATTACH]201166[/ATTACH]

EDIT 2: Ok, so I'm sorry if I'm wasting time here, clearly an eejit!  Although the update centre thing wouldn't connect I was able to manually find most of the files requested in Synaptic Manager, so at least I can play music right now, although some of the files still wouldn't download (I guess the host was busy?).

---

