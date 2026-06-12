---
title: "Update manager error"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by Nigec on 2011-02-09
For well over a week the update manager has shown as a stop sign near the bin, try to run it and I get this error:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid-backports_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report
```I get the same error if I try the console, also the software center fails to start totally

---

### Post by adeee on 2011-02-09
try

sudo apt-get -f install

and
then 
sudo apt-get update

then install your software.s

---

### Post by Nigec on 2011-02-09
Thank :)
But it just kicks out the same error:
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid-backports_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

if I try using 
sudo apt-get update

it runs through the list:
```
nige@nige-laptop:~$ sudo apt-get update
Get:1 http://archive.canonical.com lucid Release.gpg [198B]
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en          
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release.gpg                          
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB       
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB       
Get:2 http://archive.canonical.com lucid Release [8,215B]                      
Get:3 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB   
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid-backports Release.gpg         
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_GB
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release                              
Hit http://gb.archive.ubuntu.com maverick-updates Release                      
Hit http://gb.archive.ubuntu.com lucid-backports Release                       
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Get:4 http://archive.canonical.com lucid/partner Sources [5,295B]              
Hit http://gb.archive.ubuntu.com maverick/main Sources                         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Get:5 http://archive.canonical.com lucid/partner i386 Packages [12.0kB]
Hit http://gb.archive.ubuntu.com maverick/restricted Sources                 
Hit http://gb.archive.ubuntu.com maverick/universe Sources                   
Hit http://gb.archive.ubuntu.com maverick/multiverse Sources
Hit http://gb.archive.ubuntu.com maverick/main i386 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security Release                      
Hit http://gb.archive.ubuntu.com maverick/universe i386 Packages              
Hit http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources                
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources          
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://gb.archive.ubuntu.com lucid-backports/main Sources
Hit http://gb.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://gb.archive.ubuntu.com lucid-backports/universe Sources
Hit http://gb.archive.ubuntu.com lucid-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com lucid-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com lucid-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com lucid-backports/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://gb.archive.ubuntu.com lucid-backports/multiverse i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Fetched 25.8kB in 0s (57.2kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid-backports_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

---

### Post by ikt on 2011-02-09
Try heading into  /var/lib/apt/lists/ and deleting gb.archive.ubuntu.com_ubuntu_dists_lucid-backports_main_binary-i386_Packages

then run through and apt-get update again.

---

### Post by Nigec on 2011-02-09
Thanks you ikt that did the trick... :D
We had problems with our modem last week and had to get a new one, for some reason that list file pointed to the broadband activation page, which basically you can't get past if the modem isn't activated 

Thanks again, all is well now ;)

---

