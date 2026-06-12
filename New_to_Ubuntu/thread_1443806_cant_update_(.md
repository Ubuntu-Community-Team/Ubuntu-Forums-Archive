---
title: "cant update :("
date: 2010-03-31
forum: New to Ubuntu
---

### Post by acemanollie on 2010-03-31
i cant update on 9.10. i do sudo apt-get update and get this 

zer0nice@zeronice-hacktheplanet:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
zer0nice@zeronice-hacktheplanet:~$ 




and when i do the gui it says failed for the ones that are ign. there hasent been a update in like 2 weeks.

---

### Post by wojox on 2010-03-31
What errors come back when you run this in the terminal:

```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by acemanollie on 2010-03-31
zer0nice@zeronice-hacktheplanet:~$ sudo apt-get upgrade && sudo apt-get dist-upgrade
[sudo] password for zer0nice: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zer0nice@zeronice-hacktheplanet:~$

---

### Post by undecim on 2010-03-31
I don't have the GUI package manager installed on this system (I built from minimal), but I get similar results on the command line with no problems.

```
sudo aptiundecim@caffeine ^_^ ~$ sudo aptitude update
[sudo] password for undecim: 
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Hit http://security.ubuntu.com karmic-security Release.gpg                      
Ign http://security.ubuntu.com karmic-security/main Translation-en_US           
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US     
Hit http://ppa.launchpad.net karmic Release.gpg                                 
Ign http://ppa.launchpad.net karmic/main Translation-en_US                      
Hit http://archive.getdeb.net karmic-getdeb Release.gpg                         
Ign http://archive.getdeb.net karmic-getdeb/apps Translation-en_US              
Ign http://archive.getdeb.net karmic-getdeb/games Translation-en_US             
Hit http://deb.torproject.org karmic Release.gpg                                
Ign http://deb.torproject.org karmic/main Translation-en_US                     
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US       
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com karmic-security Release                          
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US              
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                     
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US      
Hit http://ppa.launchpad.net karmic Release                                     
Hit http://archive.getdeb.net karmic-getdeb Release                             
Hit http://deb.torproject.org karmic Release                                    
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com karmic Release                                 
Hit http://security.ubuntu.com karmic-security/main Packages                    
Hit http://ppa.launchpad.net karmic/main Packages                               
Hit http://archive.getdeb.net karmic-getdeb/apps Packages                       
Ign http://deb.torproject.org karmic/main Packages                              
Hit http://us.archive.ubuntu.com karmic-updates Release              
Hit http://security.ubuntu.com karmic-security/restricted Packages              
Hit http://security.ubuntu.com karmic-security/main Sources                     
Hit http://security.ubuntu.com karmic-security/restricted Sources               
Hit http://security.ubuntu.com karmic-security/universe Packages                
Hit http://archive.getdeb.net karmic-getdeb/games Packages                      
Ign http://deb.torproject.org karmic/main Packages                              
Hit http://us.archive.ubuntu.com karmic/main Packages                
Hit http://us.archive.ubuntu.com karmic/restricted Packages          
Hit http://us.archive.ubuntu.com karmic/main Sources                 
Hit http://us.archive.ubuntu.com karmic/restricted Sources           
Hit http://us.archive.ubuntu.com karmic/universe Packages            
Hit http://security.ubuntu.com karmic-security/universe Sources      
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://security.ubuntu.com karmic-security/multiverse Sources    
Hit http://us.archive.ubuntu.com karmic/universe Sources             
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://deb.torproject.org karmic/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done

undecim@caffeine ^_^ ~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  devicekit-disks tzdata tzdata-java 
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,002kB of archives. After unpacking 12.3kB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com karmic-updates/main tzdata-java 2010g-0ubuntu0.9.10 [144kB]
Get:2 http://us.archive.ubuntu.com karmic-updates/main tzdata 2010g-0ubuntu0.9.10 [682kB]
Get:3 http://us.archive.ubuntu.com karmic-updates/main devicekit-disks 007-2ubuntu6 [176kB]
Fetched 1,002kB in 2s (428kB/s)      
Preconfiguring packages ...
(Reading database ... 202370 files and directories currently installed.)
Preparing to replace tzdata-java 2010e-0ubuntu0.9.10 (using .../tzdata-java_2010g-0ubuntu0.9.10_all.deb) ...
Unpacking replacement tzdata-java ...
Preparing to replace tzdata 2010e-0ubuntu0.9.10 (using .../tzdata_2010g-0ubuntu0.9.10_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2010g-0ubuntu0.9.10) ...

Current default time zone: 'America/Chicago'
Local time is now:      Wed Mar 31 12:50:14 CDT 2010.
Universal Time is now:  Wed Mar 31 17:50:14 UTC 2010.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Reading database ... 202374 files and directories currently installed.)
Preparing to replace devicekit-disks 007-2ubuntu5 (using .../devicekit-disks_007-2ubuntu6_amd64.deb) ...
Unpacking replacement devicekit-disks ...
Processing triggers for man-db ...
Setting up tzdata-java (2010g-0ubuntu0.9.10) ...
Setting up devicekit-disks (007-2ubuntu6) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 0 updates [-3].
undecim@caffeine ^_^ ~$ 
```

are you sure this is a problem?

---

### Post by acemanollie on 2010-03-31
im not sure. there hasent been a update in a while.

---

### Post by NCLI on 2010-03-31
How long is "a while"?

To me, it looks like there are no updates to install.

---

### Post by acemanollie on 2010-03-31
2 weeks for sec updates. and a last week for some time zone stuff

thats the last time there was updates

---

### Post by LowSky on 2010-03-31
open synaptic, click on mark all upgrades, then hit apply.
Worse case check software sources to make sure you computer is set to accept updates.

---

### Post by acemanollie on 2010-03-31
how do i check to see if my comp is set to accept updates. i dont know how to use software sources.

---

### Post by slakkie on 2010-03-31
Well, apt-get update won't update a single package, just the package list.

apt-get upgrade would upgrade if there are upgrades available. And it is perfectly possible that no updates are needed for the packages you have installed. Nothing to worry about. Wait another week or so and then try again.

Anyhows, use aptitude, far better then apt-get :)

---

### Post by acemanollie on 2010-03-31
> **slakkie said:**
> Well, apt-get update won't update a single package, just the package list.

apt-get upgrade would upgrade if there are upgrades available. And it is perfectly possible that no updates are needed for the packages you have installed. Nothing to worry about. Wait another week or so and then try again.

Anyhows, use aptitude, far better then apt-get :)


ok. i was just concerned because there hasent been a sec update in a while

---

