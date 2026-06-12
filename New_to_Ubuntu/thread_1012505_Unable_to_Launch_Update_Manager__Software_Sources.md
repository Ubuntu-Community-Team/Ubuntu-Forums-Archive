---
title: "Unable to Launch Update Manager / Software Sources"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Frank_F on 2008-12-15
Hi

I am receiving "failed to run /usr/bin/software-properties-gtk as user root

unable to copy users Xauthorization file


Thanks,
frank

---

### Post by taurus on 2008-12-15
What happens when you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Tatty on 2008-12-15
what happens if you do:
```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

---

### Post by Frank_F on 2008-12-15
Hello

I receive on the update .......

Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_US             
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [189B]        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_US      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/universe Sources
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources
  404 Not Found
Fetched 3B in 1s (2B/s)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Frank_F on 2008-12-15
Hi


 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by taurus on 2008-12-15
Feisty has expired so the repos have been moved.

---

### Post by Frank_F on 2008-12-15
Hi

Sorry I am confused.....I have installed 7.10....not sure what to do...I am willing to upgrade to alleviate this issue...but am not able to...help

---

### Post by Sef on 2008-12-15
Since Feisty has reached its end of life, there will be no more updates nor security patches for it.   Best thing to do would be to either do a clean install of Hardy Heron, or Intrepid Ibex.  You can choose to keep Feisty, but any holes in it will remain unpatched.

---

### Post by taurus on 2008-12-15
> **Frank_F said:**
> Hi

Sorry I am confused.....I have installed 7.10....not sure what to do...I am willing to upgrade to alleviate this issue...but am not able to...help

I am confused too because majority of the repos in your /etc/apt/sources.list are feisty except four gutsy's repos!

```
cat /etc/apt/sources.list
```

---

### Post by Frank_F on 2008-12-15
Included is the cat /etc/apt/sources.list

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by frankleeee on 2008-12-15
I think the advice Sef gave you is going to get you to a regularly update-able distro. If you go this route down load a daily iso of Hardy or Intrepid and backup anything you want to save and do a fresh install.

---

### Post by Frank_F on 2008-12-15
thanks...

---

### Post by Frank_F on 2008-12-15
makes sense..thank you

---

