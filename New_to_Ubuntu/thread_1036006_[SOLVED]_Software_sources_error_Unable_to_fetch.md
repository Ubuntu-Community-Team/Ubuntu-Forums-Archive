---
title: "[SOLVED] Software sources error Unable to fetch"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by digital-daniel on 2009-01-10
I'm getting this error:

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  backports/binary-amd64/Packages in Meta-index file (malformed Release file?)

Some index files failed to download, they have been ignored, or old ones used instead.

My source list file is below:




> # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid backports main universe restricted multiverse

---

### Post by drs305 on 2009-01-10
I was just able to access the backports. You might try a different server. Software Sources or Synaptic > Settings > Repositories > Download from > Other.

Added:
I just noticed when I added the ubuntu server backports my sources.list has a hyphen in the backports entry:
```

deb http://archive.ubuntu.com/ubuntu/ **intrepid-backports** universe main multiverse restricted

```

---

### Post by digital-daniel on 2009-01-10
> **drs305 said:**
> I was just able to access the backports. You might try a different server. Software Sources or Synaptic > Settings > Repositories > Download from > Other.

Added:
I just noticed when I added the ubuntu server backports my sources.list has a hyphen in the backports entry:
```

deb http://archive.ubuntu.com/ubuntu/ **intrepid-backports** universe main multiverse restricted

```
That did the trick. It was the missing hyphen. Thank you so much.


Daniel

---

