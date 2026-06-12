---
title: "updating nmap through terminal"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by fartofagony on 2011-06-24
hi!

i downloaded nmap from the ubuntu software center but the version was an older one. was wondering if there re commands i can type in terminal to update the current version

thnks!

---

### Post by trizrK on 2011-06-24
Update manager will search for the update. I believe ubuntu actually has the program in their archives. 
terminal:
sudo apt-get update
sudo apt-get upgrade
cheers

---

### Post by wildmanne39 on 2011-06-24
> **fartofagony said:**
> hi!

i downloaded nmap from the ubuntu software center but the version was an older one. was wondering if there re commands i can type in terminal to update the current version

thnks!Hi, if you want one more up to date then the one in the repositories, you have to install it from the programs site, you can not update the one in the repositories or update to the new version without going to the site that has the new one and installing it from there. If it is a deb package just download it from there site and double click on it and software center should install it. Some sites you have to add there ppa to the repositories in synaptic then you can use a command to install it in the terminal. some you download from there site and you have to use ./configure, make install, so it can be confusing.

---

### Post by trizrK on 2011-06-24
Or just go to nmap.org 
Here's a tarball for the latest stable version [http://nmap.org/dist/nmap-5.51.tar.bz2](http://nmap.org/dist/nmap-5.51.tar.bz2)
Extract that and install through the make command in terminal

---

### Post by haqking on 2011-06-24
> **fartofagony said:**
> hi!

i downloaded nmap from the ubuntu software center but the version was an older one. was wondering if there re commands i can type in terminal to update the current version

thnks!


compile at [http://nmap.org/book/inst-source.html](http://nmap.org/book/inst-source.html)
source at [http://nmap.org/download.html](http://nmap.org/download.html)

EDIT :Ninja'd above ;-)

---

