---
title: "question on these commands"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-04-20
what does sudo apt-get update do?

and what does sudo apt-get upgrade do?

thanks for your information!

---

### Post by PacSci on 2009-04-20
sudo apt-get update refreshes the package cache - the list kept on your system of all the packages available for download.

sudo apt-get upgrade will upgrade all the packages to the latest version, or just some of them if you specify names on the command line.

---

### Post by iam_newhere on 2009-04-20
> **PacSci said:**
> sudo apt-get update refreshes the package cache - the list kept on your system of all the packages available for download.

sudo apt-get upgrade will upgrade all the packages to the latest version, or just some of them if you specify names on the command line.

if i do a sudo apt-get upgrade, will the upgrades installed be stable?

---

### Post by boblemur on 2009-04-20
yes they will be,


they are the official updates, they are the same as the update manager.


good practice is to use.

```
sudo aptitude update
sudo aptitude dist-upgrade

```

as aptitude is almost the same as apt-get although its smarter and should be used instead of apt-get.

dist-upgrade as apposed to upgrade will upgrade dependencies as well. (which basicly means its smarter than just upgrade)

---

### Post by iam_newhere on 2009-04-20
> **boblemur said:**
> yes they will be,


they are the official updates, they are the same as the update manager.


good practice is to use.

```
sudo aptitude update
sudo aptitude dist-upgrade

```

as aptitude is almost the same as apt-get although its smarter and should be used instead of apt-get.

dist-upgrade as apposed to upgrade will upgrade dependencies as well. (which basicly means its smarter than just upgrade)

thanks a lot!:popcorn:

---

