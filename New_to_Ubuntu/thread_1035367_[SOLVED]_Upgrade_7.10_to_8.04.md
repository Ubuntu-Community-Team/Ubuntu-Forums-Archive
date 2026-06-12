---
title: "[SOLVED] Upgrade 7.10 to 8.04"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-01-09
I just finished doing an upgrade from 7.10 to 8.04 using the option available thru the Update Manager. When I looked at the 'Third Party Software' in 'Sys>Admin>Software Sources' they are all still 'Gutsy' instead of Hardy ??? How do I upgrade these? Thanks

---

### Post by Michael.Godawski on 2009-01-09
hi,

can you please post your sources.list:

```
cat /etc/apt/sources.list
```

---

### Post by avtolle on 2009-01-09
Which third party software sources are still there? If medibuntu, you will need to go to the medibuntu site and download the Hardy sources (and reinstall the key).  See [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories) for this.

---

### Post by CoCoKnots on 2009-01-09
> **Michael.Godawski said:**
> hi,

can you please post your sources.list:

```
cat /etc/apt/sources.list
```

This is a little confusing... I see both Gutsy & Hardy referenced here:

cocoknots@cocoknots-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
cocoknots@cocoknots-laptop:~$

---

### Post by Bachstelze on 2009-01-09
The "gutsy" lines have a # at the beginning, which means they are commented out (i.e. "disabled") and not actually used by the package manager. Try to do this and tell us what it gives you:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by theozzlives on 2009-01-09
Looks like all the Gutsy ones are commented out with a #, I wouldn't worry about it.

---

### Post by CoCoKnots on 2009-01-09
> **Michael.Godawski said:**
> hi,

can you please post your sources.list:

```
cat /etc/apt/sources.list
```

> **avtolle said:**
> Which third party software sources are still there? If medibuntu, you will need to go to the medibuntu site and download the Hardy sources (and reinstall the key).  See [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories) for this.

Do I need to do the Kryring update as well ?

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by namdung on 2009-01-09
Your sources file look fine. Even though the Gutsy sources are there it's not selected (it's commented). U may safely remove the Gutsy sources from the list.

Pls post output of the following in terminal:
```
sudo apt-get update
```

---

### Post by avtolle on 2009-01-09
> **CoCoKnots said:**
> Do I need to do the Kryring update as well ?

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Yes, AFAIK.

---

### Post by CoCoKnots on 2009-01-09
> **HymnToLife said:**
> The "gutsy" lines have a # at the beginning, which means they are commented out (i.e. "disabled") and not actually used by the package manager. Try to do this and tell us what it gives you:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

cocoknots@cocoknots-laptop:~$ sudo apt-get update
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US           
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                        
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [6322B]                        
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7914B]                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Fetched 26.1kB in 5s (4360B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
cocoknots@cocoknots-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libavcodec1d libavformat1d libavutil1d libpostproc1d
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2279kB of archives.
After this operation, 516kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libavutil1d libavcodec1d libavformat1d libpostproc1d
Install these packages without verification [y/N]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free libavutil1d 3:0.cvs20070307-5ubuntu7.1+medibuntu1 [40.2kB]
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free libavcodec1d 3:0.cvs20070307-5ubuntu7.1+medibuntu1 [1875kB]
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free libavformat1d 3:0.cvs20070307-5ubuntu7.1+medibuntu1 [288kB]
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free libpostproc1d 3:0.cvs20070307-5ubuntu7.1+medibuntu1 [74.9kB]
Fetched 2279kB in 5s (397kB/s)        
(Reading database ... 107923 files and directories currently installed.)
Preparing to replace libavutil1d 3:0.cvs20070307-5ubuntu7.1 (using .../libavutil1d_3%3a0.cvs20070307-5ubuntu7.1+medibuntu1_i386.deb) ...
Unpacking replacement libavutil1d ...
Preparing to replace libavcodec1d 3:0.cvs20070307-5ubuntu7.1 (using .../libavcodec1d_3%3a0.cvs20070307-5ubuntu7.1+medibuntu1_i386.deb) ...
Unpacking replacement libavcodec1d ...
Preparing to replace libavformat1d 3:0.cvs20070307-5ubuntu7.1 (using .../libavformat1d_3%3a0.cvs20070307-5ubuntu7.1+medibuntu1_i386.deb) ...
Unpacking replacement libavformat1d ...
Preparing to replace libpostproc1d 3:0.cvs20070307-5ubuntu7.1 (using .../libpostproc1d_3%3a0.cvs20070307-5ubuntu7.1+medibuntu1_i386.deb) ...
Unpacking replacement libpostproc1d ...
Setting up libavutil1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) ...

Setting up libavcodec1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) ...

Setting up libavformat1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) ...

Setting up libpostproc1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
cocoknots@cocoknots-laptop:~$

---

### Post by CoCoKnots on 2009-01-09
> **namdung said:**
> Your sources file look fine. Even though the Gutsy sources are there it's not selected (it's commented). U may safely remove the Gutsy sources from the list.

Pls post output of the following in terminal:
```
sudo apt-get update
```

This is looking better all the time...

cocoknots@cocoknots-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 198B in 2s (98B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
cocoknots@cocoknots-laptop:~$

---

### Post by Michael.Godawski on 2009-01-09
for the medibuntu authentication run:

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by CoCoKnots on 2009-01-09
> **Michael.Godawski said:**
> for the medibuntu authentication run:

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

OK... Ran it.  Thanks Michael. I'm getting a lot of things running in my terminal page. I's difficult to keep track of what it's doing. What's next ?

---

### Post by CoCoKnots on 2009-01-09
> **CoCoKnots said:**
> OK... Ran it.  Thanks Michael. I'm getting a lot of things running in my terminal page. I's difficult to keep track of what it's doing. What's next ?

How does this look ?

cocoknots@cocoknots-laptop:~$  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Reading package lists... Done
cocoknots@cocoknots-laptop:~$

---

### Post by avtolle on 2009-01-09
Looks like you're good to go.

---

### Post by namdung on 2009-01-09
Seems like issue with ur *medibuntu* package. Remove it or fix it like suggested earlier. Else all fine.

---

### Post by CoCoKnots on 2009-01-09
Thanks Everyone... I appreciate the help. This is what I have on my Software Source screen... Still a lot of 'Gutsy' stuff. Is this OK ?

---

### Post by CoCoKnots on 2009-01-09
> **namdung said:**
> Seems like issue with ur *medibuntu* package. Remove it or fix it like suggested earlier. Else all fine.

Do I need to edit the entire line or just make sure they are un-checked in the software source page ?

---

### Post by thegreenblob on 2009-01-09
> **CoCoKnots said:**
> Thanks Everyone... I appreciate the help. This is what I have on my Software Source screen... Still a lot of 'Gutsy' stuff. Is this OK ?

All the gutsy stuff is disabled in that screenshot, so you should be fine.

---

### Post by avtolle on 2009-01-09
As has been stated above, you should be fine. If you want to eliminate the lines, rather than commenting them out, you may certainly do so either by manually editing your sources.list and deleting them, or by deleting the Gutsy references from software sources. Otherwise, all looks and acts as it should.

---

