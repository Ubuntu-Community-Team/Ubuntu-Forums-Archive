---
title: "update manager error message!!!!!!"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by fidelandche on 2009-09-11
Hi, I keep getting this error message from update manager.

Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

The update manager also reports that it could not update all the repositories and it was last updated 17 days ago!! even though it up dates nearly every day!!

The synaptic package manager will give me an error message when I have removed a package, but when it last appeared I forgot to copy the message, but it is a lot like the one from the update manager.

---

### Post by nhasian on 2009-09-11
instead of using update-manager, open up a terminal and type:

```
sudo apt-get update && sudo apt-get upgrade
```

please give us the output here.

---

### Post by fidelandche on 2009-09-12
Here is the output to that command,

Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports Release.gpg                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/deb-src Translation-en_GB                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/http://ppa.launchpad.net/bisigi/ppa/ubuntu Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/jaunty Translation-en_GB                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/main Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/restricted Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_GB 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/universe Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed Release.gpg        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed/multiverse Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed/universe Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports Release                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-proposed/universe Packages
W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
andy@andy-laptop:~$

---

### Post by nhasian on 2009-09-13
looks like the only source that is giving you trouble is [http://ppa.launchpad.net/bisigi/ppa/...jaunty/Release](http://ppa.launchpad.net/bisigi/ppa/...jaunty/Release)
what package do you need from that ppa?  you can disable it by going to System->Softwre Sources, then select the Other Software tab, and untick the box next to [http://ppa.launchpad.net/bisigi/ppa/](http://ppa.launchpad.net/bisigi/ppa/)

---

### Post by fidelandche on 2009-09-13
Thanks for that, all sorted.

---

