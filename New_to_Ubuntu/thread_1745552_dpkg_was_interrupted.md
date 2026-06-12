---
title: "dpkg was interrupted"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by razedafear on 2011-05-01
Hi 

I was upgrading my Ubuntu 10.10 to 11 through update manager.I was done with the downloading part of it and it was to a point where it was installing changes and thats when i lost power backup. Now when i open the synaptic manager it gives the following error 

[I]" E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."[/I]


i typed the above command " *sudo dpkg configure -a*" in terminal and here is the result

"[I]dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !"[/I]

I also tried these commands 

sudo apt-get update
followed by
sudo apt-get upgrade

heres what i got as output

[I][COLOR="Red"][COLOR="DarkRed"]ubuntu@ubuntu:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en   
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main Translation-en      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main Translation-en             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/universe Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/restricted Translation-en       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe Translation-en         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main Translation-en     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/universe Translation-en 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,064B]
Fetched 2,608B in 10s (248B/s)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
ubuntu@ubuntu:~$ sudo apt-get upgrade 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/COLOR][/COLOR][/I]

[B]What should i do about it now. 
Does tis mean all my downloading data is gone and i have to redownload it or i juts need to fix it somehow . [/B]

Please help :confused:

---

### Post by ~Plue on 2011-05-01
> **razedafear said:**
> 
[I]" E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."[/I]

i typed the above command " *sudo dpkg configure -a*" in terminal and here is the result

you missed the hyphens in --configure..

---

