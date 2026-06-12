---
title: "Repo error"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by icyest on 2009-02-16
Yeah, I got an error when updating my repositories:
```
t@t:~$ gksudo apt-get update
Hit http://download.virtualbox.org intrepid Release.gpg
Ign http://download.virtualbox.org intrepid/non-free Translation-en_US         
Hit http://download.virtualbox.org intrepid Release                            
Hit http://download.virtualbox.org intrepid/non-free Packages                  
Ign http://javadesktop.org stable Release.gpg                                  
Ign http://javadesktop.org stable/contrib Translation-en_US                    
Ign http://javadesktop.org stable Release                                      
Ign http://javadesktop.org stable/contrib Packages                             
Hit http://javadesktop.org stable/contrib Packages                             
Hit http://archive.canonical.com intrepid Release.gpg                          
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Get:1 http://ppa.launchpad.net intrepid Release.gpg [307B]                     
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://archive.ubuntu.com intrepid Release.gpg                             
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US            
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Ign http://packages.medibuntu.org intrepid/free Translation-en_US              
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US          
Hit http://repository.akirad.net akirad-intrepid Release.gpg                   
Ign http://repository.akirad.net akirad-intrepid/main Translation-en_US        
Hit http://archive.canonical.com intrepid Release                              
Get:2 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Ign http://ppa.launchpad.net intrepid Release                                  
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US            
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US              
Ign http://archive.ubuntu.com intrepid/main Translation-en_US                  
Hit http://archive.ubuntu.com intrepid-updates Release.gpg                     
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US    
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US    
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US      
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US          
Hit http://archive.ubuntu.com intrepid Release                                 
Hit http://packages.medibuntu.org intrepid Release                             
Hit http://repository.akirad.net akirad-intrepid Release                       
Hit http://archive.canonical.com intrepid/partner Packages                     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.ubuntu.com intrepid-updates Release                         
Hit http://packages.medibuntu.org intrepid/free Packages                       
Hit http://archive.canonical.com intrepid/partner Sources                      
Ign http://ppa.launchpad.net intrepid/main Sources                             
Hit http://archive.ubuntu.com intrepid/restricted Packages                     
Hit http://archive.ubuntu.com intrepid/multiverse Packages                     
Hit http://archive.ubuntu.com intrepid/universe Packages                       
Hit http://archive.ubuntu.com intrepid/main Packages                           
Hit http://repository.akirad.net akirad-intrepid/main Packages                 
Hit http://packages.medibuntu.org intrepid/non-free Packages                   
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages             
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://archive.ubuntu.com intrepid-updates/universe Packages            
Hit http://archive.ubuntu.com intrepid-updates/main Packages                
Hit http://ppa.launchpad.net intrepid/main Sources                          
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/main Packages
Fetched 308B in 21s (14B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: You may want to run apt-get update to correct these problems
t@t:~$ 

```

See that thing at the bottom?
The same error message pops up when I use synaptic's reload function.
Help?

---

### Post by RomeReactor on 2009-02-16
Hi. Try either one of the solutions posted [here]("http://ubuntuforums.org/showpost.php?p=6650442&postcount=11") or [here]("http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu").

---

### Post by forger on 2009-02-16
Here's a script that fixes ppa links and gets ppa keys:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

