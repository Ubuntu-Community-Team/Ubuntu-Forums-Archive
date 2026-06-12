---
title: "Synaptic Package Manager Missing in Main Menu"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by dragonmojo on 2008-12-26
Something happened where I no longer have SPM in the Main Menu under SYSTEM>Administration. I tried editing the Main Menu, checked the box for SPM, but it unchecks itself. Same with Software Source.

I'm a noob.

---

### Post by ELF_O8 on 2008-12-26
You could try manually removing and reinstalling Synaptic through apt-get.

```
sudo apt-get remove synaptic
```

Reboot the system then,

```
sudo apt-get install synaptic
```

and reboot again.

---

### Post by dragonmojo on 2008-12-27
Hi Elf,
I removed it, rebooted, then tried installing and get this:

$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate

I have a fairly new Dell Mini9 running an Ubuntu Hardy remix. Any suggestions appreciated, thx.

---

### Post by ELF_O8 on 2008-12-27
That's really very odd. Because when I do it I get this output ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
The following packages were automatically installed and are no longer required:
  libavifile-0.7c2 python-xlib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Try to fetch another manager, Adept (the KDE version of Synaptic, but it'll work just fine on GNOME)
```
sudo apt-get install adept
```

Reboot, and see if you can do anything from there.

---

### Post by dragonmojo on 2008-12-27
$ sudo apt-get install adept
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adept


I wonder what I am doing wrong?

---

### Post by Perfect Storm on 2008-12-27
Lets see your sources list;

```
cat /etc/apt/sources.list
```

---

### Post by dragonmojo on 2008-12-27
Hi Elf,


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free 


Appreciate the help! Thx.

---

### Post by ELF_O8 on 2008-12-27
Could you post the complete output?

---

### Post by dragonmojo on 2008-12-27
Hi Elf,
This is all that is returned:



$ cat /etc/apt/sources.list
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free 
$

---

### Post by Perfect Storm on 2008-12-27
Seems alot of is missing, have you been messing with the sourcelist?

It should look like this (this is for intrepid);

```
# newer versions of the distribution.                               

deb http://dk.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties                 

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://dk.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted                                                               
deb-src http://dk.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties         

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu                                                             
## team. Also, please note that software in universe WILL NOT receive any                                                               
## review or updates from the Ubuntu security team.                 
deb http://dk.archive.ubuntu.com/ubuntu/ intrepid universe          
deb http://dk.archive.ubuntu.com/ubuntu/ intrepid-updates universe  

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu                                                             
## team, and may not be under a free licence. Please satisfy yourself as to                                                             
## your rights to use the software. Also, please note that software in                                                                  
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.                                                   
deb http://dk.archive.ubuntu.com/ubuntu/ intrepid multiverse        
deb http://dk.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'                                                               
## repository.                                                      
## N.B. software from this repository may not have been tested as   
## extensively as that contained in the main release, although it includes                                                              
## newer versions of some applications which may provide useful features.                                                               
## Also, please note that software in backports WILL NOT receive any review                                                             
## or updates from the Ubuntu security team.                        
deb http://dk.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse                                         
deb-src http://dk.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse                                     

## Uncomment the following two lines to add software from Canonical's                                                                   
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu                                                               
## users.                                                           
deb http://archive.canonical.com/ubuntu intrepid partner            
deb-src http://archive.canonical.com/ubuntu intrepid partner        

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://dk.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

---

### Post by ELF_O8 on 2008-12-27
He DID mention that the Source Manager had disappeared.
But, it seems as though your whole sources.list has been trimmed into oblivion,

---

### Post by dragonmojo on 2008-12-27
I'm very new to Linux/Ubuntu (living in a Windows world), and would not have known to get into the source list. Is it possibly something that was tweaked to run on the Dell Mini9 (MiniOS)? Nice to know there are support groups like this in the Linux community!

Hmm, what now re: the Synaptic Package Manager? Many thx.

---

### Post by ELF_O8 on 2008-12-27
Well, the reason you can't get it is because you don't have the proper sources.
You could try [these instructions]("http://ubuntuforums.org/showthread.php?t=949488&highlight=repair+sources.list").
It seems to have helped this person who had the same problem, though they had a regular sources.list. You could also try to replace your sources.list with the output posted there; worth a shot.

---

### Post by plucky on 2008-12-27
Have you got an internet connection?

Please post output from a terminal of ```
sudo apt-get update
```


Good Luck

---

### Post by dragonmojo on 2008-12-27
I tried pasting the code as suggested earlier (to sources.list), and rebooted, but did not seem to work. Here you go:

$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                                                           
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg [191B]                                                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                                                  
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                                                             
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                                                                      
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release [1016B]                                                                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                                                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                                                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages            
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Fetched 194B in 2min22s (1B/s)
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2008-12-27
I just copied your sources.list and replaced mine with it and did a "sudo apt-get update" and it went through without a problem.

Also your updated sources.list seems to have extra repositories.

404 errors usually means you cannot connect to the servers,but when I click on the link,the server opens.Could be a DNS problem.

What are you using as a nameserver? Post ```
cat /etc/resolv.conf
```
Can you access the servers in Firefox?
If you copy ```
91.189.88.46
``` into the address bar of firefox,does it take you to the server?
What is your internet access setup i.e wireless,wired,modem etc.


Good Luck

---

### Post by dragonmojo on 2008-12-27
Hi Plucky,

$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4739
#
### END INFO

search hsd1.ca.comcast.net.


nameserver 68.87.76.178
nameserver 68.87.78.130
nameserver 68.87.69.146

$ 




I also used the address you provided, which took me to the ubuntu archive page.

Index of /
[ICO]	Name	Last modified	Size
[DIR]	ubuntu/	27-Dec-2008 21:59 	- 	 
Apache/2.2.8 (Ubuntu) Server at archive.ubuntu.com Port 80


I am running wireless with my Mini9 using 802.11b, Linksys router, Comcast cable, WEP 128bit. I wonder why I am not hitting those servers like you are able to? Thx for your help!

---

### Post by plucky on 2008-12-27
> I also used the address you provided, which took me to the ubuntu archive page.

Index of /
[ICO] Name Last modified Size
[DIR] ubuntu/ 27-Dec-2008 21:59 -
Apache/2.2.8 (Ubuntu) Server at archive.ubuntu.com Port 80


That probably means that it is a DNS problem i.e your nameserver is not translating the "archive.ubuntu.com" into the correct numbers.

What happens if you put "www.archive.ubuntu.com" into the address bar of firefox? (without the "quotes")


My /etc/resolv.conf has only one nameserver and is the address of my router.


Try ```
gksudo gedit /etc/resolv.conf
``` and put a # before **search hsd1.ca.comcast.net.** so it looks like ```
### BEGIN INFO
#
# Modified_by: NetworkManager
# Process: /usr/bin/NetworkManager
# Process_id: 4739
#
### END INFO

#search hsd1.ca.comcast.net.


nameserver 68.87.76.178
nameserver 68.87.78.130
nameserver 68.87.69.146

```

and then try ```
sudo apt-get update
```

Good Luck

---

### Post by dragonmojo on 2008-12-27
I get the same thing:

Index of /
[ICO]	Name	Last modified	Size
[DIR]	ubuntu/	27-Dec-2008 22:54 	- 	 
Apache/2.2.8 (Ubuntu) Server at [www.archive.ubuntu.com](www.archive.ubuntu.com) Port 80


It still doesn't look good:

$ gksudo gedit /etc/resolv.conf
$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                                                      
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg [191B]                                                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                                                  
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages                                                          
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                                                                      
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release [1016B]                                                                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                                                                    
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages                                                          
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                           
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                                
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages                          
  404 Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                            
  404 Not Found
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Fetched 194B in 2s (74B/s)
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2008-12-27
Now try it again,but put a # in front of two of the name servers
```
### BEGIN INFO
#
# Modified_by: NetworkManager
# Process: /usr/bin/NetworkManager
# Process_id: 4739
#
### END INFO

#search hsd1.ca.comcast.net.


nameserver 68.87.76.178
#nameserver 68.87.78.130
#nameserver 68.87.69.146
```

If that doesn't work,move the # from one and put it on the first one
```
### BEGIN INFO
#
# Modified_by: NetworkManager
# Process: /usr/bin/NetworkManager
# Process_id: 4739
#
### END INFO

#search hsd1.ca.comcast.net.


#nameserver 68.87.76.178
nameserver 68.87.78.130
#nameserver 68.87.69.146
```

If you see what I mean.And then the final one.
If none of that works then I am out of ideas as to what is causing this

---

### Post by dragonmojo on 2008-12-27
Plucky, each server did the same thing. Thx again for your, and everyone else's help (if anyone has further suggestions, pls let me know). At least I have an idea of what is going on by the suggestions offered (e.g. the code works, but not on my Mini9). I'll keep playing around. Again, I am open for further suggestions. Thx!!

---

### Post by plucky on 2008-12-27
Did you install the software on this Dell or is it what was shipped?

Is it a full version of Hardy? What is a Hardy remix?

It seems strange that both Synaptic and Software Sources don't seem to be installed.

Good Luck

---

### Post by dragonmojo on 2008-12-27
Both were available until recently, so I am not sure why they disappeared.

Dell has a version of Hardy Heron for the Mini9 because it uses the Intel Atom processor. The i386 packages won't work and has to be converted to lpia. At least that is what I learned from these forums.

Something else I believe I had before, but cannot do now. Some windows require me to press the Unlock button. Now it gives me a message saying I could not authenticate. Wonder if this is all related??

---

### Post by ELF_O8 on 2008-12-27
What do you mean by > Some windows require me to press the Unlock button?

---

### Post by dragonmojo on 2008-12-27
System>Administration>Services

System>Administration>Users and Groups

When I invoke these, the window comes up but I can't do anything. There is a button labeled UNLOCK... when I press it, there is a pause and then the message that it "could not authenticate".

Thx Elf!

---

### Post by ELF_O8 on 2008-12-28
To get past this use the command
```
gksudo nautilus
```
This gives you root control of the GUI. BE CAREFUL, you can literally do anything to files and folders now; no questions asked, so, be careful what you do and restart immediately after you finish what you need to do.

---

### Post by dragonmojo on 2008-12-28
Thanks Elf,
This will be helpful once I learn more about linux/ubuntu. Right now I'm likely to get into too much trouble. As it stands, I may have to see if I can get this system back to the way it was when brand new. Cheers.

---

### Post by paulbort on 2009-03-27
OK, I just figured this one out on my 8.04 install, should be the same for other versions. I'm using Likewise-Open, so the account I log in with every day is not the user account I created during the OS install.

I ran in to the same problem reported at the beginning of the thread: Synaptic missing from menu; menu editor clears the checkbox for it as soon as I check it. I also noticed that Synaptic and some other programs were listed in the menu editor in italics, and any program in italics could not be checked either.

The problem is that these are administrative programs, and the system will not give access to them to most users. Only users who are members of the "adm" group can have these programs shown on their menus.

I tried to use the "Users and Groups" program to fix this, but it doesn't show Likewise Active Directory users. (If you're having this problem and not using Likewise-Open, then you can probably fix it in Users and Groups.)

To fix it for a Likewise user, you have to add that user to the group manually. I edited the /etc/group file, and added a comma, my domain, a backslash, and my user name to the end of the the line that starts with "adm:". So now it looks like this:

adm:x:4:paul,MYDOMAIN\domainuser

The next time I logged in after that, Synaptic (and the others) were back on my menu.

I hope this helps.

Paul

---

