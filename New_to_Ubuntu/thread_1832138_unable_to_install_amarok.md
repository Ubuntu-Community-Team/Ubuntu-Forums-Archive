---
title: "unable to install amarok"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by idom on 2011-08-24
Hi I am running ubuntu 10.04 LTS in gnome. And I wanted to install amarok which is kde based .

Is it possible to run amarok in gnome? 
when I do apt-get install amarok it said following 

Thanks in advance. 

idom-desktop:~> sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: phonon-backend-xine but it is not going to be installed or
                   phonon-backend
          Depends: kdebase-runtime (>= 4:4.4.2) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.4.2) but it is not going to be installed
          Depends: libphonon4 (>= 4:4.3.0) but it is not going to be installed
          Depends: libplasma3 but it is not going to be installed
          Depends: libqt4-script (>= 4:4.5.3) but it is not going to be installed
          Depends: libqt4-sql (>= 4:4.5.3) but it is not going to be installed
          Depends: libqt4-webkit (>= 4:4.5.3) but it is not going to be installed
          Depends: phonon (>= 4:4.5.2) but it is not going to be installed
          Depends: libqtscript4-core but it is not going to be installed
          Depends: libqtscript4-gui but it is not going to be installed
          Depends: libqtscript4-network but it is not going to be installed
          Depends: libqtscript4-xml but it is not going to be installed
          Depends: libqtscript4-sql but it is not going to be installed
          Depends: libqtscript4-uitools but it is not going to be installed
          Recommends: kdemultimedia-kio-plugins (>= 4:4.2.0) but it is not going to be installed
          Recommends: libqt4-sql-sqlite but it is not going to be installed
E: Broken packages

---

### Post by androssofer on 2011-08-24
> **idom said:**
> Hi I am running ubuntu 10.04 LTS in gnome. And I wanted to install amarok which is kde based .

Is it possible to run amarok in gnome? 
when I do apt-get install amarok it said following 

Thanks in advance. 

idom-desktop:~> sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: phonon-backend-xine but it is not going to be installed or
                   phonon-backend
          Depends: kdebase-runtime (>= 4:4.4.2) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.4.2) but it is not going to be installed
          Depends: libphonon4 (>= 4:4.3.0) but it is not going to be installed
          Depends: libplasma3 but it is not going to be installed
          Depends: libqt4-script (>= 4:4.5.3) but it is not going to be installed
          Depends: libqt4-sql (>= 4:4.5.3) but it is not going to be installed
          Depends: libqt4-webkit (>= 4:4.5.3) but it is not going to be installed
          Depends: phonon (>= 4:4.5.2) but it is not going to be installed
          Depends: libqtscript4-core but it is not going to be installed
          Depends: libqtscript4-gui but it is not going to be installed
          Depends: libqtscript4-network but it is not going to be installed
          Depends: libqtscript4-xml but it is not going to be installed
          Depends: libqtscript4-sql but it is not going to be installed
          Depends: libqtscript4-uitools but it is not going to be installed
          Recommends: kdemultimedia-kio-plugins (>= 4:4.2.0) but it is not going to be installed
          Recommends: libqt4-sql-sqlite but it is not going to be installed
E: Broken packages

i used amarok on ubuntu back in the day.. then got into banshee... but as it has ties to m$ i might go back.. anyway...

open up the software center and try and install it ther... 

failing that, open up "synaptic package manager" and c if thts works. the package manager tends to handle dependencies quite well...

---

### Post by idom on 2011-08-24
> **androssofer said:**
> i used amarok on ubuntu back in the day.. then got into banshee... but as it has ties to m$ i might go back.. anyway...

open up the software center and try and install it ther... 

failing that, open up "synaptic package manager" and c if thts works. the package manager tends to handle dependencies quite well...


Errors from synaptic package manager is giving similar error. it might be same only. 

marok:
 Depends: phonon-backend-xine but it is not going to be installed or
	phonon-backend
 Depends: kdebase-runtime but it is not going to be installed
 Depends: kdelibs5 but it is not going to be installed
 Depends: libphonon4 but it is not going to be installed
 Depends: libplasma3 but it is not going to be installed
 Depends: libqt4-script but it is not going to be installed
 Depends: libqt4-sql but it is not going to be installed
 Depends: libqt4-webkit but it is not going to be installed
 Depends: phonon but it is not going to be installed
 Depends: libqtscript4-core but it is not going to be installed
 Depends: libqtscript4-gui but it is not going to be installed
 Depends: libqtscript4-network but it is not going to be installed
 Depends: libqtscript4-xml but it is not going to be installed
 Depends: libqtscript4-sql but it is not going to be installed
 Depends: libqtscript4-uitools but it is not going to be installed
 Recommends: kdemultimedia-kio-plugins but it is not going to be installed
 Recommends: libqt4-sql-sqlite but it is not going to be installed

---

### Post by David Andersson on 2011-08-24
A similar problem in thread [http://ubuntuforums.org/showthread.php?t=1695419](http://ubuntuforums.org/showthread.php?t=1695419) suggests:

```
sudo apt-get install -f
sudo dpkg --configure -a
```

(Have not tried it myself)

---

### Post by idom on 2011-08-24
> **David Andersson said:**
> A similar problem in thread [http://ubuntuforums.org/showthread.php?t=1695419](http://ubuntuforums.org/showthread.php?t=1695419) suggests:

```
sudo apt-get install -f
sudo dpkg --configure -a
```

(Have not tried it myself)

Sorry did not work. It is giving same error as before.

Samarth

---

