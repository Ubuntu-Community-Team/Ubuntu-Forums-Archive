---
title: "Checking Updates fails"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by Tuxdroid on 2011-02-26
Hi

Maybe i changed too much of ubuntu, but a week ago it started with this message over and over. My connection is fin, but dont know about the connection with the updatepage. However everytime i start up my ubuntu the update managers just give updates. But if i check randomly no connection is established.

W:Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

SO any idea or is it a global fault.

Greetz

Tuxdroid

---

### Post by Perfect Storm on 2011-02-26
Remove the PPA for GDM2setup and you should be fine. The error tells you that it (GDM2setup PPA) doesn't exist anymore.

---

### Post by Tuxdroid on 2011-02-26
thx AI, gonna look it up to remove it.

tom@tom-AMILO-PI-1536:~$ sudo apt-get remove python-gdm2setup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-gdm2setup

---

### Post by plucky on 2011-02-26
> **Tuxdroid said:**
> thx AI, gonna look it up to remove it.

tom@tom-AMILO-PI-1536:~$ sudo apt-get remove python-gdm2setup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-gdm2setup

Artificial Intelligence meant remove the PPA from Software Sources, not remove python-gdm2setup.

Open **Ubuntu Software Centre > Edit > Software Sources** and un-tick that PPA as a source.Then reload the Sources and see if you still have the error.

Good Luck

---

### Post by Tuxdroid on 2011-02-26
Thx, plucky

another thing i learnt today

Did it and Done it

---

