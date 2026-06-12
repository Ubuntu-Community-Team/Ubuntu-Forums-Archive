---
title: "can someone help me fix this"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by jrandolph on 2009-10-28
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0D3C959DB2035A6
W: You may want to run apt-get update to correct these problems

---

### Post by jrandolph on 2009-10-28
i have run apt-get update and have also tried adding the key from here [http://ppa.launchpad.net/loell/ppa/ubuntu/dists/hardy/Release.gpg]("http://ppa.launchpad.net/loell/ppa/ubuntu/dists/hardy/Release.gpg")

---

### Post by ukripper on 2009-10-28
> **jrandolph said:**
> i have run apt-get update and have also tried adding the key from here [http://ppa.launchpad.net/loell/ppa/ubuntu/dists/hardy/Release.gpg]("http://ppa.launchpad.net/loell/ppa/ubuntu/dists/hardy/Release.gpg")

Have you imported this key in software sources?

---

### Post by jrandolph on 2009-10-28
yes i saved it and then went to software sources -> authentication and clicked import and chose that file then nothing - i assumed it would give me a reload box but i didnt get anything

---

### Post by philinux on 2009-10-28
Generic answer but should get you fixed.

[https://answers.launchpad.net/ubuntu/+faq/359](https://answers.launchpad.net/ubuntu/+faq/359)

---

### Post by konqueror7 on 2009-10-28
try this, [automate ppa key download]("http://deuified.blogspot.com/2009/06/automate-launchpad-ppas-gpg-keys.html")

---

### Post by ukripper on 2009-10-28
if above doesn't work, can you post contents of this file:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by jrandolph on 2009-10-28
> **konqueror7 said:**
> try this, [automate ppa key download]("http://deuified.blogspot.com/2009/06/automate-launchpad-ppas-gpg-keys.html")

I tried this and i get a text file - so i did the second command and added .txt to the end of it
then did the last line and it tells me 

bash: launchpad-update: command not found

---

### Post by jrandolph on 2009-10-28
> **ukripper said:**
> if above doesn't work, can you post contents of this file:
```
sudo gedit /etc/apt/sources.list
```


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) hardy main

---

### Post by jrandolph on 2009-10-28
i guess i didnt post all of it 

# 
# deb cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090709.1)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090709.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) hardy main

---

### Post by konqueror7 on 2009-10-28
> **jrandolph said:**
> I tried this and i get a text file - so i did the second command and added .txt to the end of it
then did the last line and it tells me 

bash: launchpad-update: command not found

sorry, because mine was already in bash's path, so i directly executed it...

try,
```
./launchpad-update
```

---

### Post by jrandolph on 2009-10-28
no go 


jacob@jacob:~$ cd Desktop
jacob@jacob:~/Desktop$ ./launchpad-update
bash: ./launchpad-update: No such file or directory

---

### Post by jrandolph on 2009-10-28
nevermind - i forgot to put .txt
it worked

---

### Post by konqueror7 on 2009-10-28
> **jrandolph said:**
> no go 


jacob@jacob:~$ cd Desktop
jacob@jacob:~/Desktop$ ./launchpad-update
bash: ./launchpad-update: No such file or directory
```
sudo cp launchpad-update /usr/bin
```
```
launchpad-update
```

be sure to make it executable first

---

### Post by jrandolph on 2009-10-28
this is what i got after

jacob@jacob:~/Desktop$ ./launchpad-update.txt
[sudo] password for jacob: 
Grabbing key DB2035A6 for archive ppa by ~loell
[sudo] password for jacob: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com DB2035A6
gpg: requesting key DB2035A6 from hkp server keyserver.ubuntu.com
gpg: key DB2035A6: public key "Launchpad PPA for Loell Anthony Erecre" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
DONE

---

### Post by jrandolph on 2009-10-28
but im not sure that i made it executable because I cant run the same thing again by jus putting in 
```
launchpad-update
```

---

### Post by konqueror7 on 2009-10-28
just do a 

```
sudo apt-get update
```

then it will be gone, it just works for ppa,,,

the thing is, when executing files in linux, sometimes depends on where your are, so some command are relative,,,but the problem should be gone after the update...

---

### Post by jrandolph on 2009-10-28
the problem is gone 
i really thank you both for your help on this
I like to think i know a thing or two but sometimes things like this show me that i dont know enough

---

