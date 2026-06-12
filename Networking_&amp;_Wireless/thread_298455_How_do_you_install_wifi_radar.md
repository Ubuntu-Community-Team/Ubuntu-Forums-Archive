---
title: "How do you install wifi radar?"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Heyholetsgogrant on 2006-11-12
Can anyone tell me how to install wifi radar for Ubuntu? The network manager that comes with unbuntu is confusing and being a pain.

Thanks!

Grant

---

### Post by cloakable on 2006-11-12
Depends. Have you added the extra repositories?

---

### Post by 454redhawk on 2006-11-12
did you try

sudo apt-get install wifi-radar

---

### Post by FrodoB on 2006-11-12
Change your /etc/apt/sources.list to:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

And then the apt-get install wifi-radar should work for you.

---

### Post by ralf57 on 2006-12-01
The solutions provided above require you to already being connected  to the net.
If not yet, go to
[http://packages.ubuntulinux.org/edgy/net/wifi-radar](http://packages.ubuntulinux.org/edgy/net/wifi-radar) (for edgy)
from another PC, download the package, then install it by typing
```

sudo dpkg -i wifi-radar_1.9.7-0ubuntu2_all.deb

```
in a terminal
Note that the name of the file will very likely change in the future.
After installing, open
Applications >> Internet >> Wifi-Radar
and configure your connection
Hope this helps.
ralf57

---

