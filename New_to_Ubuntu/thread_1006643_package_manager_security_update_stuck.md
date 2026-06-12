---
title: "package manager security update stuck"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by AmberG on 2008-12-09
Today I was informed that a whole bundle of updates were waiting for installation.

Everything seemed to go well (downloaded and installed) with the exception of one package:

compiz-plugins-fusion-main

It is labelled as an important security update but it will not install.  It appears to download but then nothing happens. It remains stuck in the update manager window.

I haven't a clue what this is for or its importance.

I keep getting reminders that it is available to install.

memories of Microsoft patches come flooding back :(

---

### Post by lykwydchykyn on 2008-12-09
Can you type these commands into a command line and post the output?
```

sudo aptitude update
sudo aptitude upgrade

```

that will make it easier to see what's going on.

---

### Post by Tatty on 2008-12-09
can you post the output of:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by AmberG on 2008-12-09
```
~$ sudo aptitude update
[sudo] password for local: 
Writing extended state information... Done
Ign http://ppa.launchpad.net intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid/main Translation-en_GB                    
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Hit http://archive.canonical.com intrepid Release.gpg                           
Ign http://archive.canonical.com intrepid/partner Translation-en_GB             
Hit http://archive.canonical.com intrepid Release                               
Hit http://gb.archive.ubuntu.com intrepid Release.gpg                           
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB                
Ign http://ppa.launchpad.net intrepid/main Packages                             
Hit http://security.ubuntu.com intrepid-security Release.gpg                    
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB         
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg                   
Hit http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB        
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com intrepid-backports Release.gpg                 
Hit http://ppa.launchpad.net intrepid/main Packages                             
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB     
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB   
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB   
Hit http://security.ubuntu.com intrepid-security Release                        
Hit http://archive.ubuntu.com intrepid Release.gpg                              
Ign http://gb.archive.ubuntu.com intrepid-backports/main Translation-en_GB      
Ign http://gb.archive.ubuntu.com intrepid-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-backports/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-backports/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-proposed Release.gpg                  
Hit http://gb.archive.ubuntu.com intrepid-proposed/universe Translation-en_GB   
Hit http://gb.archive.ubuntu.com intrepid-proposed/main Translation-en_GB       
Hit http://gb.archive.ubuntu.com intrepid-proposed/multiverse Translation-en_GB 
Hit http://gb.archive.ubuntu.com intrepid-proposed/restricted Translation-en_GB 
Hit http://archive.ubuntu.com intrepid Release                                  
Hit http://archive.canonical.com intrepid/partner Packages                      
Hit http://gb.archive.ubuntu.com intrepid Release                               
Hit http://gb.archive.ubuntu.com intrepid-updates Release           
Hit http://security.ubuntu.com intrepid-security/main Packages      
Hit http://gb.archive.ubuntu.com intrepid-backports Release         
Hit http://archive.canonical.com intrepid/partner Sources                       
Hit http://security.ubuntu.com intrepid-security/universe Packages              
Hit http://security.ubuntu.com intrepid-security/restricted Packages            
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-proposed Release           
Hit http://archive.ubuntu.com intrepid/main Sources                             
Hit http://security.ubuntu.com intrepid-security/main Sources                   
Hit http://security.ubuntu.com intrepid-security/universe Sources    
Hit http://security.ubuntu.com intrepid-security/restricted Sources  
Hit http://security.ubuntu.com intrepid-security/multiverse Sources  
Hit http://gb.archive.ubuntu.com intrepid/main Packages              
Hit http://gb.archive.ubuntu.com intrepid/universe Packages
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid/main Sources
Hit http://gb.archive.ubuntu.com intrepid/universe Sources
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources
Hit http://archive.ubuntu.com intrepid/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid-backports/main Packages
Hit http://gb.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-proposed/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-proposed/main Packages
Hit http://gb.archive.ubuntu.com intrepid-proposed/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-proposed/restricted Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done             

```

and

```

:~$ sudo aptitude upgrade
[sudo] password for local: 
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages will be REMOVED:
  bsh{u} bsh-gcj{u} libxalan2-java{u} libxalan2-java-gcj{u} 
The following packages will be upgraded:
  compiz-fusion-plugins-main 
1 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 1269kB of archives. After unpacking 17.5MB will be freed.
Do you want to continue? [Y/n/?]

```

Given the warning do I continue ?

---

### Post by Tatty on 2008-12-09
Yes continue with that.  Its just a textual version of the update-manager.  If it works then it will update your machine, if not then it should hopefully say why.

---

### Post by AmberG on 2008-12-09
That seems to have worked - the update flag has gone away.

Noo idea what it was for or if it was worth the hassle.

Anyway, many thanks for the help fixing it.

---

