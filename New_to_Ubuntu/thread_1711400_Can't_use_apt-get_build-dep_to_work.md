---
title: "Can't use apt-get build-dep to work"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by dougao06 on 2011-03-21
Hello,

sorry for bothering, I'm new to ubuntu, and I wanted to try the open-source math softwares available, to see if it is worth it to change from mathlab. But I can't seem to be able to compile the files (I know I can take them from software center, but they seem to be older versions, and I figured I would have to learn how to do this sooner or later).

The readme and guide files recommend using sudo apt-get build-dep scilab (for example), but when I try it, it shows:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/ppa.launchpad.net_falk-t-j_games_ubuntu_dists_maverick_main_source_Sources - open (2: No such file or directory)

```While searching on the forum, I stumbled upon a recommendation to run apt-get update, but that fails also:

```
Hit http://br.archive.ubuntu.com maverick Release.gpg
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://br.archive.ubuntu.com/ubuntu/ maverick/main Translation-pt          
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Hit http://br.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-pt    
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Hit http://br.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-pt    
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://br.archive.ubuntu.com/ubuntu/ maverick/universe Translation-pt      
Hit http://br.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-pt  
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-pt
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-pt
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-pt
Hit http://br.archive.ubuntu.com maverick Release                              
Hit http://br.archive.ubuntu.com maverick-updates Release                      
Hit http://br.archive.ubuntu.com maverick/main Sources                         
Hit http://br.archive.ubuntu.com maverick/restricted Sources                   
Hit http://br.archive.ubuntu.com maverick/universe Sources                     
Hit http://br.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://br.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://br.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://br.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://br.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://br.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://br.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://br.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://br.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://br.archive.ubuntu.com maverick-updates/main i386 Packages           
Hit http://br.archive.ubuntu.com maverick-updates/restricted i386 Packages     
Hit http://br.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://br.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://linux.dropbox.com maverick Release.gpg                              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/falk-t-j/games/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/falk-t-j/games/ubuntu/ maverick/main Translation-en_US
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-pt       
Hit http://archive.canonical.com maverick Release                              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-pt              
Hit http://linux.dropbox.com maverick Release                                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-pt              
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-pt   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-pt
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-pt
Ign http://ppa.launchpad.net/falk-t-j/games/ubuntu/ maverick/main Translation-pt
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://extras.ubuntu.com maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-pt
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://archive.getdeb.net maverick-getdeb Release.gpg            
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en_US
Hit http://security.ubuntu.com maverick-security/main Sources        
Ign http://ppa.launchpad.net maverick/main Sources                   
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources    
Hit http://security.ubuntu.com maverick-security/multiverse Sources  
Hit http://security.ubuntu.com maverick-security/main i386 Packages  
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-pt
Hit http://archive.getdeb.net lucid-getdeb Release.gpg               
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/games Translation-en
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/games Translation-en_US
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/games Translation-pt
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages                     
  404  Not Found
Hit http://archive.getdeb.net maverick-getdeb Release  
Hit http://archive.getdeb.net lucid-getdeb Release
Hit http://archive.getdeb.net maverick-getdeb/apps Sources  
Hit http://archive.getdeb.net maverick-getdeb/apps i386 Packages
Hit http://archive.getdeb.net lucid-getdeb/games Sources
Hit http://archive.getdeb.net lucid-getdeb/games i386 Packages
W: Failed to fetch http://ppa.launchpad.net/falk-t-j/games/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/falk-t-j/games/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Anyone knows where the problem is?

Thank you beforehand,
Pedro.

---

### Post by SeijiSensei on 2011-03-21
It's pretty clearly the PPA ppa.launchpad.net/falk-t-j.  It's unreachable.  Delete it from /etc/apt/sources.list, run 'sudo apt-get update', and try again.

---

### Post by dougao06 on 2011-03-21
Ah, I didn't know that other sources could interfere like that. Anyway, that worked, thank you. :D

---

