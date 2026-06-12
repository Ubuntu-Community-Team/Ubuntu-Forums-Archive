---
title: "Aircrack help needed"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by whoshotmydog on 2007-06-17
I'm trying to install aircrack-ng-0.9 but I get stuck when attempting to do a make install. 
I get a huge load of warnings and errors upon doing the make install and nothing good comes from it; I'd appreciate any help or suggestions to what might be keeping me from installing this program.

Btw, I thought it might be the linux header. Which is 2.6.20-15-generic 

If I do need to update header plz give links for header updates. Also, I have no active connection to the internet via the computer that is running Ubuntu so any kind of auto-update is out of the question.

Thx.

---

### Post by sharke on 2007-06-17
In a terminal
sudo apt-get install build-essential
now install downloaded file.
Regards
Sharke

---

### Post by whoshotmydog on 2007-06-18
i tried that and all I get is an error saying couldn't find build-essential. Before you ask, yes I am in fact in the directory that the tarball data was extracted too. I'm probably doing something stupid, but help is appreciated.

---

### Post by sharke on 2007-06-18
Why not install aircrack-ng from repos
apt-get istall aircrack-ng
Regards
Sharke

---

### Post by tturrisi on 2007-06-18
> **sharke said:**
> Why not install aircrack-ng from repos
apt-get istall aircrack-ng
Regards
Sharke
because it's an old version in repos.

install latest aircrack-ng version, open a ROOT terminal & do:
```
cd /usr/src
apt-get install linuxheaders-`uname -r`
apt-get install build-essential
wget http://download.aircrack-ng.org/aircrack-ng-0.9.tar.gz
tar -zxvf aircrack-ng-0.9.tar.gz
cd aircrack-ng-0.9
make
make install
```

---

### Post by sharke on 2007-06-18
You need build-essential installed it is in the repos so i dont understand the can not find error. maybe a problem with apt sources.
Regards
Sharke

---

