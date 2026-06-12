---
title: "wine help!"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by flaxairn on 2010-02-22
I've downloaded the current stable version of wine on my ubuntu 9.10 then opened my terminal and did this.. : 

christina@skagDEfeater:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bsd-mailx: Depends: postfix but it is not going to be installed or
                      mail-transport-agent
  lsb-core: Depends: postfix but it is not going to be installed or
                     mail-transport-agent
  wine: Depends: wine1.2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
christina@skagDEfeater:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
christina@skagDEfeater:~$ 


what happened?
what do I do to install wine?

---

### Post by cariboo on 2010-02-22
It seems you have some broken dependencies, you forgot to add sudo to the apt-get command, it should be:

```
sudo apt-get -f install
```

---

