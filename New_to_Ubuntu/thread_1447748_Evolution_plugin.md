---
title: "Evolution plugin"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by motorhead_1 on 2010-04-05
I'd like to install the following plugin [http://gnome.eu.org/evo/index.php/Evolution_Tray](http://gnome.eu.org/evo/index.php/Evolution_Tray) 
I've downloaded and extracted the tar.gz file what should I do know? the README file appears to be empty... thanks

---

### Post by motorhead_1 on 2010-04-05
..,

---

### Post by shrimpy89 on 2010-04-06
1. Extract the files to your desktop

2. In the terminal:

```
cd ./Desktop/evolution-tray-0.0.3
```

```
./configure
```

Read the output of the text that follows.  If it says something is missing, use "sudo apt-get install" followed by the package name.  Then run ./configure again until it runs all the way through without asking for anything.  Then:

```
make
```

```
make install
```

And that should do it.  If someone has an easier way (say, finding a .deb or something), by all means reply, since ./configure isn't all that user-friendly at times.

---

### Post by henkeC on 2010-04-06
Or add: **ppa:ripps818/ppa** to your third party repos

```
sudo apt-get update
sudo apt-get install evolution-tray
```

---

### Post by motorhead_1 on 2010-04-06
> **henkeC said:**
> Or add: **ppa:ripps818/ppa** to your third party repos

```
sudo apt-get update
sudo apt-get install evolution-tray
```
excuse my ignorance but how do I do it? in Jaunty I used  
sudo nano /etc/apt/sources.list

and edit the source.list file, doing this in Karmic the source file appears in the terminal and I can't edit it...

---

### Post by philinux on 2010-04-06
Just use this.

```
sudo add-apt-repository ppa:ripps818/ppa
```

[https://launchpad.net/~ripps818/+archive/ppa](https://launchpad.net/~ripps818/+archive/ppa)

---

### Post by motorhead_1 on 2010-04-06
```
daitarn@daitarn-laptop:~$ sudo add-apt-repository ppa:ripps818/ppa
[sudo] password for daitarn: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv F8B95F9164704B0DC676DAF47778990EEEB23232
gpg: requesting key EEB23232 from hkp server keyserver.ubuntu.com
gpg: key EEB23232: "Launchpad PPA for Taylor "Ripps" L-Wren" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
daitarn@daitarn-laptop:~$ sudo apt-get update
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Get:1 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://archive.canonical.com karmic Release                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:2 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://www.mendeley.com  Release.gpg                                       
Get:3 http://dl.google.com stable Release.gpg [189B]                           
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://www.mendeley.com  Translation-en_US                                 
Get:4 http://ppa.launchpad.net karmic Release [66.0kB]                         
Hit http://archive.canonical.com karmic/partner Packages                       
99% [Release gpgv 44056] [Waiting for headers] [Waiting for headers] [Waiting f
Hit http://archive.canonical.com karmic/partner Sources                        
Ign http://www.mendeley.com  Release                                           
Get:5 http://ppa.launchpad.net karmic Release [66.0kB]                         
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://ppa.launchpad.net karmic Release                                    
Ign http://ppa.launchpad.net karmic Release                                    
Hit http://security.ubuntu.com karmic-security/main Packages                   
Ign http://www.mendeley.com  Packages                                          
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://www.mendeley.com  Packages                                          
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://www.mendeley.com  Packages                                          
Hit http://it.archive.ubuntu.com karmic Release.gpg                            
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://download.virtualbox.org karmic Release.gpg                          
Ign http://download.virtualbox.org karmic/non-free Translation-en_US           
Hit http://download.virtualbox.org karmic Release                              
Hit http://download.virtualbox.org karmic/non-free Packages                    
Ign http://it.archive.ubuntu.com karmic/main Translation-en_US       
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Hit http://packages.medibuntu.org karmic Release                     
Ign http://it.archive.ubuntu.com karmic/restricted Translation-en_US 
Hit http://packages.medibuntu.org jaunty Release                               
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://packages.medibuntu.org karmic/free Sources                
Hit http://packages.medibuntu.org karmic/non-free Sources            
Hit http://packages.medibuntu.org jaunty/free Packages               
Hit http://packages.medibuntu.org jaunty/non-free Packages           
Ign http://it.archive.ubuntu.com karmic/universe Translation-en_US   
Ign http://it.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://it.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://it.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://it.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://it.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://it.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Hit http://it.archive.ubuntu.com karmic Release                                
Hit http://it.archive.ubuntu.com karmic-updates Release                        
Hit http://it.archive.ubuntu.com karmic/main Packages                          
Hit http://it.archive.ubuntu.com karmic/restricted Packages                    
Hit http://it.archive.ubuntu.com karmic/universe Packages                      
Hit http://it.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://it.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://it.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://it.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://it.archive.ubuntu.com karmic-updates/multiverse Packages            
Ign http://dl.google.com stable/main Translation-en_US                         
Get:6 http://dl.google.com stable Release [2,540B]
Get:7 http://dl.google.com stable/main Packages [917B]
Fetched 4,262B in 2min 0s (35B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C28F899060FD0E97
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 015A66E603E02400
daitarn@daitarn-laptop:~$ 
daitarn@daitarn-laptop:~$ sudo apt-get install evolution-tray
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package evolution-tray**
daitarn@daitarn-laptop:~$ 

```

---

### Post by philinux on 2010-04-06
Looks like the ppa failed to be added.

Are you using Jaunty or Karmic?

---

### Post by motorhead_1 on 2010-04-06
Karmic

---

### Post by philinux on 2010-04-06
When a ppa adds correctly it gives the terminal output as shown in this screen shot. Maybe that ppa is having a bad day.

---

### Post by motorhead_1 on 2010-04-06
yea seems it failed to add it...

gpg: requesting key EEB23232 from hkp server keyserver.ubuntu.com
gpg: key EEB23232: "Launchpad PPA for Taylor "Ripps" L-Wren" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

---

