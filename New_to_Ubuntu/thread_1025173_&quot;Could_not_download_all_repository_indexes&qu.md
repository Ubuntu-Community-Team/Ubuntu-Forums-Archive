---
title: "&quot;Could not download all repository indexes&quot; 8.04"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by trooperchix on 2008-12-29
:confused:
```

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

```

Output is:

```

GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/source/Sources.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/source/Sources.gz  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.

```

No clue why.  How do I fix this?  More info to follow...

---

### Post by mkvnmtr on 2008-12-29
It is possible the repository mirror you are using is doing some mantinence and is down for a short time . If you are on 8.04 and up it is easy to try another mirror. If you are on one of the older distros it is posible support has ended for your distro.

---

### Post by linuxisevolution on 2008-12-29
> **mkvnmtr said:**
> It is possible the repository mirror you are using is doing some mantinence and is down for a short time . If you are on 8.04 and up it is easy to try another mirror. If you are on one of the older distros it is posible support has ended for your distro.

He is on Hardy, you can see from his apt errors.

---

### Post by thunk77 on 2008-12-29
How about using the official ubuntu repositories?
Are those the only repositories you're using?

---

### Post by trooperchix on 2008-12-29
Output of /etc/apt/sources.list

```

pjuggalo@Juggalo:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu-rocks.org/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy universe
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy universe
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy multiverse
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy-security universe
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy-security multiverse
deb http://apt.wicd.net hardy extras
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
# deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb http://ppa.launchpad.net/project-neon/ubuntu/ hardy main #Amarok
deb http://ppa.launchpad.net/fta/ubuntu hardy main #Firefox
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main #KDE 4
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
pjuggalo@Juggalo:~$ 


```

Help!!

---

### Post by trooperchix on 2008-12-29
oops...  posted last message twice..

---

### Post by RomeReactor on 2008-12-29
Hi. Try going to 'System->Administration->Software Sources' and on the first tab (Ubuntu Software) you'll find a "Download from:" dropdown menu; there, select "Other" and you'll be able to choose another server, or press "Select Best Server" so Ubuntu tries to find the one nearest to you.

---

### Post by thunk77 on 2008-12-29
> **RomeReactor said:**
> Hi. Try going to 'System->Administration->Software Sources' and on the first tab (Ubuntu Software) you'll find a "Download from:" dropdown menu; there, select "Other" and you'll be able to choose another server, or press "Select Best Server" so Ubuntu tries to find the one nearest to you.

That is an excellent suggestion.
Also, you could select main server. Better than editing manually the sources.list file.

---

### Post by trooperchix on 2008-12-29
I've already done that, and aside from speed things up, has made no difference.  I will say with all the research I'm doing, check this out and tell me if it is related and how to resolve this:

[https://launchpad.net/ubuntu/+mirror/archive.ubuntu-rocks.org-archive]("https://launchpad.net/ubuntu/+mirror/archive.ubuntu-rocks.org-archive")

That is the link I got from:

[http://www.ubuntu-rocks.org/]("http://www.ubuntu-rocks.org/") under the Ubuntu Archives Mirror option.

---

### Post by thunk77 on 2008-12-29
It sure looks like it's related. Probably the server is down and that is why there's no go.
If you have changed the server via "Software Sources" could you please repost your sources.list file?

---

### Post by trooperchix on 2008-12-29
> **thunk77 said:**
> It sure looks like it's related. Probably the server is down and that is why there's no go.
If you have changed the server via "Software Sources" could you please repost your sources.list file?

The above listed sources.list file is the result *after* the changed server...

---

### Post by thunk77 on 2008-12-29
No, this is what it should look like after you've chosen "Main Server"

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe #Added by software-properties
```

---

### Post by RomeReactor on 2008-12-29
> **trooperchix said:**
> The above listed sources.list file is the result *after* the changed server...

Were you prompted to reload the package information after changing servers? If not, try:
```
sudo aptitude update
```

---

### Post by trooperchix on 2008-12-30
I'll give it a shot...  Any other ideas?  Does anyone know if the ubuntu-rocks repositories are still maintained?

---

