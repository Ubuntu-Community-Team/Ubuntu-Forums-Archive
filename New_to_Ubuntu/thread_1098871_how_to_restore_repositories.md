---
title: "how to restore repositories?"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by geltonas on 2009-03-17
Hi, 
I've got "problem" I can't update my source.list file properly, probably I made some changes in that file, how to restore back this file?

this is what I get when I try tu run command update:
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg [189B]        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [51.2kB]           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release [51.2kB]          
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_GB       
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Fetched 51.6kB in 1s (34.5kB/s)
Reading package lists... Done
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by taurus on 2009-03-17
Go into System -> Administration -> Software Sources and switch to another server.

---

