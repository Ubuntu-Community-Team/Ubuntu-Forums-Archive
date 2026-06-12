---
title: "how to download g++"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by orky7 on 2009-06-18
hi this is my problem the PC on which i am loading Xubuntu don't have a net connection and no way i can have one on that PC, but i want to install the c++ compiler that is g++ on it so how to install it. i have a net connection on my lappy..i mean how to get all the dependent packages and install it. is there is any single .deb for it....

---

### Post by credobyte on 2009-06-18
[http://packages.ubuntu.com/jaunty/devel/build-essential](http://packages.ubuntu.com/jaunty/devel/build-essential) ( replace *jaunty* with what you are currently using ).

---

### Post by orky7 on 2009-06-18
yup buddy i already seen that in debian website but if u click on it then there will be 4-5 packages and inside those 4-5 packages there are more dependence packages so the recursiveness goes on so how to download and install.....

---

### Post by KIAaze on 2009-06-18
This should help you:
[https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

---

### Post by orky7 on 2009-06-18
ok i will try it and reply back....

---

### Post by -kg- on 2009-06-18
There is a .deb file available for it.  Go to the following link:

[http://archive.debian.org/debian-archive/debian/dists/Debian-2.1/main/binary-i386/devel/]("http://archive.debian.org/debian-archive/debian/dists/Debian-2.1/main/binary-i386/devel/")

Then look for the link to download the "g++_2.91.66-0slink2.deb" file.

I don't know whether this will install the required dependencies without an internet connection, though.  Usually, (if I am not mistaken) dependencies are resolved through apt-get or aptitude, even when installing software through a deb file.  You will have to somehow download and install any dependencies, as well.

---

### Post by orky7 on 2009-06-18
hey thanks but i discovered a wire in some old box that will connect the ADSL modem to my old pc's USB, so is the ADSL modem gona work with the USB port what i mean is there is going to be a driver problem( but i am using the modem with ubuntu in my lappy with RJ45 port or lan port....ok i will try it first.

---

### Post by -kg- on 2009-06-18
Yeah, with internet access it's a piece of cake.  Just open Synaptic, search for G++, and mark it for installation.  It will take care of the installation and resolve any dependencies.

---

### Post by goldblattster on 2009-06-18
Anyway, to compile almost everything written C or C++ (includes gcc and make, etc.)
```
sudo apt-get install build-essential
```
To handle the autogen files
```
sudo apt-get install automake
```
To safely get the stuffs into your system.
```
sudo apt-get install checkinstall
```
If you need just g++, search for it in synaptic or plug in
```
sudo apt-get install g++
```
(not sure if the command will work)

---

