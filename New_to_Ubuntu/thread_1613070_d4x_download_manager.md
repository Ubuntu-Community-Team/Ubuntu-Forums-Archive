---
title: "d4x download manager"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by mlempenau on 2010-11-04
I am trying to install d4x download manager but can not find the location of the source files.  

What I am really trying to do is to get a download manager similar to the one I had in windows that downloaded large files with an INTERNET connection that is slow at best.  It did this by downloading different parts of the file at the same time and then saving them together.  It worked very well.  I don't know if d4x will do this but the writeup seemed to indicate it did.  Any help is greatly appreciated.

---

### Post by sully101 on 2010-11-04
> **mlempenau said:**
> I am trying to install d4x download manager but can not find the location of the source files.  

What I am really trying to do is to get a download manager similar to the one I had in windows that downloaded large files with an INTERNET connection that is slow at best.  It did this by downloading different parts of the file at the same time and then saving them together.  It worked very well.  I don't know if d4x will do this but the writeup seemed to indicate it did.  Any help is greatly appreciated.

In a terminal type.

sudo apt-get install d4x

works for me! on lucid in universe repositories

---

### Post by mlempenau on 2010-11-04
Well, this is what happens ...

mikee@mike-desktop:~$ sudo apt-get install d4x
[sudo] password for mikee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package d4x
mikee@mike-desktop:~$

---

### Post by sikander3786 on 2010-11-04
> **mlempenau said:**
> Well, this is what happens ...

mikee@mike-desktop:~$ sudo apt-get install d4x
[sudo] password for mikee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package d4x
mikee@mike-desktop:~$
It is in the universe repositories. Make sure Universe is enabled in Software Sources under System > Administration > Software Sources.

---

### Post by mlempenau on 2010-11-04
I checked in Software sources as well as Synaptic.  In Synaptic it has maverick-proposed and maverick-updates for universe.  It is possible I need lucid source  to get it?  It is still not showing up.

---

### Post by mlempenau on 2010-11-04
I'm getting something different now when I use the terminal.  

mikee@mike-desktop:~$ sudo apt-get install d4x
[sudo] password for mikee: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mikee@mike-desktop:~$ 

I'm afraid I'm too new to understand this ...

---

### Post by Bapun007 on 2010-11-04
> **mlempenau said:**
> I'm getting something different now when I use the terminal.  

mikee@mike-desktop:~$ sudo apt-get install d4x
[sudo] password for mikee: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mikee@mike-desktop:~$ 

I'm afraid I'm too new to understand this ...

Close synaptic and all other programs . If not work restart .

---

### Post by sikander3786 on 2010-11-04
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

That error shows up when another process like Synaptic, Software Center, apt-get, aptitude, update manager, Add/Remove etc is running. Try to close all other programs as already mentioned and try again. If it still doesn't work, a reboot will sort it out.

---

### Post by mlempenau on 2010-11-05
after reboot the terminal went back to the original result.

mikee@mike-desktop:~$ sudo apt-get install d4x
[sudo] password for mikee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package d4x
mikee@mike-desktop:~$

So I guess there are two things to think about:
1.  Do I have the correct source?
2.  What else is causing the s/w not to see the install package?

---

### Post by sikander3786 on 2010-11-05
Once more, please copy paste this command into your terminal,

```
sudo apt-get update && sudo apt-get install d4x
```

If it doesn't work yet, please post the output of the above command and also your sources.list so we can have a look at it.

```
cat /etc/apt/sources.list
```

---

### Post by mlempenau on 2010-11-05
Ok, I have attached two files.  I think my sources list is messed up but have no idea what is wrong.  Thanks for help.

---

### Post by sikander3786 on 2010-11-05
Can you please post the output in your post and wrap it with code tags from # post menu. [code] at start and [ /code] at the end.

I am on a Windows computer right now and notepad doesn't appear to open it successfully.

Thanks.

---

### Post by mlempenau on 2010-11-05
Hope this works ... I'll post in two reply:
<code> mikee@mike-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-backports restricted main multiverse universe
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/ # disabled on upgrade to maverick
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/ # disabled on upgrade to maverick

# Fingerprint reader support (fprint)
deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
mikee@mike-desktop:~$ </code>

---

### Post by mlempenau on 2010-11-05
<code> mikee@mike-desktop:~$ sudo apt-get update && sudo apt-get install d4x
[sudo] password for mikee: 
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports Release.gpg
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en   
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports Release                       
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/main Sources                  
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/restricted Sources            
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/universe Sources              
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/multiverse Sources            
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/main i386 Packages            
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/restricted i386 Packages      
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/universe i386 Packages        
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/multiverse i386 Packages      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg [198B]                    
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg [197B]                
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Get:4 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                 
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [65B]                      
Ign [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Release.gpg                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Release.gpg           
Ign [http://www.geekconnection.org/remastersys/repository/](http://www.geekconnection.org/remastersys/repository/) ubuntu/ Translation-en
Ign [http://www.remastersys.klikit-linux.com/repository/](http://www.remastersys.klikit-linux.com/repository/) remastersys/ Translation-en
Ign [http://www.geekconnection.org/remastersys/repository/](http://www.geekconnection.org/remastersys/repository/) ubuntu/ Translation-en_US
Ign [http://www.remastersys.klikit-linux.com/repository/](http://www.remastersys.klikit-linux.com/repository/) remastersys/ Translation-en_US
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release.gpg                          
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Release               
Ign [http://www.geekconnection.org/remastersys/repository/](http://www.geekconnection.org/remastersys/repository/) karmic/ Translation-en
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Packages              
Ign [http://www.geekconnection.org/remastersys/repository/](http://www.geekconnection.org/remastersys/repository/) karmic/ Translation-en_US
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Packages              
Ign [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Release                              
Err [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Packages              
  404  Not Found
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release                              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en             
Ign [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Packages/DiffIndex                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en       
Ign [http://ppa.launchpad.net/madman2k/ubuntu/](http://ppa.launchpad.net/madman2k/ubuntu/) hardy/main Translation-en        
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages/DiffIndex                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en       
Ign [http://ppa.launchpad.net/madman2k/ubuntu/](http://ppa.launchpad.net/madman2k/ubuntu/) hardy/main Translation-en_US     
Ign [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Packages                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US    
Get:6 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en         
Ign [http://ppa.launchpad.net/madman2k/ubuntu/](http://ppa.launchpad.net/madman2k/ubuntu/) hardy/multiverse Translation-en  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US      
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Ign [http://ppa.launchpad.net/madman2k/ubuntu/](http://ppa.launchpad.net/madman2k/ubuntu/) hardy/multiverse Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg [198B]            
Ign [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Packages                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en     
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US           
Ign [http://ppa.launchpad.net/madman2k/ubuntu/](http://ppa.launchpad.net/madman2k/ubuntu/) hardy/restricted Translation-en  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US  
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Get:8 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://ppa.launchpad.net/madman2k/ubuntu/](http://ppa.launchpad.net/madman2k/ubuntu/) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Get:9 [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Packages [544B]                    
Ign [http://ppa.launchpad.net/madman2k/ubuntu/](http://ppa.launchpad.net/madman2k/ubuntu/) hardy/universe Translation-en    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Get:10 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en 
Ign [http://ppa.launchpad.net/madman2k/ubuntu/](http://ppa.launchpad.net/madman2k/ubuntu/) hardy/universe Translation-en_US 
Get:11 [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages [956B]                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Get:12 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources [3,618B]          
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg [198B]          
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en    
Get:15 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [7,437B]    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US 
Ign [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/) maverick/main Translation-en 
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Get:16 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [7,437B]    
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Get:18 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:19 [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release [6,857B]                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                             
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en             
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Get:20 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                         
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release.gpg [198B]          
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing/non-free Translation-en            
Get:22 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages/DiffIndex        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages/DiffIndex    
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing/non-free Translation-en_US         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources/DiffIndex                 
Get:23 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                            
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [57.3kB]                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources/DiffIndex             
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:25 [http://dl.google.com](http://dl.google.com) testing Release [2,513B]                           
Ign [http://dl.google.com](http://dl.google.com) testing Release                                       
Ign [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages/DiffIndex               
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://dl.google.com](http://dl.google.com) testing/non-free i386 Packages/DiffIndex              
Get:26 [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages [1,010B]             
Get:27 [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages [3,260B]      
Get:28 [http://dl.google.com](http://dl.google.com) testing/non-free i386 Packages [793B]              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Get:29 [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages [7,100B]  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Get:30 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources [3,287B]               
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Get:31 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources [5,593B]           
Get:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [39.8kB]                      
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release.gpg [198B]         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main i386 Packages                          
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Get:34 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [57.3kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/restricted i386 Packages                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe i386 Packages                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/multiverse i386 Packages                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Get:35 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [2,239B]                 
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release [39.8kB]                     
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [3,933B]           
Get:38 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages [14B]              
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release [31.4kB]             
Get:40 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [1,995B]                 
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release [27.2kB]            
Get:42 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [3,334B]           
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release [31.4kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main i386 Packages                          
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release [23.2kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/restricted i386 Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe i386 Packages                      
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages [1,492kB]         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/multiverse i386 Packages                    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main i386 Packages                          
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/restricted i386 Packages                    
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe i386 Packages                      
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/multiverse i386 Packages                    
  404  Not Found
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages [5,992B]    
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [5,791kB]     
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages [183kB]     
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages [75.4kB]  
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages [14B]
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages [32.9kB]
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages [1,963B]
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages [32.1kB] 
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages [12.8kB]
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages [1,660B]
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/main i386 Packages [35.3kB] 
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [14B]
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/universe i386 Packages [11.8kB]
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/restricted i386 Packages [14B]
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/main i386 Packages [14B]   
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/multiverse i386 Packages [14B]
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/universe i386 Packages [1,432B]
Fetched 8,057kB in 1min 51s (72.5kB/s)                                         
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: Failed to fetch [http://www.remastersys.klikit-linux.com/repository/remastersys/Packages.gz](http://www.remastersys.klikit-linux.com/repository/remastersys/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
mikee@mike-desktop:~$ sudo apt-get install d4x
Reading package lists... Done
Building dependency tree       
Reading state information... Done
W: Duplicate sources.list entry [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_maverick_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to locate package d4x
mikee@mike-desktop:~$ </code>

---

### Post by sadaruwan12 on 2010-11-05
Bro, I've also a windows user turned linux kind of a guy but when I did that I also had the same problem when I've to find a download manager that did what IDM did for me in the windows system.

So I found the perfect replacement and I never looked back. Actually it's a browser addon but works just fine like a stand alone software it also use the same method as the one you've used.

Here's the link:[http://www.downthemall.net/]("http://www.downthemall.net/")

This might solve your problem friend.

---

### Post by oldos2er on 2010-11-05
If you check packages.ubuntu.com, it appears d4x has been dropped from Maverick's repositories. You'll need to grab the Lucid version.

---

### Post by sikander3786 on 2010-11-05
I see many errors with your output.

First of all disable all the launchpad and other ppas from Software Center > Edit > Software Sources as they are giving 404 Error.

Secondly your medibuntu public key is missing. You can follow this thread for a workaround. See post # 25 specifically.

[http://ubuntuforums.org/showthread.php?t=983132&page=3](http://ubuntuforums.org/showthread.php?t=983132&page=3)

Although those apt-get errors have nothing to do with installation of d4x, you still need to solve the medibuntu repos as it contains many useful software you might need later on.

And **oldos2er** seems correct about d4x being dropped from maverick repos as I was unable to find one. You may download the lucid .deb here and try to install it.

[http://packages.ubuntu.com/search?keywords=d4x&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=d4x&searchon=names&suite=lucid&section=all)

---

### Post by Paul820 on 2010-11-05
There is also **multiget** you could try.
> sudo apt-get install multiget

---

### Post by oldos2er on 2010-11-05
If you're running 10.10 Maverick, you should remove all non-Maverick repositories from your sources.list!

---

### Post by nnamdi on 2010-11-05
hmm glad to be posting once again on ubuntu forum now down to the matter d4x has not really been working for me so i normally use a firefox plugin called : downloadthemall. and it has been nice...

---

### Post by mlempenau on 2010-11-05
Wow!  Thanks for all the help.  It will take me a while to sort it all out since I have to work at other things too.  I will try out the other programs and I knew there was something wrong with the sources list but now I understand it better.  I suspect you will see me back on this form for something else since I know just enough to lock up both my brain and my computer (normally at the same time!).

---

### Post by mlempenau on 2010-11-06
I followed the instructions listed in the link below but it keeps giving me the following error:  Unable to locate package medibuntu-keyring

medibuntu public key is missing. You can follow this thread for a workaround. See post # 25 specifically.
[http://ubuntuforums.org/showthread.php?t=983132&page=3](http://ubuntuforums.org/showthread.php?t=983132&page=3)


mikee@mike-desktop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
[sudo] password for mikee: 
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports Release.gpg
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en   
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en
Ign [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports Release                       
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en             
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/main Sources                  
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/restricted Sources            
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/universe Sources              
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/multiverse Sources            
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/main i386 Packages            
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/restricted i386 Packages      
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/universe i386 Packages        
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) lucid-backports/multiverse i386 Packages      
Get:2 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                          
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing/non-free Translation-en            
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing/non-free Translation-en_US         
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release.gpg                          
Ign [http://www.geekconnection.org/remastersys/repository/](http://www.geekconnection.org/remastersys/repository/) karmic/ Translation-en
Ign [http://www.geekconnection.org/remastersys/repository/](http://www.geekconnection.org/remastersys/repository/) karmic/ Translation-en_US
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release                              
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg [198B]                    
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages/DiffIndex                   
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [65B]                      
Get:6 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                 
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Get:8 [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages [956B]                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en             
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Get:9 [http://dl.google.com](http://dl.google.com) testing Release [2,513B]                            
Ign [http://dl.google.com](http://dl.google.com) testing Release                                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US          
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en       
Get:10 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [57.3kB]                      
Get:11 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [39.8kB]                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US    
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en       
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US    
Get:13 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]                  
Ign [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages/DiffIndex               
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US      
Get:14 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]                  
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [3,329B]           
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg [198B]           
Ign [http://dl.google.com](http://dl.google.com) testing/non-free i386 Packages/DiffIndex              
Get:17 [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages [1,010B]             
Get:18 [http://dl.google.com](http://dl.google.com) testing/non-free i386 Packages [793B]              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en     
Get:19 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources [3,618B]          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US  
Get:20 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [7,437B]    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Get:21 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [7,437B]    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Get:22 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages [14B]              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg [198B]          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release.gpg [198B]          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release [39.8kB]                     
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release [31.4kB]             
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release [27.2kB]            
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release [31.4kB]            
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release [23.2kB]           
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages [1,492kB]         
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages [5,992B]    
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [5,791kB]     
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages [183kB]     
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages [80.4kB]  
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages [14B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages [34.4kB]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages [1,963B]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages [32.1kB] 
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages [12.8kB]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages [1,660B]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/main i386 Packages [20.1kB] 
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [14B]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/universe i386 Packages [7,085B]
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/restricted i386 Packages [14B]
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/main i386 Packages [14B]   
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/multiverse i386 Packages [14B]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/universe i386 Packages [1,432B]
Fetched 7,958kB in 6min 24s (20.7kB/s)                                         
Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package medibuntu-keyring
mikee@mike-desktop:~$

---

### Post by Enigmapond on 2010-11-06
I use Jdownloader and it's just wonderful and works so much better than d4x...IMHO..
[https://launchpad.net/~jd-team/+archive/jdownloader](https://launchpad.net/~jd-team/+archive/jdownloader)

---

### Post by sikander3786 on 2010-11-06
> I followed the instructions listed in the link below but it keeps giving me the following error: Unable to locate package medibuntu-keyring

Ok. This command should update the medibuntu repository information and its GPG key.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

It is a single command. Copy/paste whole of it into terminal and run apt-get update afterwards to see the results.

Hope it works this time.

---

### Post by cem.beyaz on 2011-08-28
to install d4x on 11.04

open **terminal**
enter the following command
> sudo nano /etc/apt/sources.listadd the following line 
> deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) lucid main universerun below command
> sudo apt-get update && sudo apt-get install d4x

---

