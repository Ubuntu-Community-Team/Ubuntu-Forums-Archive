---
title: "Update Manager Respository Indexes"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by jrox717 on 2009-04-03
For about a week now the update manager on Ubuntu 8.10 has had a yellow warning sign as an icon on the panel. When I click on it it tells me that my system is up-to-date, but when I click "check" it says that it could not download all repository indexes:

> The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.debain.org/dists/stable/updates/main/binary-i386/Packages.gz](http://security.debain.org/dists/stable/updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://non-us.debain.org/debain-non-US/dists/stable/non-US/main/binary-i386/Packages.gz](http://non-us.debain.org/debain-non-US/dists/stable/non-US/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.debain.org/debain/dists/sid/main/binary-i386/Packages.gz](http://ftp.debain.org/debain/dists/sid/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.debain.org/dists/stable/updates/contrib/binary-i386/Packages.gz](http://security.debain.org/dists/stable/updates/contrib/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://non-us.debain.org/debain-non-US/dists/stable/non-US/contrib/binary-i386/Packages.gz](http://non-us.debain.org/debain-non-US/dists/stable/non-US/contrib/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ftp.debain.org/debain/dists/sid/contrib/binary-i386/Packages.gz](http://ftp.debain.org/debain/dists/sid/contrib/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

the output of cat /etc/apt/sources.list:

> # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ftp.debain.org/debain/](http://ftp.debain.org/debain/) sid main contrib
deb [http://non-us.debain.org/debain-non-US](http://non-us.debain.org/debain-non-US) stable/non-US main contrib
deb [http://security.debain.org](http://security.debain.org) stable/updates main contrib



I'm not sure what to do... any help? Thank you!

---

### Post by kestrel1 on 2009-04-03
What happens if you type```
sudo apt-get update
```in a terminal.

---

### Post by taurus on 2009-04-03
Edit /etc/apt/sources.list and remove the last three repos or put a # in front of them to comment them out.

```

**[COLOR="Blue"]#[/COLOR]**deb http://ftp.debain.org/debain/ sid main contrib
**[COLOR="Blue"]#[/COLOR]**deb http://non-us.debain.org/debain-non-US stable/non-US main contrib
**[COLOR="Blue"]#[/COLOR]**deb http://security.debain.org stable/updates main contrib 

```
Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ajgreeny on 2009-04-03
Much simpler than all that.  You have a misspelling of the word **debian**, which you spelled debain, though I'm not too sure about adding debian repos to a ubuntu system.  Are you sure you need them?

---

### Post by kestrel1 on 2009-04-03
Well spotted ajgreeny. Missed that one. :lolflag:

---

### Post by jrox717 on 2009-04-03
> Much simpler than all that. You have a misspelling of the word debian, which you spelled debain, though I'm not too sure about adding debian repos to a ubuntu system. Are you sure you need them? 

Ok, I changed "debain" to "debian." Thank you for catching that! I am very confused though because I didn't change the spelling of any of those links since I installed Ubuntu... in any case now I run into some additional problems. When I run apt-get update, I get:

> Err [http://non-us.debian.org](http://non-us.debian.org) stable/non-US Release.gpg
  Could not resolve 'non-us.debian.org'
Err [http://non-us.debian.org](http://non-us.debian.org) stable/non-US/main Translation-en_US
  Could not resolve 'non-us.debian.org'
Err [http://non-us.debian.org](http://non-us.debian.org) stable/non-US/contrib Translation-en_US
  Could not resolve 'non-us.debian.org'
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Get:1 [http://ftp.debian.org](http://ftp.debian.org) sid Release.gpg [197B]                             
Ign [http://ftp.debian.org](http://ftp.debian.org) sid/main Translation-en_US                           
Get:2 [http://security.debian.org](http://security.debian.org) stable/updates Release.gpg [197B]             
Ign [http://security.debian.org](http://security.debian.org) stable/updates/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources  
Ign [http://security.debian.org](http://security.debian.org) stable/updates/contrib Translation-en_US
Ign [http://ftp.debian.org](http://ftp.debian.org) sid/contrib Translation-en_US              
Get:3 [http://security.debian.org](http://security.debian.org) stable/updates Release [40.8kB]     
Get:4 [http://ftp.debian.org](http://ftp.debian.org) sid Release [77.8kB]
Ign [http://security.debian.org](http://security.debian.org) stable/updates Release
Ign [http://ftp.debian.org](http://ftp.debian.org) sid Release                                 
Hit [http://security.debian.org](http://security.debian.org) stable/updates/main Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://ftp.debian.org](http://ftp.debian.org) sid/main Packages    
Hit [http://ftp.debian.org](http://ftp.debian.org) sid/contrib Packages 
Hit [http://security.debian.org](http://security.debian.org) stable/updates/contrib Packages
Fetched 396B in 2s (153B/s)
Reading package lists... Done
W: GPG error: [http://security.debian.org](http://security.debian.org) stable/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: Failed to fetch [http://non-us.debian.org/debian-non-US/dists/stable/non-US/Release.gpg](http://non-us.debian.org/debian-non-US/dists/stable/non-US/Release.gpg)  Could not resolve 'non-us.debian.org'

W: Failed to fetch [http://non-us.debian.org/debian-non-US/dists/stable/non-US/main/i18n/Translation-en_US.bz2](http://non-us.debian.org/debian-non-US/dists/stable/non-US/main/i18n/Translation-en_US.bz2)  Could not resolve 'non-us.debian.org'

W: Failed to fetch [http://non-us.debian.org/debian-non-US/dists/stable/non-US/contrib/i18n/Translation-en_US.bz2](http://non-us.debian.org/debian-non-US/dists/stable/non-US/contrib/i18n/Translation-en_US.bz2)  Could not resolve 'non-us.debian.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems



Should I just comment out those links? The title for one of them, [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) , now says that it's unstable.
Thank you!

---

### Post by kestrel1 on 2009-04-03
I would comment out the debian links.

---

### Post by ajgreeny on 2009-04-03
In any case, if you didn't add those debian repos where on earth did they come from?  They are most certainly not in the default ubuntu sources.list file so someone must have done something very strange.  Has somebody else been "helping" you with installing any unusual applications not in the ubuntu repos?

Anyway, as kestrel1 says, comment out or delete the debian lines and it should be OK, though I'm not sure about the ignored lines, below, which don't even appear to be in your file, though they could be in a *sources.list.d* folder, a subfolder of /etc/apt
```
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") intrepid-security/main Translation-en_US        
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") intrepid-security/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") intrepid-updates/multiverse Translation-en_US
```

---

### Post by jrox717 on 2009-04-04
No, no one has helped me install anything or actually done anything on my computer. In any case I commented out those lines and have had no further problems. Thank you everyone!

---

### Post by raterwil on 2009-10-22
I am running 8.04 Server. I have received the following message (I see similar posts on this thread, but I'm still not sure what to do):

Any help is appreciated. Thanks :-)

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

