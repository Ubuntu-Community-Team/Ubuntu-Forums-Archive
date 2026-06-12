---
title: "upgraded to 9.04 and now problems :D"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by zeb2cool2b on 2009-05-01
hi guys and gals

ok im new to this but iv tryed to put as much info in as pos. sorry in advance tor terrible spelling and grammer.

ok so i thought i had ubuntu vertion 9.04 or 9.10 though yesterday (havent used ubuntu for weeks) the update program sayed click here to upgrade to 9.04 so i did i had fire fox and 3rd party aMSN open it took ages to update and there where a couple error messages i ignored them cuz i have 64bit amd (i hate it) and i though it was just something not compatable. the update finished and there was a final error say not all parts could be installed. i restarted and there was a new load screen and log in very sexy lookin :P. after log in next to the vol and battry indicators a red cir with white line though it and it was saying that an update for aMSN could not be updaded. then went to add remove to get rid of aMSN and got this message "major failer in managment system......... cheak file /ect/apt/sources.list reload software using "sudo apt-get update" and "sudo apt-get install -f"

so sudo apt-get update gave me this
zeb2cool2b@ubuntu:~$ sudo apt-get update
```
[sudo] password for zeb2cool2b: 
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid Release.gpg
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid Release
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Packages
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Packages
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Packages
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Packages
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://archive.canonical.com intrepid Release.gpg                          
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://packages.medibuntu.org hardy Release                                
Hit http://archive.canonical.com intrepid Release                              
Hit http://security.ubuntu.com intrepid-security Release.gpg         
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
Ign http://archive.canonical.com intrepid/partner Packages                     
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://security.ubuntu.com intrepid-security Release             
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg          
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg      
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US     
Ign http://archive.canonical.com intrepid/partner Sources                      
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Hit http://packages.medibuntu.org hardy/free Sources                           
Hit http://packages.medibuntu.org hardy/non-free Sources                       
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release                      
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://security.ubuntu.com intrepid-security/restricted Packages 
Hit http://security.ubuntu.com intrepid-security/main Sources        
Hit http://security.ubuntu.com intrepid-security/restricted Sources  
Hit http://security.ubuntu.com intrepid-security/universe Packages   
Hit http://archive.canonical.com intrepid/partner Sources            
Hit http://us.archive.ubuntu.com intrepid-backports Release          
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-backports/main Sources
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-backports/universe Sources
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Sources
W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)/dists/intrepid/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)/dists/intrepid/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
```and sudo apt-get install -f gave me 
```
zeb2cool2b@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  amsn
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1004kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128558 files and directories currently installed.)
Removing amsn ...
dpkg: error processing amsn (--remove):
 cannot remove `/usr/bin/amsn-remote-CLI': Stale NFS file handle
Errors were encountered while processing:
 amsn
E: Sub-process /usr/bin/dpkg returned an error code (1)
zeb2cool2b@ubuntu:~$ 

```i did befor this enter 
```
sudo apt-get autoremove amsn
```it removed some files but there where errors i didnt copy.

to to recap i just want amsn gone and my add remove to work again. sorry if this dont make sence.

martyn

---

### Post by Temposs on 2009-05-02
Try to go to System->Administration->Synaptic Package Manager.

Click the "Edit" menu, then choose "Fix Broken Packages".  See if it will repair what's wrong with amsn.

---

### Post by llamabr on 2009-05-02
Man, your sources.list file is a mess.  Take out all that cdrom crap, and clean it up.  This may be an error caused by some inconsistency in there.

Also, just try:

```
sudo apt-get autoremove
```

then

```
sudo apt-get remove amsn
```

But only after you clean that mess, and then do 
```
sudo apt-get update
```

---

### Post by zeb2cool2b on 2009-05-02
> **llamabr said:**
> Man, your sources.list file is a mess.  Take out all that cdrom crap, and clean it up.  This may be an error caused by some inconsistency in there.

Also, just try:

```
sudo apt-get autoremove
```then

```
sudo apt-get remove amsn
```But only after you clean that mess, and then do 
```
sudo apt-get update
```

i have know clew where the sources.list file is or where or what the cdrom stuff is. sorry to be a bit clueless :D
tryed the first 2 codes and got this as a responce
```
zeb2cool2b@ubuntu:~$ sudo apt-get autoremove
[sudo] password for zeb2cool2b: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  amsn
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1004kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128558 files and directories currently installed.)
Removing amsn ...
dpkg: error processing amsn (--remove):
 cannot remove `/usr/bin/amsn-remote-CLI': Stale NFS file handle
Errors were encountered while processing:
 amsn
E: Sub-process /usr/bin/dpkg returned an error code (1)
zeb2cool2b@ubuntu:~$ sudo apt-get remove amsn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  amsn
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1004kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128558 files and directories currently installed.)
Removing amsn ...
dpkg: error processing amsn (--remove):
 cannot remove `/usr/bin/amsn-remote-CLI': Stale NFS file handle
Errors were encountered while processing:
 amsn
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

