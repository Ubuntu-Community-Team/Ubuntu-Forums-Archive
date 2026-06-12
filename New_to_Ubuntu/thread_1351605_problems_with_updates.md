---
title: "problems with updates"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by herrnaphta on 2009-12-10
So I've got the little orange triangle telling me my update information is outdated.  I tried sudo apt-get update and I get ```
Ign http://www.statux.org jaunty Release.gpg
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://www.statux.org jaunty/main Translation-en_US                        
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Hit http://www.array.org jaunty Release.gpg                                    
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Ign http://www.statux.org jaunty Release                                       
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Ign http://repos.eeebuntu.org eb3 Release.gpg                                  
Hit http://security.ubuntu.com jaunty-security Release                         
Ign http://repos.eeebuntu.org eb3/main Translation-en_US                       
Ign http://repos.eeebuntu.org eb3/non-free Translation-en_US                   
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://packages.medibuntu.org jaunty Release                               
Ign http://www.statux.org jaunty/main Packages                                 
Hit http://us.archive.ubuntu.com jaunty Release                                
Ign http://www.array.org jaunty/main Translation-en_US                         
Ign http://repos.eeebuntu.org eb3/contrib Translation-en_US                    
Ign http://www.statux.org jaunty/main Packages                                 
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Get:1 http://repos.eeebuntu.org eb3 Release [1952B]                            
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://ppa.launchpad.net karmic/main Packages                              
Err http://www.statux.org jaunty/main Packages                                 
  404 Not Found
Hit http://packages.medibuntu.org jaunty/free Packages                         
Hit http://www.array.org jaunty Release                                        
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Ign http://repos.eeebuntu.org eb3/main Packages                                
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://us.archive.ubuntu.com jaunty/main Packages                          
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://us.archive.ubuntu.com jaunty/main Sources                           
Hit http://us.archive.ubuntu.com jaunty/restricted Sources           
Hit http://us.archive.ubuntu.com jaunty/universe Packages            
Hit http://us.archive.ubuntu.com jaunty/universe Sources             
Ign http://repos.eeebuntu.org eb3/non-free Packages                  
Ign http://repos.eeebuntu.org eb3/contrib Packages                   
Hit http://www.array.org jaunty/main Packages                        
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages          
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources            
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages                  
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages            
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources                   
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources             
Hit http://repos.eeebuntu.org eb3/main Packages                                
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages              
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources               
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages  
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources   
Hit http://repos.eeebuntu.org eb3/non-free Packages                  
Hit http://www.array.org jaunty/main Sources   
Hit http://repos.eeebuntu.org eb3/contrib Packages
Fetched 1B in 1s (1B/s)  
W: Failed to fetch http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Then I tried sudo apt-get update and i get 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  banshee
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```So clearly something is wrong with banshee.  When i try to update it via synaptic, I get a window that says "can't find repository indexes" and "Failed to fetch [http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages](http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

Any advice on how to get past this?

---

### Post by k3lt01 on 2009-12-10
Open a terminal and copy and paste this command into it
```
gksudo gedit /etc/apt/sources.list
```
type in your password when prompted hit enter and it will open Gedit for you with your sources.list file.

Now that your sources.list file is open comment out, by placing a # in front of the entries that correspond to the failed and ignored files in the list you have above. Now save your sources.list close the file and

```
 sudo apt-get update
```

then tell us how you go.

---

### Post by Buuntu on 2009-12-10
'sudo apt-get update' only refreshes what needs updated from the repositories.  To actually update your system you need to run update-manager or simply type in
```
sudo apt-get upgrade
```

---

### Post by azitizz on 2011-03-26
Im having a similar but slightly different problem, I have th red-triangle in th corner, and when I click on "Check" for updates, an error message appears and it says to check my internet connection. The details listed in the error message box are this:

```
W:GPG error: http://debian.tagancha.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5BC4CFB8EEF818CF, W:GPG error: http://debian.scribus.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5BC4CFB8EEF818CF, W:Failed to fetch http://debian.tagancha.org/debian/dists/lucid/non-free/source/Sources.gz  404  Not Found
, W:Failed to fetch http://debian.tagancha.org/debian/dists/lucid/non-free/binary-amd64/Packages.gz  404  Not Found
, W:Failed to fetch http://debian.scribus.net/debian/dists/lucid/non-free/source/Sources.gz  404  Not Found
, W:Failed to fetch http://debian.scribus.net/debian/dists/lucid/non-free/binary-amd64/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

What to do. I know my connection is good as I have been installing updates, however this triangle is often around now and the same error message appears when I try and check for the updates. 
Merci

---

