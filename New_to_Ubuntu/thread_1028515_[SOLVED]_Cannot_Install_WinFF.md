---
title: "[SOLVED] Cannot Install WinFF"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by USFMD82 on 2009-01-02
I followed the Synaptic Instructions and after I reload, and I type WinFF in the search menu it does not come up, anyone have any suggestions? from another thread on this topic I am adding this to save time possibly in case I made an error somewhere

Sources.lst
```
# deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081030.3)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://winff.org/ubuntu intrepid universe
```

Thanks in advance for any assistance you can provide Note I am using Xubuntu

---

### Post by oldos2er on 2009-01-02
I don't know what search menu you're referring to, but try typing "winff" in a terminal to see of the program starts.

---

### Post by USFMD82 on 2009-01-02
Im talking about the search bar in synaptic After I follow all the directions and hit reload, ideally as i understand it it should pop up under the search so i can download it

---

### Post by FakeOutdoorsman on 2009-01-02
Perhaps you need to reload your package sources.  Open a terminal and enter:
```
sudo apt-get update
```
It should now show up in Synaptic.  There's probably a way to do this in Synaptic, but I'm not sure since I don't use it.

---

### Post by oldos2er on 2009-01-02
> **USFMD82 said:**
> Im talking about the search bar in synaptic After I follow all the directions and hit reload, ideally as i understand it it should pop up under the search so i can download it

 Ok, I see now. Are you using 'Search' or 'Quick Search'? 

 Or you could just type "sudo aptitude update && sudo aptitude install winff" in a terminal.

---

### Post by -kg- on 2009-01-02
> **FakeOutdoorsman said:**
> Perhaps you need to reload your package sources.  Open a terminal and enter:
```
sudo apt-get update
```
It should now show up in Synaptic.  There's probably a way to do this in Synaptic, but I'm not sure since I don't use it.

Yes, there's a way to update your sources in Synaptic.  The top-left button allows you to reload the package information.

I did a search for WinFF in Synaptics and it's not available.  And I have all my repositories enabled, before anyone asks (not back door, but I don't have sufficient skill to want to play with that yet :P ).

It isn't available in the Repos, but you can check [this page]("http://code.google.com/p/winff/wiki/UbuntuInstallation") for instructions on how to enable their repo to let you get it.

---

### Post by USFMD82 on 2009-01-05
Worked when I used the "search" instead of quick search THANKS!!

---

