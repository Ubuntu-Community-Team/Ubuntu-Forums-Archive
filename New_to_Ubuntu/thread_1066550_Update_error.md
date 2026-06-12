---
title: "Update error"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Mr.Glenmore on 2009-02-11
Hi all,
I keep getting this in the Synaptic Package Manager:


E: acpid: subprocess post-installation script returned error exit status 1
E: ntp: subprocess post-installation script returned error exit status 1


I tried to find a solution.Please,Can someone helpme to fix this??
Thanks for your help

---

### Post by jbrown96 on 2009-02-11
Try running the updates in a terminal (Apps===>Accessories===>Terminal). It will give you more output and possibly a solution.
```
sudo apt-get update && sudo apt-get upgrade
```

Post back the output if it still doesn't work and you don't know what to do.

---

### Post by Mr.Glenmore on 2009-02-11
Here comes the output:


horstscheffler@horstscheffler-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for horstscheffler: 
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_AU                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Translation-en_AU                  
Get:2 [http://ftp.debian.org](http://ftp.debian.org) etch Release.gpg [386B]                            
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Translation-en_AU                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_AU               
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Translation-en_AU  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Translation-en_AU    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Translation-en_AU  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Get:4 [http://ftp.debian.org](http://ftp.debian.org) etch Release [58.2kB]                              
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Packages                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Sources                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Packages             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 695B in 2s (264B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils initramfs-tools initscripts libbind9-30 libisccc30
  libisccfg30 linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic ssl-cert
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up acpid (1.0.4-5ubuntu9.1) ...
 * Stopping Hardware abstraction layer hald                              [ OK ] 
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ntp (1:4.2.4p4+dfsg-3ubuntu2.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing ntp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
 ntp
E: Sub-process /usr/bin/dpkg returned an error code (1)
horstscheffler@horstscheffler-desktop:~$ 

Thanks

---

### Post by jbrown96 on 2009-02-11
I noticed that you are using PPA and Debian archives. I'm not sure about which packages this repositories contain, but I would be very careful mixing them. If you added them to download some new packages, I would comment them out and just try updates with them when you know there are no other updates to run.

Again, forcing these updates with those repositories could be dangerous. 
```
sudo apt-get -f install
``` should clear up those problems.

---

### Post by johnjohn2 on 2009-02-11
The above command is what i used as i had the same problems with intrepid, i also believe something to have gone wrong   with the keys, PPA as i still get that same eror it is like they are not signed.

---

### Post by Mr.Glenmore on 2009-02-11
Thanks johnjohn2,
I will remember that.

---

