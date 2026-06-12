---
title: "how do i get rid of this?"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-03-17
i have this symbol in my notification area and i can't seem to figure out how to get rid of it can you help?  attached is a pic

---

### Post by GrfyGrumpyBear on 2009-03-17
the gray warning symbol means that the system is doing... program installation, the broken window is the force-app-quit applet. try restarting. If it continues, open up a terminal with Applications->Accesories-Terminal and try:

```
sudo killall dpkg
```

---

### Post by mamamia88 on 2009-03-17
i was pointing to the triangle with the ! in the middle not the force quit

---

### Post by simeon87 on 2009-03-17
Does it give a message when you hover over it or when you click on it..?

---

### Post by Bölvaður on 2009-03-17
I am not familiar with that icon theme. If you know what icon set you are using you can identify it somewhere:

~/.icons  [COLOR="Silver"](user installed)[/COLOR]
/usr/share/icons/  [COLOR="Silver"](comes with the standard installation + apt-get installed themes)
[/COLOR]

I would guess it is update manager, possibly it is working when it is gray... just like the previous poster said (checking if there are any software needing updating)

---

### Post by orethrius on 2009-03-17
> **GrfyGrumpyBear said:**
> the gray warning symbol means that the system is doing... program installation, the broken window is the force-app-quit applet. try restarting. If it continues, open up a terminal with Applications->Accesories-Terminal and try:

```
sudo killall dpkg
```

Uh, if critical updates are being installed - as seems to be indicated by the icon - won't killing the installer result in a broken system?

---

### Post by mamamia88 on 2009-03-17
it said run check for updates manually which i did and it said some sources where out of date or no longer existed

---

### Post by taurus on 2009-03-17
Post the whole error message and also your /etc/apt/sources.list too.

```
sudo apt-get update
```

```
cat /etc/apt/sources.list
```

---

### Post by mamamia88 on 2009-03-17
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu.com/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.  

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main
deb [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid main universe

---

### Post by taurus on 2009-03-17
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the last line.

```
deb http://archive.ubuntu.com intrepid main universe
```
Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mamamia88 on 2009-03-17
thanks it worked

---

