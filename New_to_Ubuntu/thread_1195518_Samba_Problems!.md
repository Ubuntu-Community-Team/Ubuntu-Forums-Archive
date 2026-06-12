---
title: "Samba Problems!"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-23
I'm getting tired of these random problems.
Sigh.

Anyway,
I went to share a folder, and I got this:

Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
	No such file or directory
Error loading services.

I tried to remove and reinstall samba from Add/remove, and I get this....

E: samba: subprocess post-installation script returned error exit status 2
E: system-config-samba: dependency problems - leaving unconfigured


Help?

---

### Post by duanedesign on 2009-06-23
looks like your smb.conf is missing or messed up.

I'd recommend copying a fresh smb.conf from /usr/share/samba.

```
sudo cp /usr/share/samba/smb.conf  /etc/samba/smb.conf
```

---

### Post by Gp. on 2009-06-24
It has to do with something else...
like Dependency errors

---

### Post by bodhi.zazen on 2009-06-24
Open a terminal and try:

```
sudo apt-get update && sudo apt-get -y dist-upgrade

sudo apt-get install samba
```and if you get error messages, please post a little more detail (entire error message).

---

### Post by Gp. on 2009-06-24
Got this...
```
sudo apt-get update && apt-get -y dist-upgrade
[sudo] password for kyle: 
Hit http://mirror.internode.on.net jaunty Release.gpg
Get:1 http://mirror.internode.on.net jaunty/main Translation-en_AU [2734B]     
Ign http://mirror.internode.on.net jaunty/restricted Translation-en_AU         
Ign http://mirror.internode.on.net jaunty/universe Translation-en_AU           
Ign http://mirror.internode.on.net jaunty/multiverse Translation-en_AU         
Hit http://mirror.internode.on.net jaunty-updates Release.gpg                  
Ign http://mirror.internode.on.net jaunty-updates/main Translation-en_AU       
Ign http://mirror.internode.on.net jaunty-updates/restricted Translation-en_AU 
Ign http://mirror.internode.on.net jaunty-updates/universe Translation-en_AU   
Ign http://mirror.internode.on.net jaunty-updates/multiverse Translation-en_AU 
Hit http://mirror.internode.on.net jaunty-security Release.gpg                 
Ign http://mirror.internode.on.net jaunty-security/main Translation-en_AU      
Ign http://mirror.internode.on.net jaunty-security/restricted Translation-en_AU
Ign http://mirror.internode.on.net jaunty-security/universe Translation-en_AU  
Ign http://mirror.internode.on.net jaunty-security/multiverse Translation-en_AU
Hit http://mirror.internode.on.net jaunty Release                              
Hit http://mirror.internode.on.net jaunty-updates Release                      
Hit http://mirror.internode.on.net jaunty-security Release                     
Hit http://mirror.internode.on.net jaunty/main Packages                        
Hit http://mirror.internode.on.net jaunty/restricted Packages                  
Hit http://mirror.internode.on.net jaunty/main Sources                         
Hit http://mirror.internode.on.net jaunty/restricted Sources                   
Hit http://mirror.internode.on.net jaunty/universe Packages                    
Hit http://mirror.internode.on.net jaunty/universe Sources                     
Hit http://mirror.internode.on.net jaunty/multiverse Packages                  
Hit http://mirror.internode.on.net jaunty/multiverse Sources                   
Hit http://mirror.internode.on.net jaunty-updates/main Packages                
Hit http://mirror.internode.on.net jaunty-updates/restricted Packages          
Hit http://mirror.internode.on.net jaunty-updates/main Sources                 
Hit http://mirror.internode.on.net jaunty-updates/restricted Sources           
Hit http://mirror.internode.on.net jaunty-updates/universe Packages            
Hit http://mirror.internode.on.net jaunty-updates/universe Sources             
Hit http://mirror.internode.on.net jaunty-updates/multiverse Packages          
Hit http://mirror.internode.on.net jaunty-updates/multiverse Sources           
Hit http://mirror.internode.on.net jaunty-security/main Packages               
Hit http://mirror.internode.on.net jaunty-security/restricted Packages         
Hit http://mirror.internode.on.net jaunty-security/main Sources                
Hit http://mirror.internode.on.net jaunty-security/restricted Sources          
Hit http://mirror.internode.on.net jaunty-security/universe Packages           
Hit http://mirror.internode.on.net jaunty-security/universe Sources            
Hit http://mirror.internode.on.net jaunty-security/multiverse Packages         
Hit http://mirror.internode.on.net jaunty-security/multiverse Sources          
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_AU              
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_AU              
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_AU                     
Hit http://wine.budgetdedicated.com jaunty Release                             
Hit http://archive.canonical.com jaunty Release                                
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_AU                
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                     
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://wine.budgetdedicated.com jaunty/main Packages                       
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_AU            
Hit http://packages.medibuntu.org jaunty Release                               
Ign http://archive.canonical.com jaunty/partner Packages                       
Hit http://ppa.launchpad.net jaunty Release                                    
Hit http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://packages.medibuntu.org jaunty/free Packages                         
Ign http://archive.canonical.com jaunty/partner Sources                        
Ign http://www.pvv.ntnu.no ./ Release.gpg                            
Ign http://www.pvv.ntnu.no ./ Translation-en_AU                                
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://archive.canonical.com jaunty/partner Packages                       
Get:2 http://www.pvv.ntnu.no ./ Release [712B]                       
Hit http://ppa.launchpad.net jaunty/main Packages                        
Hit http://ppa.launchpad.net jaunty/main Sources                     
Hit http://archive.canonical.com jaunty/partner Sources              
Hit http://www.pvv.ntnu.no ./ Packages         
Hit http://www.pvv.ntnu.no ./ Sources
Fetched 2735B in 3s (836B/s)
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

Yes, I did sudo, and no other package managers appear open, so wth?

---

### Post by bodhi.zazen on 2009-06-24
OOps, add the sudo as suggested below.

---

### Post by fooman on 2009-06-24
> **bodhi.zazen said:**
> Open a terminal and try:

```
sudo apt-get update && apt-get -y dist-upgrade

sudo apt-get install samba
```and if you get error messages, please post a little more detail (entire error message).

there is a missing "sudo" in the first command...should be:

```
sudo apt-get update && sudo apt-get -y dist-upgrade
```

then try the second one:

```
sudo apt-get install samba
```

---

### Post by Gp. on 2009-06-24
```
sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-tdb libuser1 python-libuser
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba-common
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools
The following NEW packages will be installed:
  samba samba-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9538kB of archives.
After this operation, 26.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba-common.
(Reading database ... 181795 files and directories currently installed.)
Unpacking samba-common (from .../samba-common_2%3a3.3.2-1ubuntu3_amd64.deb) ...
Selecting previously deselected package samba.
Unpacking samba (from .../samba_2%3a3.3.2-1ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up samba-common (2:3.3.2-1ubuntu3) ...
Not replacing deleted config file /etc/samba/smb.conf
Install/upgrade will fail. To recover, please try:
  sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
  sudo dpkg --configure -a
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.3.2-1ubuntu3); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 samba-common
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

More errors! yay!
-_-

---

### Post by bodhi.zazen on 2009-06-24
The error message also suggests the solution :

[quote]Not replacing deleted config file /etc/samba/smb.conf[FONT=monospace]
[/FONT]Install/upgrade will fail. To recover, please try:[FONT=monospace]
[/FONT] sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf[FONT=monospace]
[/FONT] sudo dpkg --configure -a[/code]

So try opening a terminal and :

```
sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf[FONT=monospace]
[/FONT] sudo dpkg --configure -a
```

---

### Post by Gp. on 2009-06-24
Okay, that fixed that problem, but when I right click a folder and try to share I get this error:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.

---

### Post by LazarusHC on 2009-06-29
> **Gp. said:**
> Okay, that fixed that problem, but when I right click a folder and try to share I get this error:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.

I'm having this exact same problem, and it also happened right after I ran "sudo dpkg --configure -a"  I've been searching for hours to find a solution.

---

### Post by Gp. on 2009-06-29
Well I'm back on windows.
Windows 7 RC infact, and it's great.
Not saying Ubuntu isn't great, but it's these annoying problems, that if you arn't einstein are a pain, and prevents me from doing what I need to do.
I'm redoing my entire system so perhaps I'll reinstall Ubuntu later, but probably not with 9.04 unless I can figure out all the issues that occur.

---

### Post by LazarusHC on 2009-06-30
> **Gp. said:**
> Well I'm back on windows.
Windows 7 RC infact, and it's great.
Not saying Ubuntu isn't great, but it's these annoying problems, that if you arn't einstein are a pain, and prevents me from doing what I need to do.
I'm redoing my entire system so perhaps I'll reinstall Ubuntu later, but probably not with 9.04 unless I can figure out all the issues that occur.

Well, that's the beauty of choice.  All the power to you, and I don't begrudge you for choosing it.  I, however, don't want to spend enough money to buy a months worth of food on an operating system, when I have this one for free (and legally).  

So, if anyone has any ideas, I would be thankful. :)

---

### Post by bodhi.zazen on 2009-06-30
Can you provide more details ?

How did you install samba ? did you log off and back on ? Is this error on the server or client ? firewall ?

What directory are you trying to share ? you user must have permission to share the directory. You should not share your $HOME directroy, rather share a folder within $HOME, say /home/user_name/share or what have you.

---

### Post by LazarusHC on 2009-06-30
> **bodhi.zazen said:**
> Can you provide more details ?

How did you install samba ? did you log off and back on ? Is this error on the server or client ? firewall ?

What directory are you trying to share ? you user must have permission to share the directory. You should not share your $HOME directroy, rather share a folder within $HOME, say /home/user_name/share or what have you.

Well, I installed and reinstalled every package related to samba that I could find in an attempt to solve another problem I had (I couldn't access any share already on the network).  I couldn't tell you what order I did it in. 

I don't really know samba networking that well, but this error is on the server side.  It happens when I try to share anything at all (I know I need the proper permissions).  Right click, sharing options, then share this folder, create share.  I get this error: "'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter."

---

### Post by bodhi.zazen on 2009-06-30
Sounds like a bug to me, I advise you file a bug report on Launchpad.

As a work around, some people have reported starting nautilus as root allow you to share the directories.

```
gksu nautilus
```

Other then that, my only other thought is that you manually go through samba and the configuration files , including manually adding your user as a samba user.

[https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html)

Work through that page step-by-step.

---

### Post by LazarusHC on 2009-06-30
> **bodhi.zazen said:**
> Sounds like a bug to me, I advise you file a bug report on Launchpad.

As a work around, some people have reported starting nautilus as root allow you to share the directories.

```
gksu nautilus
```

Other then that, my only other thought is that you manually go through samba and the configuration files , including manually adding your user as a samba user.

[https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html)

Work through that page step-by-step.

I've tried that workaround, and I still got the same error.  

Before I file it as a bug, I want to make sure I can easily replicate it (in case it was just something I messed up myself).  Which means reinstalling everything from scratch.  In the mean time, I think I may just set it up manually, so I can at least use it.  

Thanks for the help!

---

