---
title: "Can I install a RPM download"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by thadacto on 2010-03-01
I have just downloaded the latest version of Open Office (3.2) but it has come in a RPM package which also has a setup program.
Can I use this to install OO on my Ubantu 8.04 64 bit machine?

---

### Post by themusicalduck on 2010-03-01
You can download it in .deb format from the open office website.

I installed 3.2 on my system using this guide here - [http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html)

For future reference, you can if you need convert rpm files to .deb using a program called Alien, but it's better to use a deb if you can.

---

### Post by thadacto on 2010-03-01
My first download was (unfortunately) the 32 bit version which took about 90 minutes.
When I try to download the 64 bit version from the Argentine download site I am given an estimated time of 8 hours + to complete. (The joys of living in a rural location down here).

The RPM version came from a UK site which again took about 90 minutes.

I've just tried the local Argi site again and still over 8 hours to download.

So far I've spent the last 6 hours trying to get it right and I'm starting to get a bit naft off.

Thanks any way

---

### Post by superfrogman94 on 2010-03-01
in the future you can actually convert a rpm to deb by using alien
```
sudo apt-get install alien
```then use 
```
alien X.rpm
```replace X with whatever your rpm package name is

---

### Post by thadacto on 2010-03-01
Thanks superfrogman94 - I'll give that a go

---

### Post by Hagar Delest on 2010-03-02
Beware of the OOo RPMs, there may be some scripts that cause problems when aliened. See last section of first post: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

NB: don't use the script but the package manager (dpkg).

---

### Post by Mark Phelps on 2010-03-03
I've used alien myself on RPMs and the result has been mixed.  Self-contained simple stuff with few or no dependencies tended to work OK.  Complex stuff with lots of dependencies failed every time.

I would strongly recommend against using it for something as complex as Open Office.  You run the risk of lots of dependencies that might not be resolved properly.

---

### Post by The Cog on 2010-03-03
I agree - you are probably better off taking the time to download the .deb version. I recommend copying the URL from the browser and downloading it with wget - like this:
> wget [http://download.services.openoffice.org/files/localized/en-GB/3.2.0/OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz](http://download.services.openoffice.org/files/localized/en-GB/3.2.0/OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz) because it retries quite persistently if you have connection difficulties.

---

