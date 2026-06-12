---
title: "Duplicate sources.list"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by Fiddlenut on 2011-05-23
Hello,
I've looked around the forum to sort out what's happening inside my computer, but I guess I don't know how to even ask my question, so I'll let the terminal do the explaining:

Every time I type the sudo apt-get update command, this is what I get.

```
loic@loic-desktop:~$ sudo apt-get update
Ign http://ppa.launchpad.net natty InRelease
Ign http://archive.canonical.com natty InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://fr.archive.ubuntu.com maverick-backports InRelease                  
Ign http://archive.ubuntu.com natty InRelease                                  
...................et cetera................
Ign http://archive.ubuntu.com natty-proposed/main Translation-oc
Ign http://archive.ubuntu.com natty-proposed/main Translation-fr
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_GB
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_CA
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_AU
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-oc
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-fr
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_GB
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_CA
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_AU
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-oc
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-fr
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_GB
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_CA
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_AU
Ign http://archive.ubuntu.com natty-proposed/universe Translation-oc
Ign http://archive.ubuntu.com natty-proposed/universe Translation-fr
Fetched 59.3 kB in 14s (4,178 B/s)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ natty-backports/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ natty-backports/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ natty-backports/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ natty-backports/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-backports_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
loic@loic-desktop:~$ 
```

I feel like I'm going around in circles. Thank you for any help!

---

### Post by beew on 2011-05-23
It is because you have enabled the same repos several times (in different language?) so just disable the duplicates.

---

### Post by micael3000 on 2011-05-23
- Open /etc/apt/sources.list with an editor (suggestion: "sudo nano /etc/apt/sources.list").
- Locate the duplicated lines and place your cursor there. 
- Press crtl+k until you remove all of them.
- Press crtl+x and Y for saving the file.

sources.list keeps the list of repositories where the applications lies. In your case, there are repeated registers, you just have to remove them (by doing the steps on this post) =]

---

### Post by Fiddlenut on 2011-05-23
Okay,
I'll look around to find out how to do that.
Thanks beew!

---

### Post by Fiddlenut on 2011-05-23
Sorry, cross-post
Thanks micael

---

### Post by beew on 2011-05-23
> **Fiddlenut said:**
> Okay,
I'll look around to find out how to do that.
Thanks beew!

Open Synaptic, go to Settings > Repositories. Look at the tabs "Ubuntu Software" and "Other Software" and uncheck the boxes of the duplicates, keeping only one version checked (or highlight and remove the duplicates keeping only one version)

---

### Post by Fiddlenut on 2011-05-23
Well, that didn't work...
I removed the Maverick Meerkat repo thinking that might be the problem because it started with "fr.", but now I think I might be up a certain creek without a paddle...
Here's what the terminal says:

```
loic@loic-desktop:~$ sudo apt-get install updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package updates
loic@loic-desktop:~$ sudo apt-get install updates
[sudo] password for loic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package updates
loic@loic-desktop:~$ 
```

Now what?
Yes, I know, I **am** reading the manual :-)

---

### Post by plucky on 2011-05-23
> sudo apt-get install updates


That command tries to install a package called "updates",which doesn't exist.

Which is why you get > E: Unable to locate package updates

Try ```
sudo apt-get update
```

Also post the output of ```
cat /etc/apt/sources.list
```

---

### Post by Fiddlenut on 2011-05-23
So here's what I get with

```
loic@loic-desktop:~$ sudo apt-get update
Ign http://ppa.launchpad.net natty InRelease
Ign http://extras.ubuntu.com natty InRelease                        
Ign http://archive.canonical.com natty InRelease                    
Ign http://archive.ubuntu.com natty InRelease                        
Ign http://archive.ubuntu.com natty-updates InRelease                
Ign http://archive.ubuntu.com natty-security InRelease                         
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                       
Hit http://archive.canonical.com natty Release.gpg                   
Ign http://archive.ubuntu.com natty-backports InRelease              
Ign http://archive.ubuntu.com natty-proposed InRelease               
Hit http://archive.ubuntu.com natty Release.gpg                                
Hit http://extras.ubuntu.com natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://archive.canonical.com natty Release                        
Hit http://archive.ubuntu.com natty-updates Release.gpg               
Hit http://archive.ubuntu.com natty-security Release.gpg
Hit http://archive.ubuntu.com natty-backports Release.gpg
Hit http://archive.ubuntu.com natty-proposed Release.gpg              
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://archive.ubuntu.com natty Release                          
Hit http://archive.ubuntu.com natty-updates Release                  
Hit http://archive.ubuntu.com natty-security Release                 
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://archive.ubuntu.com natty-backports Release                          
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://archive.ubuntu.com natty-proposed Release                           
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://archive.ubuntu.com natty/universe Sources                           
Hit http://archive.ubuntu.com natty/restricted Sources                         
Hit http://archive.ubuntu.com natty/multiverse Sources                         
Hit http://archive.ubuntu.com natty/main i386 Packages                         
Hit http://archive.ubuntu.com natty/universe i386 Packages                     
Hit http://archive.ubuntu.com natty/restricted i386 Packages         
Hit http://archive.ubuntu.com natty/multiverse i386 Packages                   
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Hit http://archive.ubuntu.com natty-updates/main Sources                       
Hit http://archive.ubuntu.com natty-updates/universe Sources                   
Hit http://archive.ubuntu.com natty-updates/restricted Sources                 
Hit http://archive.ubuntu.com natty-updates/multiverse Sources                 
Hit http://archive.ubuntu.com natty-updates/main i386 Packages                 
Hit http://archive.ubuntu.com natty-updates/universe i386 Packages             
Hit http://archive.ubuntu.com natty-updates/restricted i386 Packages           
Hit http://archive.ubuntu.com natty-updates/multiverse i386 Packages           
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Hit http://archive.ubuntu.com natty-security/main Sources                      
Hit http://archive.ubuntu.com natty-security/universe Sources                  
Hit http://archive.ubuntu.com natty-security/restricted Sources                
Hit http://archive.ubuntu.com natty-security/multiverse Sources                
Hit http://archive.ubuntu.com natty-security/main i386 Packages                
Hit http://archive.ubuntu.com natty-security/universe i386 Packages            
Hit http://archive.ubuntu.com natty-security/restricted i386 Packages          
Hit http://archive.ubuntu.com natty-security/multiverse i386 Packages          
Ign http://archive.ubuntu.com natty-security/main TranslationIndex             
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex         
Hit http://archive.ubuntu.com natty-backports/main Sources                     
Hit http://archive.ubuntu.com natty-backports/universe Sources                 
Hit http://archive.ubuntu.com natty-backports/restricted Sources               
Hit http://archive.ubuntu.com natty-backports/multiverse Sources               
Hit http://archive.ubuntu.com natty-backports/main i386 Packages               
Hit http://archive.ubuntu.com natty-backports/universe i386 Packages           
Hit http://archive.ubuntu.com natty-backports/restricted i386 Packages         
Hit http://archive.ubuntu.com natty-backports/multiverse i386 Packages         
Ign http://archive.ubuntu.com natty-backports/main TranslationIndex            
Ign http://archive.ubuntu.com natty-backports/multiverse TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/restricted TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/universe TranslationIndex        
Hit http://archive.ubuntu.com natty-proposed/main Sources                      
Hit http://archive.ubuntu.com natty-proposed/universe Sources                  
Hit http://archive.ubuntu.com natty-proposed/restricted Sources                
Hit http://archive.ubuntu.com natty-proposed/multiverse Sources                
Hit http://archive.ubuntu.com natty-proposed/main i386 Packages                
Hit http://archive.ubuntu.com natty-proposed/universe i386 Packages            
Hit http://archive.ubuntu.com natty-proposed/restricted i386 Packages          
Hit http://archive.ubuntu.com natty-proposed/multiverse i386 Packages          
Ign http://archive.ubuntu.com natty-proposed/main TranslationIndex             
Ign http://archive.ubuntu.com natty-proposed/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-proposed/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-proposed/universe TranslationIndex         
Ign http://ppa.launchpad.net natty/main Translation-en_GB                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en_GB               
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://extras.ubuntu.com natty/main Translation-en_GB                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Hit http://archive.ubuntu.com natty/main Translation-en_GB                     
Ign http://extras.ubuntu.com natty/main Translation-en_CA                      
Hit http://archive.ubuntu.com natty/main Translation-en_CA                     
Hit http://archive.ubuntu.com natty/main Translation-en_AU                     
Hit http://archive.ubuntu.com natty/main Translation-oc                        
Hit http://archive.ubuntu.com natty/main Translation-fr                        
Ign http://ppa.launchpad.net natty/main Translation-en_CA                      
Ign http://archive.canonical.com natty/partner Translation-en_CA               
Ign http://archive.canonical.com natty/partner Translation-en_AU               
Ign http://archive.canonical.com natty/partner Translation-oc                  
Ign http://extras.ubuntu.com natty/main Translation-en_AU                      
Ign http://extras.ubuntu.com natty/main Translation-oc                         
Hit http://archive.ubuntu.com natty/multiverse Translation-en_GB               
Hit http://archive.ubuntu.com natty/multiverse Translation-en_AU               
Ign http://ppa.launchpad.net natty/main Translation-en_AU                      
Ign http://ppa.launchpad.net natty/main Translation-oc                         
Ign http://ppa.launchpad.net natty/main Translation-fr                         
Hit http://archive.ubuntu.com natty/multiverse Translation-oc                  
Hit http://archive.ubuntu.com natty/multiverse Translation-fr        
Hit http://archive.ubuntu.com natty/restricted Translation-en_GB     
Hit http://archive.ubuntu.com natty/restricted Translation-en_CA     
Hit http://archive.ubuntu.com natty/restricted Translation-en_AU     
Ign http://archive.canonical.com natty/partner Translation-fr        
Ign http://extras.ubuntu.com natty/main Translation-fr               
Hit http://archive.ubuntu.com natty/restricted Translation-oc        
Hit http://archive.ubuntu.com natty/restricted Translation-fr
Hit http://archive.ubuntu.com natty/universe Translation-en_GB
Hit http://archive.ubuntu.com natty/universe Translation-oc
Hit http://archive.ubuntu.com natty/universe Translation-fr
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_CA
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_CA
Ign http://archive.ubuntu.com natty/universe Translation-en_AU
Ign http://archive.ubuntu.com natty-updates/main Translation-en_GB
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_CA
Ign http://archive.ubuntu.com natty-updates/main Translation-en_AU
Ign http://archive.ubuntu.com natty-updates/main Translation-oc
Ign http://archive.ubuntu.com natty-updates/main Translation-fr
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_GB
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_CA
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_AU
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-oc
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-fr
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_CA
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_AU
Ign http://archive.ubuntu.com natty-updates/restricted Translation-oc
Ign http://archive.ubuntu.com natty-updates/restricted Translation-fr
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_GB
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_CA
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_AU
Ign http://archive.ubuntu.com natty-updates/universe Translation-oc
Ign http://archive.ubuntu.com natty-updates/universe Translation-fr
Ign http://archive.ubuntu.com natty-security/main Translation-en_GB
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_CA
Ign http://archive.ubuntu.com natty-security/main Translation-en_AU
Ign http://archive.ubuntu.com natty-security/main Translation-oc
Ign http://archive.ubuntu.com natty-security/main Translation-fr
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_GB
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_CA
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_AU
Ign http://archive.ubuntu.com natty-security/multiverse Translation-oc
Ign http://archive.ubuntu.com natty-security/multiverse Translation-fr
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_CA
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_AU
Ign http://archive.ubuntu.com natty-security/restricted Translation-oc
Ign http://archive.ubuntu.com natty-security/restricted Translation-fr
Ign http://archive.ubuntu.com natty-security/universe Translation-en_GB
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_CA
Ign http://archive.ubuntu.com natty-security/universe Translation-en_AU
Ign http://archive.ubuntu.com natty-security/universe Translation-oc
Ign http://archive.ubuntu.com natty-security/universe Translation-fr
Ign http://archive.ubuntu.com natty-backports/main Translation-en_GB
Ign http://archive.ubuntu.com natty-backports/main Translation-en
Ign http://archive.ubuntu.com natty-backports/main Translation-en_CA
Ign http://archive.ubuntu.com natty-backports/main Translation-en_AU
Ign http://archive.ubuntu.com natty-backports/main Translation-oc
Ign http://archive.ubuntu.com natty-backports/main Translation-fr
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en_GB
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en_CA
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en_AU
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-oc
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-fr
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en_GB
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en_CA
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en_AU
Ign http://archive.ubuntu.com natty-backports/restricted Translation-oc
Ign http://archive.ubuntu.com natty-backports/restricted Translation-fr
Ign http://archive.ubuntu.com natty-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com natty-backports/universe Translation-en
Ign http://archive.ubuntu.com natty-backports/universe Translation-en_CA
Ign http://archive.ubuntu.com natty-backports/universe Translation-en_AU
Ign http://archive.ubuntu.com natty-backports/universe Translation-oc
Ign http://archive.ubuntu.com natty-backports/universe Translation-fr
Ign http://archive.ubuntu.com natty-proposed/main Translation-en_GB
Ign http://archive.ubuntu.com natty-proposed/main Translation-en
Ign http://archive.ubuntu.com natty-proposed/main Translation-en_CA
Ign http://archive.ubuntu.com natty-proposed/main Translation-en_AU
Ign http://archive.ubuntu.com natty-proposed/main Translation-oc
Ign http://archive.ubuntu.com natty-proposed/main Translation-fr
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_GB
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_CA
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_AU
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-oc
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-fr
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_GB
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_CA
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_AU
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-oc
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-fr
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_GB
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_CA
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_AU
Ign http://archive.ubuntu.com natty-proposed/universe Translation-oc
Ign http://archive.ubuntu.com natty-proposed/universe Translation-fr
Reading package lists... Done
```

and then with


```
loic@loic-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu natty main universe restricted multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates main universe restricted multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://archive.ubuntu.com/ubuntu natty-security main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security main universe restricted multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu natty-backports main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-backports main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu natty-proposed main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-proposed main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu natty-backports main
loic@loic-desktop:~$ 
```

Thanks plucky

---

### Post by plucky on 2011-05-23
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-backports main


That line is already in the list as > deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-backports main universe restricted multiverse

Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of the line.

Or us the Software Sources GUI and un-tick the extra repositories.

You also don't need the deb-src repositories unless you want the source files.

I would also disable the backports repositories unless you want to install some packages that might break your system.


Good Luck

---

### Post by Fiddlenut on 2011-05-23
All right plucky,

That seems to have fixed it. I'll just wait 'till new upgrades come in again to see.

Thank you all for the help!

---

