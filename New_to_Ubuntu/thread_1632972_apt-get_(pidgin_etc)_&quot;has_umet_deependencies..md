---
title: "apt-get: (pidgin etc) &quot;has umet deependencies....but it it not going to be installed&quot;"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-11-28
So I have Ubuntu Minimal 10.04 with added software (gnome-core etc). Anyhow, my understanding was that <sudo apt-get install> handles unmet dependencies. On other threads I have checked, it was recommended to look at /etc/apt/sources.list: 

note that in : system>admin>software sources, GUI, i see "canonical open source software main" but I dont see it in the sources.list file below (maybe this could be part of the problem? ) I have had no problems installing software to this point.


 ```
# deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
# deb http://security.ubuntu.com/ubuntu lucid-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

```
sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gyachi: Depends: libgpgme11 (>= 1.1.8) but it is not going to be installed
          Depends: libgtkhtml2-0 (>= 2.11.1) but it is not going to be installed
          Depends: libgtkspell0 (>= 2.0.10) but it is not going to be installed
          Depends: libmcrypt4 but it is not going to be installed
          Recommends: w32codecs but it is not installable
  pidgin: Depends: pidgin-data (>= 1:2.6.6) but it is not going to be installed
          Depends: pidgin-data (< 1:2.6.6-z) but it is not going to be installed
          Depends: libgtkspell0 (>= 2.0.10) but it is not going to be installed
          Depends: libpurple0 (>= 1:2.6.0) but it is not going to be installed
          Recommends: pidgin-libnotify but it is not going to be installed

``` and 
```
sudo apt-get install gyachi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gyachi is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gyachi: Depends: libgpgme11 (>= 1.1.8) but it is not going to be installed
          Depends: libgtkhtml2-0 (>= 2.11.1) but it is not going to be installed
          Depends: libgtkspell0 (>= 2.0.10) but it is not going to be installed
          Depends: libmcrypt4 but it is not going to be installed
          Recommends: w32codecs but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by mikewhatever on 2010-11-28
Try refreshing the index with **sudo apt-get update** .

---

### Post by UbuNoob001 on 2010-11-28
thanks to anyone who might have been researching my problem. Messing around, I was able to find a solution that, hopefully, might be of use to someone else with the same problem. 



1. Upon going to Synaptic, I tried "fix broken packages". 
2. Synaptic's response was "dependency problem has been fixed"
3. However the dependencies were never installed so
4. Once I asked it to fix broken packages, I clicked "Apply"
5. It installed the very files that, above, apt said "would not be installed"
6. Gyache was able to be installed

---

### Post by UbuNoob001 on 2010-11-28
> **mikewhatever said:**
> Try refreshing the index with **sudo apt-get update** .


mike, thanks for the suggestion however when I tried that earlier, it did not work. Solution published above. 

Thread Marked As Solved.

---

### Post by wojox on 2010-11-28
Why didn't you just run

```
sudo apt-get -f install
```

The -f option is to Fix.

---

### Post by UbuNoob001 on 2010-11-29
> **wojox said:**
> Why didn't you just run

```
sudo apt-get -f install
```The -f option is to Fix.

yeah i tried that recommendation  that was part of the error output "E:..."
however the issue was not resolved. Solution above.

---

