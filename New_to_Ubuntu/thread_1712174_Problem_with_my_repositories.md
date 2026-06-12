---
title: "Problem with my repositories"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by darknuts on 2011-03-22
Hey everyone! I have a small problem with my repositories. When I run 'sudo apt-get update', I get the following:

```

bearcat@bearcat8f:~$ sudo apt-get update
Ign http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ilap/lwp/ubuntu/ lucid/main Translation-en_US     
Hit http://archive.ubuntu.com lucid Release.gpg                     
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US             
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US       
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Ign http://ppa.launchpad.net lucid Release                                     
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid-updates Release.gpg              
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid-security Release.gpg                       
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ lucid/partner Translation-en_US    
Hit http://archive.canonical.com lucid Release                                 
Ign http://ppa.launchpad.net lucid/main Packages                               
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Ign http://ppa.launchpad.net lucid/main Packages                               
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid Release                                    
Hit http://archive.ubuntu.com lucid-updates Release                            
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://archive.canonical.com lucid/partner Sources                         
[COLOR=Red]Err http://ppa.launchpad.net lucid/main Packages                               
  404  Not Found[/COLOR]
Hit http://archive.ubuntu.com lucid-security Release                 
Hit http://archive.canonical.com lucid/partner Packages              
[COLOR=Green]Get:1 http://dl.google.com stable Release.gpg [197B] [/COLOR]                
Hit http://archive.ubuntu.com lucid/main Packages   
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/main Sources    
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Ign http://dl.google.com/linux/earth/deb/ stable/main Translation-en_US
[COLOR=Green]Get:2 http://dl.google.com stable Release [1,338B]
Get:3 http://dl.google.com stable/main Packages [474B][/COLOR]                         
Fetched 2,009B in 31s (63B/s)                                                  
[COLOR=Red]W: Failed to fetch http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found[/COLOR]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Apparently, some of my sources are no longer good and its giving me constant error messages when I update and when I try to install some programs. Should I just delete these sources? Is there anything to replace them with? Also, the lines highlighted green caught my eye. What do these 'get' lines mean?

---

### Post by wojox on 2011-03-22
The green is for your chrome browser updates. You can uncheck the ppa for the red one and it should work okay.

---

### Post by QLee on 2011-03-22
[QUOTE=wojox]...You can uncheck the ppa for the red one and it should work okay.[/QUOTE]

And that, darknuts, is because the URL:[http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/) does not contain a folder for lucid, only one for maverick, your system is telling you the truth. Perhaps there was one there in the past, you might try asking the person responsible for the ppa.

---

### Post by darknuts on 2011-03-22
Thanks guys! Great advice as usual.

---

