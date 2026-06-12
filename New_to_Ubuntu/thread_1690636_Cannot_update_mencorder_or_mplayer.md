---
title: "Cannot update mencorder or mplayer"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by Paperloader on 2011-02-18
In the Update Manager it shows there are updates for mencorder and mplayer but when I try to update them I get a message that says Requires installation of untrusted packages
"The action would require the installation of packages from not authenticated sources."
How do I fix this so I can update these packages?

---

### Post by mikewhatever on 2011-02-18
Where are you installing those updates from?

---

### Post by Paperloader on 2011-02-18
The update manager.

---

### Post by mikewhatever on 2011-02-18
The update manager is just a GUI front end, but where do the packages come from? In case you don't know, post the output of 'sudo apt-get update' to show your sources.

---

### Post by Paperloader on 2011-02-18
How do I post the output?

---

### Post by mikewhatever on 2011-02-18
Copy/paste. Wrap the [noparse]```

```[/noparse] tags around it.

---

### Post by Paperloader on 2011-02-18
greg@greg-Compaq-PC:~$ sudo apt-get update
[sudo] password for greg: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [31.4kB]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [28.1kB]       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [11.3kB]   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [643B]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [93.6kB] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [49.2kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages             
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [1,659B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages   
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                     
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Get:12 [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg [197B]               
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US         
Get:13 [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release [6,857B]                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources/DiffIndex              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources/DiffIndex          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages/DiffIndex        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages/DiffIndex    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages              
Fetched 216kB in 12s (16.9kB/s)                                                
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
greg@greg-Compaq-PC:~$

---

### Post by mikewhatever on 2011-02-18
So, no authentication key for medibuntu. According to the medibuntu help page you need to allow unauthenticated content:
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)
```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
```

That should solve it.

---

### Post by Paperloader on 2011-02-18
I did that and I still cannot update. Here is what I did:
greg@greg-Compaq-PC:~$ sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
[sudo] password for greg: 
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
greg@greg-Compaq-PC:~$

---

### Post by Paperloader on 2011-02-18
OK, I figured it out and everything is fine now. Thank you for the help.

---

