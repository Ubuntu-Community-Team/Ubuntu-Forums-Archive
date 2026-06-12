---
title: "cannot install deb packages"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by yoshiki2 on 2009-10-17
I was installing and unistalling esktops, programs, playing with sinaptics.. (trying to get used to the OS) but now i cannot instail deb packages.... I'm pretty sure i messed up something...
what do i need to reinstall in order to fix this.. thx.

---

### Post by philinux on 2009-10-17
Open a terminal.

```
sudo apt-get update

then

sudo apt-get upgrade


```

Post back with any errors it spits out.

---

### Post by yoshiki2 on 2009-10-17
Not so sure about what does this mean:




/ubuntu Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/jaunty Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Translation-en_US     
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Release    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/maindeb-src Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [57.9kB]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/jaunty Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/maindeb-src Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/jaunty Packages                         
Hit [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Packages              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/maindeb-src Packages             
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu Packages
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/jaunty Packages
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [195kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2589B]                                                                               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [55.4kB]                                                                                     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [623B]                                                                                 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [80.4kB]                                                                                
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [22.3kB]                                                                                
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [8128B]                                                                              
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]                                                                               
Fetched 426kB in 13s (30.6kB/s)                                                                                                                             
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/jaunty/maindeb-src/binary-i386/Packages](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/jaunty/maindeb-src/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/jaunty/http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/binary-i386/Packages](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/jaunty/http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/jaunty/jaunty/binary-i386/Packages](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/jaunty/jaunty/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
alfredo@alfredo-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 691kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main tzdata 2009n-0ubuntu0.9.04.1 [691kB]
Fetched 691kB in 27s (24.7kB/s)                                                                                                                             
Preconfiguring packages ...
(Reading database ... 116921 files and directories currently installed.)
Preparing to replace tzdata 2009n-0ubuntu0.9.04 (using .../tzdata_2009n-0ubuntu0.9.04.1_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2009n-0ubuntu0.9.04.1) ...

Current default timezone: 'America/New_York'
Local time is now:      Sat Oct 17 16:54:14 EDT 2009.
Universal Time is now:  Sat Oct 17 20:54:14 UTC 2009.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


localepurge: Disk space freed in /usr/share/locale: 540K




any ideas??

---

### Post by yoshiki2 on 2009-10-17
deb files are working now

---

