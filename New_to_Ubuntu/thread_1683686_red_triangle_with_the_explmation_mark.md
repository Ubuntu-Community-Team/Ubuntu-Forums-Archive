---
title: "red triangle with the explmation mark"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Billisnice on 2011-02-07
The red triangle with the explmation mark does not every go away...

Update seems to work ok though...

Any suggestions?

---

### Post by Billisnice on 2011-02-07
I get this when i check in update manager...

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tekkidd on 2011-02-07
Quite a few people have been getting that error. The fix would be to go into the terminal and type in: 
```
sudo gedit /etc/apt/sources.list
```
it will ask you for the password then open up a text file with a bunch of sites in it. 
search for ```
 [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

``` and append a "#" in front of it then save. 
after that run the command ```
sudo apt-get update
```
now you can update the system: ```
sudo apt-get dist-upgrade
```

---

### Post by Billisnice on 2011-02-07
here is the source,list

I do not see  [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release Candidate i386 (20100928)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by Billisnice on 2011-02-08
sudp apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

solved it, but i do not know why...

---

### Post by Paqman on 2011-02-08
> **tekkidd said:**
> Quite a few people have been getting that error. The fix would be to go into the terminal and type in: 
```
sudo gedit /etc/apt/sources.list
```


Couple of wee points:
[LIST=1]
[*]You don't need to edit your sources file by hand, there's a nice easy-to-use tool for it in Synaptic and Ubuntu Software Centre.
[*]For graphical apps like gedit, you want to use gksudo. Plain sudo is only for terminal apps.
[*]The recommended way to update your system using the command line is apt-get upgrade, not apt-get dist-upgrade.
[/LIST]

---

### Post by Tyggna on 2011-02-08
> **Billisnice said:**
> sudp apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

solved it, but i do not know why...

It solved it because you effectively told your system that you "authorize" communication with that server.  It was probably giving you the exclamation point in the first place because your computer wasn't sure if you trusted where your software was coming from.

It's a security feature--to make sure no one puts illegitimate software on your system by pretending to be a legitimate source.

---

