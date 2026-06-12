---
title: "NEED HELP!!!! Synaptic Manager wont work!!"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by raptorsenior on 2011-05-08
Hi.
I'm having a problem with the synaptic manager. Here is the list:

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/lucid](http://us.archive.ubuntu.com/ubuntu/lucid) main
deb-src [http://us.archive.ubuntu.com/ubuntu/lucid](http://us.archive.ubuntu.com/ubuntu/lucid) main

And here is the error: 

E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Please Help!

---

### Post by lmarmisa on 2011-05-08
Have you modified the file **/etc/apt/sources.list**?

The last two lines seem wrong:

```

deb http://us.archive.ubuntu.com/ubuntu/lucid main
deb-src http://us.archive.ubuntu.com/ubuntu/lucid main

```

Try to comment them:

```

# deb http://us.archive.ubuntu.com/ubuntu/lucid main
# deb-src http://us.archive.ubuntu.com/ubuntu/lucid main

```

or change their syntax:

```

deb http://us.archive.ubuntu.com/ubuntu/ lucid main
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main

```

For editing the file, use the command


```

sudo gedit /etc/apt/sources.list

```

---

### Post by beew on 2011-05-08
Why would you have lucid repos in Natty? Should just delete them.

---

### Post by shuttleworthwannabe on 2011-05-09
yes, exactly as beew said.Remove those lines (comment them out in gedit as above) or use synaptic to remove the repositories.

HTH,
SWB

---

