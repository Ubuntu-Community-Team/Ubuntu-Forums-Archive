---
title: "Apt-get fails with 404"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by H4rm0ny on 2011-01-16
I have a fresh install of Ubuntu Server Hardy. I'm unable to install any new packages via apt-get. It fails with a 404 when trying to retrieve them. apt-get update appears find (at least it reports hits and doesn't throw any errors). I can't tell if apt-get upgrade works as it says everything is already up to date.

I can ping the repositories that are 404'ing both by IP and by name. That's as far as my knowledge of this goes. Please help! :(

I get the following output when trying to install Apache, for example:
```
root@mybox:~# apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-worker apache2-utils apache2.2-common libaprutil1 libpq5
Suggested packages:
  apache2-doc
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common libaprutil1 libpq5
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1537kB/1612kB of archives.
After this operation, 5874kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://us.archive.ubuntu.com hardy-updates/main libpq5 8.3.7-0ubuntu8.04.1
  404 Not Found [IP: 91.189.88.45 80]
Err http://security.ubuntu.com hardy-security/main libpq5 8.3.7-0ubuntu8.04.1
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com hardy-security/main apache2-utils 2.2.8-1ubuntu0.5
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com hardy-security/main apache2.2-common 2.2.8-1ubuntu0.5
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com hardy-security/main apache2-mpm-worker 2.2.8-1ubuntu0.5
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com hardy-security/main apache2 2.2.8-1ubuntu0.5
  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.7-0ubuntu8.04.1_amd64.deb  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.8-1ubuntu0.5_amd64.deb  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.8-1ubuntu0.5_amd64.deb  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-worker_2.2.8-1ubuntu0.5_amd64.deb  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.8-1ubuntu0.5_all.deb  404 Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

My /etc/apt/sources.list is as follows:
```
#deb cdrom:[Ubuntu-Server 8.04.2 _Hardy Heron_ - Release amd64 (20090121.1)]/ hardy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Thanks for any replies,

H.

---

### Post by ikt on 2011-01-16
you need to do: sudo apt-get update

first

---

### Post by H4rm0ny on 2011-01-16
> **ikt said:**
> you need to do: sudo apt-get update

first

I'm logged in as root and as mentioned, apt-get update worked fine. At least it appears to be so:
```
root@mybox:~# apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
```

---

### Post by ikt on 2011-01-16
> **H4rm0ny said:**
> I'm logged in as root and as mentioned, apt-get update worked fine. At least it appears to be so:
```
root@mybox:~# apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
```

yep, now you can do sudo apt-get upgrade and sudo apt-get install apache2

the problem was that because the package index was out of date it was trying to download updates that don't exist/have been replaced.

---

### Post by H4rm0ny on 2011-01-16
> **ikt said:**
> yep, now you can do sudo apt-get upgrade and sudo apt-get install apache2

the problem was that because the package index was out of date it was trying to download updates that don't exist/have been replaced.

No. As I've said, I don't need to sudo because I'm already logged in as root, upgrade doesn't do anything because everything is currently up to date as far as it is concerned, and the apache install fails as in the first post with the 404 error. Something is wrong.

H.

---

### Post by yeats on 2011-01-16
You might try a different mirror... They sometimes get out of sync.  See this list: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

You might also wait a bit to see if the problem fixes itself.

> No. As I've said, I don't need to sudo because I'm already logged in as root

No need to point this out.  Using sudo is the preferred/supported way of doing things.  Just know that when someone who is helping you says sudo, you can adjust that for the way you're doing it directly as root.

---

### Post by H4rm0ny on 2011-01-16
> **yeats said:**
> You might try a different mirror... They sometimes get out of sync.  See this list: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

This has solved the problem. I searched and replaced through the sources.list file and changed all instances of 

[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

to one I selected from the list of mirrors, and tried an apt-get update. It picked up lots of new stuff and is installing Apache now.

Thank you very much for this. I had assumed the error was at my end and it didn't occur to me there could be a problem with the repository itself.

> **yeats said:**
> 
No need to point this out.  Using sudo is the preferred/supported way of doing things.  Just know that when someone who is helping you says sudo, you can adjust that for the way you're doing it directly as root.

Apologies to the other respondent. No offence was meant.

Thanks to both of you,

H.

---

