---
title: "linux headers 386 package"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by true_friend on 2006-08-15
I am trying to install intel536/37 ep modems. my problem is the packages requiered are build essential which i have from internet but linux headrs 386  i can not get. on internet i is giving 404 not found error. from cd after mounting install cd it does not install it from cd try to download form internet.
have i to clean up me sources.list for getting package installed from cd????
i always can install a pcakage from cd if i have a fresh install of ubuntu and not connected to internet yet.
plz guide me in this regard or provide me some alive link to download linux headers 386.
Edit: found the package for dapper but it is tarball. if debian package would be available it will better. :)
Regards
True_Friend

---

### Post by az on 2006-08-15
> **true_friend said:**
> I am trying to install intel536/37 ep modems. my problem is the packages requiered are build essential which i have from internet but linux headrs 386  i can not get. on internet i is giving 404 not found error. from cd after mounting install cd it does not install it from cd try to download form internet.
have i to clean up me sources.list for getting package installed from cd????
i always can install a pcakage from cd if i have a fresh install of ubuntu and not connected to internet yet.
plz guide me in this regard or provide me some alive link to download linux headers 386.
Edit: found the package for dapper but it is tarball. if debian package would be available it will better. :)
Regards
True_Friend

Use any package manager to get rid of those online repositories.  All those packages are on the cd.  On the DEkstop (live) cd, they are found on a repository apart from the live session.  Boot into your installed ubuntu system and then insert the cd while at the desktop.  The package manager will start and you will be able to install build-essential and linux-headers-386 from there.

---

