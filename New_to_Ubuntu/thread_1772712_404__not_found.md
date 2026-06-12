---
title: "404  not found"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by soorajviraat on 2011-06-01
Failed to fetch [http://paparazzi.enac.fr/ubuntu/dists/maverick/main/source/Sources](http://paparazzi.enac.fr/ubuntu/dists/maverick/main/source/Sources)  404  Not Found

my sources.list is here

```

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) maverick main
deb-src [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) maverick main

deb [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) natty main

```

---

### Post by wolfen69 on 2011-06-01
It just means that the link is invalid or down at the moment. What were you trying to get with that repo? Also, you should uncomment (remove the # in the beginning of the lines) the "extras" and "partners" links, to be able to download more stuff.

---

### Post by Pand5461 on 2011-06-01
It means what it says - the corresponding file is not present on the server.

Why do you use repos both for maverick and natty? If you upgraded from 10.10 to 11.04 then you don't need the repos with lines ending with "maverick main". I'd suggest to comment those lines.

---

### Post by soorajviraat on 2011-06-01
i tried wat u said
my present sources.list is as  follows
```

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) natty main
deb-src [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) natty main

```

and the errors shown in the terminal are

```

W: Failed to fetch [http://paparazzi.enac.fr/ubuntu/dists/natty/main/source/Sources](http://paparazzi.enac.fr/ubuntu/dists/natty/main/source/Sources)  404  Not Found [IP: 10.93.0.35 3128]

W: Failed to fetch [http://paparazzi.enac.fr/ubuntu/dists/natty/main/binary-amd64/Packages](http://paparazzi.enac.fr/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found [IP: 10.93.0.35 3128]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

errors shown in synaptic is as follows

ailed to fetch [http://paparazzi.enac.fr/ubuntu/dists/natty/main/source/Sources](http://paparazzi.enac.fr/ubuntu/dists/natty/main/source/Sources)  404  Not Found [IP: 10.93.0.36 3128]
Failed to fetch [http://paparazzi.enac.fr/ubuntu/dists/natty/main/binary-amd64/Packages](http://paparazzi.enac.fr/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found [IP: 10.93.0.36 3128]
Some index files failed to download. They have been ignored, or old ones used instead.

PLS REPLY

ADVANCE THANX FOR THE REPLY

---

### Post by lisati on 2011-06-01
FYI: to get the "code" thing working, highlight the information you're copying and click on the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button at the top of the post editor.

---

### Post by plucky on 2011-06-01
> W: Failed to fetch [http://paparazzi.enac.fr/ubuntu/dist...source/Sources](http://paparazzi.enac.fr/ubuntu/dist...source/Sources)  404  Not Found [IP: 10.93.0.35 3128]

W: Failed to fetch [http://paparazzi.enac.fr/ubuntu/dist...amd64/Packages](http://paparazzi.enac.fr/ubuntu/dist...amd64/Packages)  404  Not Found [IP: 10.93.0.35 3128]

E: Some index files failed to download. They have been ignored, or old ones used instead.

Clear out your list files with ```
sudo rm /var/lib/apt/lists/* -vf
```
Then run ```
sudo apt-get update && sudo apt-get upgrade
```

If you still get the error,then go into **Software Sources** and change your "Download Server" and then run the above commands again.


Good Luck

---

### Post by Pand5461 on 2011-06-01
Apparently the repo doesn't have source packages. Just comment the line ```
deb-src http://paparazzi.enac.fr/ubuntu natty main
``` and everything's gonna be OK.
btw, those warnings don't mean any harm to your system, so they can be ignored.

---

