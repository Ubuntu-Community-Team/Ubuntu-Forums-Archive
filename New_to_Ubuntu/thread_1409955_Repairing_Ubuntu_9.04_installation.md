---
title: "Repairing Ubuntu 9.04 installation"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Sejanus on 2010-02-18
Is there any way? I accidentally deleted many required packages, including gnome. Internet connection does not work too, and CD-ROM as well (at least /media/CDrom is empty despite CD being inside). 

I do have live CD (thats how I'm writing this anyway) ;) 

apt-get --fix-missing doesnt work obviously, with no internet connection.

---

### Post by anaconda on 2010-02-18
well..
sudo apt-get install xxx
will first check if you already have that package in you /var/cache/apt/archives -folder. and tries to download the packages only if they are not found from that directory.

If yuo havn't emptied apt-cache, then you might be in luck. What happens if you type eg:
sudo apt-get install ubuntu-desktop

---

### Post by Sejanus on 2010-02-18
The problem is, I dont know what packages I'm missing. I noticed missing the most obvious, like the fact that I can boot into command line only and I have no internet :)

I'm going to try ubuntu-desktop now.

---

### Post by Sejanus on 2010-02-18
apt-get tries to fetch packages from archives.ubuntu.com and does not succeed :( Any way to force it to use live-cd or something? Or maybe there's some way to repair like Windows Install CDs have?

---

### Post by Sejanus on 2010-02-18
anybody? :(

---

