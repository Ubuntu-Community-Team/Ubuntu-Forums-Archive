---
title: "Error installing Miro 4 in Ubuntu 11.04"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by mtotowajirani on 2011-06-08
I installed Miro 4 using this code:

sudo add-apt-repository ppa:cf/miro-releases
sudo apt-get update
sudo apt-get install miro

After the installation, I tried the sudo apt-get update and it brings a 404 error for some reason:

> 
admin@mothership:~$ sudo apt-get update
[sudo] password for admin: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
W: Failed to fetch [http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
admin@mothership:~$ 

Can anyone help me remove this?

---

### Post by mike555 on 2011-06-08
It probably just means that the server is too busy or offline for repairs ........ try later ..

 but if it persists you can uncheck that one in Software Sources ....

---

### Post by mtotowajirani on 2011-06-09
This helps. I unchecked it from software sources.

Thanks.

---

