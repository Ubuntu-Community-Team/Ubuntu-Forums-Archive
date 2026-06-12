---
title: "Synaptic Package Manager Error"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by malty on 2009-11-25
Getting the following error..(in 9.04)

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Doing  gksudo gedit /etc/apt/sources.list  giver the following.....

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://ppa.launchpad.net/gnac-team/ppa/ubuntu](http://ppa.launchpad.net/gnac-team/ppa/ubuntu) jaunty main
deb [http://winff.org/ubuntu](http://winff.org/ubuntu) jaunty universe
deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu) jaunty main

Any suggestions please.

---

### Post by pi.boy.travis on 2009-11-25
Try opening a terminal, and running:

sudo apt-get update

and then:

sudo apt-get upgrade


Hope this helps. . .

---

### Post by malty on 2009-11-26
pbt
   Thanks for response, tried that, this is what I get....

john@john-desktop:~$ sudo apt-get update
[sudo] password for john: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://winff.org](http://winff.org) jaunty Release.gpg                                        
Ign [http://winff.org](http://winff.org) jaunty/universe Translation-en_GB                         
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_GB            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty Release.gpg                     
Ign [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty/main Translation-en_GB          
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Hit [http://winff.org](http://winff.org) jaunty Release                                            
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty Release                         
Get: 4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://winff.org](http://winff.org) jaunty/universe Packages                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources   
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Fetched 616B in 0s (834B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Any help would be appreciated.

---

### Post by MelDJ on 2009-11-26
tried this? [http://ubuntuforums.org/archive/index.php/t-440883.html](http://ubuntuforums.org/archive/index.php/t-440883.html)

---

### Post by kansasnoob on 2009-11-26
Looking at this:

> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

The medibuntu repo may be the culprit so I'd run:

```
gksudo gedit /etc/apt/sources.list
```

And "comment out" the medibuntu repo as indicated below in red (I'm only using red for visibility):

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
**[COLOR="Red"]#[/COLOR]**deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://ppa.launchpad.net/gnac-team/ppa/ubuntu](http://ppa.launchpad.net/gnac-team/ppa/ubuntu) jaunty main
deb [http://winff.org/ubuntu](http://winff.org/ubuntu) jaunty universe
deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu) jaunty main

Then click on Save, then File > Quit.

Then run apt-get update & apt-get upgrade again to see what happens. If that fixes it you'll probably need to remove the medibuntu repo and old gpg key and then reinstall medibuntu.

---

### Post by malty on 2009-11-26
kansasnoob, tried that, get this.......

 
john@john-desktop:~$ sudo apt-get update
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty Release.gpg                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages                      
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty/main Translation-en_GB          
Hit [http://winff.org](http://winff.org) jaunty Release.gpg                                        
Ign [http://winff.org](http://winff.org) jaunty/universe Translation-en_GB                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages                    
Get: 4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://winff.org](http://winff.org) jaunty Release                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty/main Packages                   
Hit [http://winff.org](http://winff.org) jaunty/universe Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Fetched 616B in 0s (785B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/winff.org_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
john@john-desktop:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/winff.org_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Thanks for the suggestion.

---

### Post by MaxIBoy on 2009-11-26
Looks like problems with this configuration file:
/var/lib/apt/lists/winff.org_ubuntu_dists_jaunty_universe_binary-i386_Packages
That file is a list of packages installed from one of your sources, specifically winff.org.

Looking at [http://winff.org](http://winff.org), it appears that winff is a GPL program with its own Ubuntu repositories, and you added those repos to your apt configuration. (Neat looking program by the way.)

Try removing those repositories and see if that fixes anything.

Also, winff is in the Debian repos already, and I bet it's in the Ubuntu repos too. Unless its an issue with outdated versions, you could probably just install it from the main Ubuntu repos.

---

### Post by Paqman on 2009-11-26
> **MaxIBoy said:**
> 
Also, winff is in the Debian repos already, and I bet it's in the Ubuntu repos too.

[Behold!]("http://packages.ubuntu.com/karmic/winff")

It's in the Universe repo, so as long as you're subscribed to that you can get it through any of the normal package management tools (eg: Synaptic)

---

### Post by malty on 2009-11-26
MaxIBoy, Paqman

Locked out of Synaptic with this message,,,

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/winff.org_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

How then, do I remove offending package.

Its icon is in..Applications..sound and Video..winff, I think I installed as a requirement for the ITV player (didn't work anyway)

Kind regards.

---

### Post by kansasnoob on 2009-11-26
> **malty said:**
> MaxIBoy, Paqman

Locked out of Synaptic with this message,,,

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/winff.org_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

How then, do I remove offending package.

Its icon is in..Applications..sound and Video..winff, I think I installed as a requirement for the ITV player (didn't work anyway)

Kind regards.

Just edit the sources.list again like you did for medibuntu only this time for winff:

> #deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://ppa.launchpad.net/gnac-team/ppa/ubuntu](http://ppa.launchpad.net/gnac-team/ppa/ubuntu) jaunty main
#deb [http://winff.org/ubuntu](http://winff.org/ubuntu) jaunty universe
deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu) jaunty main

I'm suggesting using comments (#) rather than actually removing things because it's easier to undo if it does no good.

You should be able to comment out any of the added ppa's just to troubleshoot this.

Also, I doubt this actually applies but, make sure that the terminal and synaptic are not both open at the same time.

---

### Post by malty on 2009-11-26
kansasnoob
            tried that, same response....

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/winff.org_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
john@john-desktop:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/winff.org_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened. 

thanks for suggestion.  "You should be able to comment out any of the added ppa's just to troubleshoot this."  wouldn't know what to look for.

Kind regards  
      malty

---

### Post by Paqman on 2009-11-27
Make sure you've commented out every reference to winff in your sources.list, you've got several in there.

---

### Post by malty on 2009-11-27
kansasnoob, tried that, including commenting out the three ppa lines, got the following....

john@john-desktop:~$ sudo apt-get update & apt-get upgrade
[1] 7166
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB           
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg [189B]          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release [57.9kB]            
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty Release.gpg              
Ign [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty/main Translation-en_GB   
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages            
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages [210kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages [2599B]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources [58.6kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources [509B]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages [90.8kB]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources [24.9kB]
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages [8128B]
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]
Fetched 456kB in 2s (173kB/s)                      
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repository.akirad.net_dists_akirad-jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
 Help!

---

### Post by MaxIBoy on 2009-11-27
See how the next one causing problems is repository.akirad.net? Do the same for that. And keep going for every one that causes problems.

If you eventually wind up having to comment out every single one, then naturally that's no good either, but let us know if you actually have to go that far. (Won't break anything, but you won't be able to see updates or install from the repos either.)

---

### Post by malty on 2009-11-27
Really perplexed, did gksudo....
 gksudo gedit /var/lib/apt/lists/repository.akirad.net_dists_akirad-jaunty_main_binary-i386_Packages

which gave me this.......

   </tr>
    <tr>
      <td colspan="2"><img src="/images/spacer.gif" border="0" width="1" height="10" alt=""><br></td>
    </tr>
    <tr style="background:url(/images/wave.gif) no-repeat center center;margin-top:15px">
      <td valign="top" style="padding-top:20px;padding-left:15px;">
        <script type="text/javascript">writeMenu();</script>
      </td>
      <td valign="top">
        <table cellpadding="0" cellspacing="0" border="0" style="margin-top:15px">
          <script type="text/javascript">writeNavBar();</script>
          <tr>
            <td>
              <table width="700" cellspacing="0" cellpadding="0" border="0">
                <tr>
                  <td>
                   <script type="text/javascript">new pm('error', 'Your DSL connection is down. Verify that your SpeedTouch is correctly connected to your phone line. If the problem persists, check your documentation.');</script>

<script type="text/javascript">pm_write_messages();</script>



<table cellspacing='0' cellpadding='0'><tr><td align='left'><img src='/images/spacer.gif' width='120' alt='' border='0'></td><td align='left'><div class='contentcontainer'>
<table cellspacing='0' cellpadding='0'><tr><td align='left'><span class='itemtitle'>Not Connected...</span></td><td align='right'></td></tr><tr><td colspan='2'><img src='/images/spacer.gif' width='600' height='20' alt='' border='0'></td></tr></table><p>Your DSL connection is down.</p>
<p>Verify if your SpeedTouch is correctly connected to your DSL line.  For more information consult your documentation.</p>
<p>Please close this window and try again.</p>
</div>
</td></tr></table>                  </td>
                </tr>
              </table>
            </td>
          </tr>
        </table>
      </td>
    </tr>
  </table>
</body>
</html><!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
  <title>SpeedTouch</title>
  <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
  <script type="text/javascript">var g_navitem = -1;</script>
  <script type="text/javascript"> var g_focus = -1;</script>
  <script type='text/javascript' src='/cgi/b/ic/util.js'></script>
  <link rel="stylesheet" type="text/css" href="/styles.css">
</head>
<body onLoad="setFocus();" height="100%" style="margin:0px">
  <noscript>
    <h1>Thomson - SpeedTouch</h1>
    <h4>To view the Web interface of the SpeedTouch, JavaScript must be supported and enabled on your browser! <br><br>Please enable scripting and refresh your browser.</h4>
  </noscript>
  <table cellspacing="0" cellpadding="0" border="0" width="100%" style="background-color:white" height="100%">
    <tr>
      <td colspan="2">
        <table width="100%" cellspacing="0" cellpadding="0" border="0">
          <tr>
            <td style="padding-left:15px;" class="Product">THOMSON&nbsp;ST536</td><td align="right" style="padding:5px 15px 0px 0px;"><a href="/"><img src="/images/Thomson.gif" border="0" width="109" height="50" alt="THOMSON logo"></a></td>
          </tr>      
          <tr>
            <td colspan="2">
              <table width="100%" cellspacing="0" cellpadding="0" border="0">
                <tr style="background-image:url(/images/bar.gif)">
                  <td width="20%"></td>
                  <td width="10" align="left"></td>
                  <td width="10"><img src="/images/barend_left.gif"></td>
                  <td><img width="100%" height="10" src="/images/spacer_white.gif"></td>
                </tr>
                <tr style="background-image:url(/images/bar.gif)">
                  <td align="right"><img width="100%" height="10" src="/images/spacer_white.gif"></td>
                  <td width="10"><img src="/images/barend_right.gif"></td>
                  <td colspan="2"></td>
                </tr>
              </table>
            </td>
          </tr>
          <tr>
            <td></td><td align="right" valign="middle" style="padding-right:15px"><form name="langSelect" action="/cgi/language.cgi" method=post><span class="langSelect"><input type="hidden" name=6 value="en"></span></form></td>
          </tr>
        </table>
      </td>

Can't see what to comment out, if its part of the modem setup, should I ?

---

### Post by Paqman on 2009-11-27
> **malty said:**
> 
Can't see what to comment out

You want to be commenting out the lines in your sources that are causing the errors, just like you did for the previous ones.

---

### Post by malty on 2009-11-27
Commented out all suspect lines (last seven) no luck, no other obvious culprit in the /etc/apt/sources.list.
No reference to akirad there, any other place akirad might be?


# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
#deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
#deb [http://ppa.launchpad.net/gnac-team/ppa/ubuntu](http://ppa.launchpad.net/gnac-team/ppa/ubuntu) jaunty main
#deb [http://winff.org/ubuntu](http://winff.org/ubuntu) jaunty universe
#deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) jaunty main
#deb [http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu) jaunty main

Regards Malty

---

### Post by malty on 2009-11-28
Sorted...it became obvious that commenting out was not the fix, I tried System-software sources-third party. Then removed the akirad repository, this did the fix.

The lesson being, be carefull of third party dodgy software.

Thanks for all of your help everyone.
  
Malty.

---

