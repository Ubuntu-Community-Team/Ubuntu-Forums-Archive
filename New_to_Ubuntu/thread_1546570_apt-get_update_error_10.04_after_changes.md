---
title: "apt-get update error 10.04 after changes"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2010-08-05
Here is what happens when I run ```
sudo apt-get update
```  I have done a fresh install of 10.04, but I replaced my /etc folder and /home folder but merged the two together.  Any ideas?  Is this a simple fix?

**Output:**

```

sudo apt-get update 
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ lucid/partner Translation-en_US              
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/ lucid/main Translation-en_US
Get:2 http://packages.medibuntu.org jaunty Release.gpg [197B]                  
Ign http://packages.medibuntu.org/ jaunty/free Translation-en_US               
Ign http://packages.medibuntu.org/ jaunty/non-free Translation-en_US           
Hit http://linux.dropbox.com lucid Release.gpg                                 
Get:3 http://dl.google.com stable Release [2,544B]                             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Hit http://security.ubuntu.com lucid-security Release                          
Ign http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Get:4 http://ppa.launchpad.net jaunty Release.gpg [307B]                       
Ign http://ppa.launchpad.net/m-buck/gtk-desktop-info/ubuntu/ jaunty/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Get:5 http://packages.medibuntu.org jaunty Release [11.7kB]                    
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US              
Get:6 http://dl.google.com stable/main Packages [1,072B]                       
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.canonical.com lucid/partner Packages                        
Get:7 http://ppa.launchpad.net jaunty Release [74.7kB]                         
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://ppa.launchpad.net jaunty Release                                    
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/main Sources                            
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://linux.dropbox.com lucid Release                                     
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://ppa.launchpad.net lucid/main Packages                               
Ign http://packages.medibuntu.org jaunty Release                               
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://us.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages             
Hit http://us.archive.ubuntu.com lucid-updates/main Sources                    
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://linux.dropbox.com lucid/main Packages                               
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages   
Hit http://ppa.launchpad.net jaunty/main Packages                    
Hit http://ppa.launchpad.net jaunty/main Sources                     
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://packages.medibuntu.org jaunty/free Packages               
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources              
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Fetched 16.0kB in 5s (2,752B/s)
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C303E756BBC89BD
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

Here is the output of my /etc/apt/sources.list

```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner

```

---

### Post by drs305 on 2010-08-05
Your sources.list doesn't contain references to Jaunty, but you probably have some jaunty listings in the  /etc/sources.list.d folder. You can take a look into that folder manually or via Synaptic or Software Sources go to Settings, Respositories and check the "Third Party" or "Other Software" tabs for repositories that still list Jaunty.

Note you might also want to update your Ubuntu Forum profile to reflect that you are now running Lucid.   :-)

---

### Post by x C0MMAND0 x on 2010-08-05
I remembered I had added some items to "other sources" (see attached screenshot).  I thought that was a graphical end to /etc/apt/sources.list but perhaps I am wrong?  See attached screenshot that is my guess as to what is causing the error.

---

### Post by x C0MMAND0 x on 2010-08-05
Sounds like you pointed me in the right direction, I removed all Jaunty from the "other sources" and it cleared up.  On a side note, I am getting the following error when I try to install one of my favorite applications, perhaps you can help?  Otherwise I will mark this solved and start a new thread.

Here is the error

```

sudo apt-get install kpowersave 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kpowersave is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kpowersave has no installation candidate

```

---

### Post by drs305 on 2010-08-06
I did a brief search and it appears kpowersave is no longer supported by Lucid's repositories. It looks like the last one to include it was Karmic. You might be able to use the .deb on this page:
[http://packages.debian.org/sid/m68k/kpowersave/download]("http://packages.debian.org/sid/m68k/kpowersave/download")
but I have no idea about it's dependencies.

There is also CPU frequency scaling available in Ubuntu. Right click the top panel, Add to Panel, and you will see it.

---

