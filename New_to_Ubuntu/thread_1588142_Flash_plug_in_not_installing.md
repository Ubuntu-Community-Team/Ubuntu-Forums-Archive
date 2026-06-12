---
title: "Flash plug in not installing"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by Darris on 2010-10-04
When I type this:
 sudo apt-get install flashplugin-nonfree

I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 35 not upgraded.
Need to get 21.5kB of archives.
After this operation, 229kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse flashplugin-installer 10.1.53.64ubuntu0.9.10.1
  404  Not Found [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse flashplugin-installer 10.1.53.64ubuntu0.9.10.1
  404  Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse flashplugin-nonfree 10.1.53.64ubuntu0.9.10.1
  404  Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.53.64ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.53.64ubuntu0.9.10.1_i386.deb)  404  Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.1.53.64ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.1.53.64ubuntu0.9.10.1_i386.deb)  404  Not Found [IP: 91.189.88.37 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


it seems as if none of the sites are still on or something.

---

### Post by Dustin2128 on 2010-10-04
download straight from adobe, if I recall correctly they have deb packages.
[http://www.adobe.com/support/flashplayer/downloads.html](http://www.adobe.com/support/flashplayer/downloads.html)

---

### Post by sandyd on 2010-10-04
> **Darris said:**
> When I type this:
 sudo apt-get install flashplugin-nonfree

I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 35 not upgraded.
Need to get 21.5kB of archives.
After this operation, 229kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse flashplugin-installer 10.1.53.64ubuntu0.9.10.1
  404  Not Found [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse flashplugin-installer 10.1.53.64ubuntu0.9.10.1
  404  Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse flashplugin-nonfree 10.1.53.64ubuntu0.9.10.1
  404  Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.53.64ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.53.64ubuntu0.9.10.1_i386.deb)  404  Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.1.53.64ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.1.53.64ubuntu0.9.10.1_i386.deb)  404  Not Found [IP: 91.189.88.37 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


it seems as if none of the sites are still on or something.
```

sudo apt-get update
```
then try again.

---

### Post by bodhi.zazen on 2010-10-04
You could consider gnash or lightspark, both open source alternates to flash.

They do not work on every site, but tend to be over looked as alternates to flash.

[http://ubuntuguide.net/lightspark-an-alternative-high-performance-free-flash-player](http://ubuntuguide.net/lightspark-an-alternative-high-performance-free-flash-player)

Testing and bug fixing open source alternates would help all.

---

### Post by khelben1979 on 2010-10-04
In case all of the above doesn't work for you, there is another way of doing it as well: download the source package file. After unpacking you simply copy libflashplayer.so to the /home/[your user]/.mozilla/mozilla/plugins/ file catalog.

The bad side with this one is that you need to do the same thing every time you want to get it updated. I use it myself to get the most recent version. I don't need to rely on if the apt repos. have been updated or not.

Having a sources.list file which directly points at the file catalog at the Adobe ftp would be the best solution. The drawback if everyone would do it: the downloading speed and the bandwith gets extremely high if everyone uses the same ftp for updates.

---

