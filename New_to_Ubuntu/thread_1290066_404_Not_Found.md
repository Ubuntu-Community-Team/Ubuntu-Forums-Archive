---
title: "404 Not Found ???????????????????"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by baskar007 on 2009-10-13
> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FE8956A73C5EE1C9GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7AGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E5F6C1A69241F1Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty/restricted/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty/main/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty/multiverse/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty/universe/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/main/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/universe/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/restricted/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/restricted/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/main/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/main/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/universe/source/Sources](http://ftp.iitm.ac.in/ubuntu/dists/jaunty-security/universe/source/Sources)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

this is error msg displayed when i try to update my software sources.

I live in India. 

anyone suggest me which server is best?

---

### Post by swoody on 2009-10-13
Well it appears that you are having a GPG key issue. Open a terminal (Applications>Accessories>Terminal) and enter this command:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FE8956A73C5EE1C9 2836CB0A8AC93F7A 61E5F6C1A69241F1
```
then run:
```
sudo apt-get update
```
and see if the problem persists. If you get no errors from this command, you are good to go :)

As far as servers go, there are only two other servers in India, so I would just pick either one of those. You could test the servers, and see which one would be fastest for you. Go to System>Administration>Software Sources Then under the 'Ubuntu Software' tab, find the 'Download From' drop-down menu, and select 'Other'. In the new window that appears, click on 'Select Best Server'. This will test out your connection speed between *all* of the Ubuntu servers. Just to let you know, this may take some time, so be patient with it. After it does it's thing, it will select the fastest server from your testing. Sometimes, it may select a server that's nowhere near you, if this is the case, you may just want to select one of the other servers in India manually.

---

### Post by baskar007 on 2009-10-13
i have selected cn server but its very very slow.
apt-get work in 200bps?

---

### Post by baskar007 on 2009-10-13
India servers are too slow, and 404 error present in India server?

THis is my soureccelist:    is any worng address present here?
> # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse

deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) hardy main
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main
#tu-ppa/backports/ubuntu jaunty main
deb [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty/

deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main

deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) jaunty main

deb [http://ppa.launchpad.net/webkit-team/epiphany/ubuntu](http://ppa.launchpad.net/webkit-team/epiphany/ubuntu) jaunty main
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/stani/ppa/ubuntu](http://ppa.launchpad.net/stani/ppa/ubuntu) jaunty main

---

### Post by swoody on 2009-10-13
Please see my above post, I added some more info to it. Also, can you run:
```
gksu gedit /etc/apt/sources.list
```
and paste the entire contents of that file here. Thanks :)

---

### Post by baskar007 on 2009-10-13
> **swoody said:**
> Please see my above post, I added some more info to it. Also, can you run:
```
gksu gedit /etc/apt/sources.list
```
and paste the entire contents of that file here. Thanks :)
here my sources.list:  [http://ubuntuforums.org/showpost.php?p=8097092&postcount=4](http://ubuntuforums.org/showpost.php?p=8097092&postcount=4)

---

### Post by baskar007 on 2009-10-13
r-desktop:~/Documents$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FE8956A73C5EE1C9 2836CB0A8AC93F7A 61E5F6C1A69241F1
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys FE8956A73C5EE1C9 2836CB0A8AC93F7A 61E5F6C1A69241F1
gpg: requesting key 3C5EE1C9 from hkp server keyserver.ubuntu.com
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: requesting key A69241F1 from hkp server keyserver.ubuntu.com
gpg: key 3C5EE1C9: public key "Launchpad PPA for Stéphane Marguet" imported
gpg: key 8AC93F7A: public key "Launchpad Kubuntu Updates" imported
gpg: key A69241F1: public key "Launchpad PPA for midori" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 3
gpg:               imported: 3  (RSA: 3)



is GPG key having a issue?

---

### Post by swoody on 2009-10-13
From a quick glance, that sources.list looks fine by me. Did you just change that? I noticed none of them are the iitm.ac.in server that you reported issues with in the first post. With your new sources.list are you still experiencing this errors?

---

### Post by swoody on 2009-10-13
> **baskar007 said:**
> r-desktop:~/Documents$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FE8956A73C5EE1C9 2836CB0A8AC93F7A 61E5F6C1A69241F1
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys FE8956A73C5EE1C9 2836CB0A8AC93F7A 61E5F6C1A69241F1
gpg: requesting key 3C5EE1C9 from hkp server keyserver.ubuntu.com
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: requesting key A69241F1 from hkp server keyserver.ubuntu.com
gpg: key 3C5EE1C9: public key "Launchpad PPA for Stéphane Marguet" imported
gpg: key 8AC93F7A: public key "Launchpad Kubuntu Updates" imported
gpg: key A69241F1: public key "Launchpad PPA for midori" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 3
gpg:               imported: 3  (RSA: 3)



is GPG key having a issue?

Well, it appears that you've added the 3 keys you were missing in your original post. Can you try running:
```
sudo apt-get update
```
and see if you're still getting the same errors? Thanks again :)

---

### Post by baskar007 on 2009-10-13
thank you. 
now there are no errors.
thank you very much swoody

---

### Post by swoody on 2009-10-13
No problem, glad everything worked out for you :)

Since there is now a solution to your query, could you mark this thread [SOLVED]? You can do it by going to the 'Thread Tools' in the top right of this page, and selecting to 'Mark Thread as [SOLVED]'

---

### Post by baskar007 on 2009-10-13
> **swoody said:**
> No problem, glad everything worked out for you :)

Since there is now a solution to your query, could you mark this thread [SOLVED]? You can do it by going to the 'Thread Tools' in the top right of this page, and selecting to 'Mark Thread as [SOLVED]'
I did it swoody.

---

