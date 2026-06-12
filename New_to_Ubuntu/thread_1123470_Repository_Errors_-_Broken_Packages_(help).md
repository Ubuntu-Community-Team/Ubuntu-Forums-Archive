---
title: "Repository Errors - Broken Packages (help)"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Sethalos on 2009-04-12
I have been trying most of the morning to install the programs I need to share my folders however, when I run the program I'm getting an error that says I have broken packages and it can't be resolved. 

So I ran a sudo apt-get upgrade and I received the following errors:

W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991                                                                                                                       
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263                                                                                                                             

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 778978B00F7992B0                                                                                                                                    

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783                                                                                                                               

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available:NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2C392DFEEFD17969
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680

W: Failed to fetch [http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/Release)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/Release](http://wine.budgetdedicated.com/apt/dists/intrepid/Release)

W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/Release](http://packages.medibuntu.org/dists/intrepid/Release)

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release)

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release)

W: Failed to fetch [http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
sethalos@sethalos-laptop:~$


I'm  not sure how to fix this..I've tried a few things but nothing seems to resolve the issues.

Thanks.

Seth

---

### Post by llamabr on 2009-04-12
What a mess.

post your /etc/apt/sources.list

You need to install the keys to go along with the repositories when you add them.  Otherwise you'll get those errors.

I would probably start fresh with a new list, and then add them one at a time.

---

### Post by Sethalos on 2009-04-12
Here it is:


# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by taurus on 2009-04-12
Is that the complete list because you are missing a few repos in there (from error messages)?  Otherwise, post

```
ls -la /etc/apt/sources.list.d
```

---

### Post by Sethalos on 2009-04-12
Ok, typed in that command, and this is what I got:

sethalos@sethalos-laptop:~$ ls -la /etc/apt/sources.list.d
total 96
drwxr-xr-x 2 root root 4096 2009-02-21 12:35 .
drwxr-xr-x 4 root root 4096 2009-04-12 10:28 ..
-rw-r--r-- 1 root root   79 2009-04-12 10:28 amarok-nightly.sources.list
-rw-r--r-- 1 root root   79 2009-04-12 10:28 amarok-nightly.sources.list.save
-rw-r--r-- 1 root root   70 2009-04-12 10:28 compiz.sources.list
-rw-r--r-- 1 root root   70 2009-04-12 10:28 compiz.sources.list.save
-rw-r--r-- 1 root root   77 2009-04-12 10:28 frostwire.sources.list
-rw-r--r-- 1 root root   77 2009-04-12 10:28 frostwire.sources.list.save
-rw-r--r-- 1 root root   80 2009-04-12 10:28 google_gadgets.sources.list
-rw-r--r-- 1 root root   80 2009-04-12 10:28 google_gadgets.sources.list.save
-rw-r--r-- 1 root root   66 2009-04-12 10:28 google.sources.list
-rw-r--r-- 1 root root   66 2009-04-12 10:28 google.sources.list.save
-rw-r--r-- 1 root root  229 2009-04-12 10:28 medibuntu.list
-rw-r--r-- 1 root root  229 2009-04-12 10:28 medibuntu.list.save
-rw-r--r-- 1 root root   87 2009-04-12 10:28 openoffice.sources.list
-rw-r--r-- 1 root root   87 2009-04-12 10:28 openoffice.sources.list.save
-rw-r--r-- 1 root root   67 2009-04-12 10:28 songbird.sources.list
-rw-r--r-- 1 root root   67 2009-04-12 10:28 songbird.sources.list.save
-rw-r--r-- 1 root root   74 2009-04-12 10:28 ultimate.sources.list
-rw-r--r-- 1 root root   74 2009-04-12 10:28 ultimate.sources.list.save
-rw-r--r-- 1 root root   62 2009-04-12 10:28 wine.sources.list
-rw-r--r-- 1 root root   62 2009-04-12 10:28 wine.sources.list.save
-rw-r--r-- 1 root root   86 2009-04-12 10:28 xbmc.sources.list
-rw-r--r-- 1 root root   86 2009-04-12 10:28 xbmc.sources.list.save
sethalos@sethalos-laptop:~$

---

### Post by taurus on 2009-04-12
How many third-party repos did you add to your list anyway (11)?  

Try something like

```
sudo mv /etc/apt/sources.list.d  /etc/apt/sources.list.d.bak
sudo mkdir /etc/apt/sources.list.d
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Sethalos on 2009-04-12
I'm not really sure why they are all there. I'm using the Ultimate Edition Distro, and they came as a default.  

However, your fix above seemed to have worked fine...no more issues. Thanks much for your help.

Seth

---

