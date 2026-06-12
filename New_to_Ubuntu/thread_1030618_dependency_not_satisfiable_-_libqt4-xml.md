---
title: "dependency not satisfiable - libqt4-xml"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by boblettoj99 on 2009-01-04
hi i am getting this error when trying to install acetoneiso, a cd image mounting program.
i looked in adept manager and libqt4-xml isn't there although libqt4-core and several others are. how do i get the xml one to show up?

thanks

---

### Post by kestrel1 on 2009-01-04
try this:
```
sudo apt-get install libqt4-xml
```

---

### Post by boblettoj99 on 2009-01-04
it says it can't find package libqt4-xml

---

### Post by shifty_powers on 2009-01-04
you could grab the deb file from [http://packages.ubuntu.com/intrepid/libqt4-xml](http://packages.ubuntu.com/intrepid/libqt4-xml) adn install it with gdebi...

---

### Post by Elfy on 2009-01-04
Check that you have the repos enabled - can't tell you where to check unfortunately not really ever used kubuntu.

In hardy I think it's in backports

---

### Post by boblettoj99 on 2009-01-04
hmmm just tried that link you gave me, im using gutsy and it says its not available in this suite??

---

### Post by boblettoj99 on 2009-01-04
all the standard repositories are enabled...

---

### Post by boblettoj99 on 2009-01-04
i may be being stupid here but does it look like some lines are missing to you too?

> deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse #Added by software-properties
# Line commented out by installer because it failed to verify:


---

### Post by Elfy on 2009-01-04
Not sure if you'll be able to use it in gutsy - it's new for hardy which is why it's in backports.

---

### Post by boblettoj99 on 2009-01-04
oh lame, oh never mind then!
thanks for the help

---

### Post by Elfy on 2009-01-04
You could try this [http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)

I had to use the wget command as the deb location as dead.

---

### Post by bulletxt on 2009-01-05
Ubuntu Gutsy is "very old" especially for new softwares like QT4. I highly suggest to upgrade your system to at least Ubuntu Hardy ;)

Of course you can always compile latest QT4 by yourself...but believe me you'll be faster upgrading :)

---

