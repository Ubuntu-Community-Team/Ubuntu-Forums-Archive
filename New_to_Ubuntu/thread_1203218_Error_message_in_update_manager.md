---
title: "Error message in update manager"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by JoeNZ on 2009-07-03
Hello from NZ,

When I manually run the update manager, I get this error message:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Can someone please help?

Regards
JoeNZ

---

### Post by x33a on 2009-07-03
comment out the security.ubuntu.com lines in /etc/apt/sources.list

---

### Post by davit on 2009-07-03
> **x33a said:**
> comment out the security.ubuntu.com lines in /etc/apt/sources.list


Why would this be the case, is there a problem with 
"security.ubuntu.com"?

y'day I had problems with both 9.04 and 8.10 on various machines and unable to fetch packages. Gave a Bzip2 / Hash mismatch error or a unable to download some packages. Would it have been busy servers? I tried other mirrors and also changed the sources.list a number of times but still no success.

David

---

### Post by JoeNZ on 2009-07-03
My sources list reads like this:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunt$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted uni$
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted$

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaun$
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

Is there anything wrong there?

---

### Post by x33a on 2009-07-04
ok, i found the gpg key for this repo, see if it works.

```

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQBKTqrIQJdur0N9BbURAmlfAKCQZ86FjqocKdJuj+7yXszzc4VfewCeKGqT
KAuOJUbnFRcRy7sgWKHovjg=
=Ne5t
-----END PGP SIGNATURE-----
```[http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)

just copy this and paste it into an empty file. then import that file with 

system -> administration -> software sources -> authentication -> import key file.

---

### Post by JoeNZ on 2009-07-04
I copied the key over twice (I didn't know what the file extension was) and named it release.pgp and release.gpg. Tried importing both of them but nothing happened.
Also, I saw the comment above about the servers being busy so I got Software Sources to pick the best server for me. It chose a different NZ server.

From there, I have manually updated several times and there are no errors. I've since got rid of the Mozilla PPA's because I have been trying to install the latest Firefox 3.5 with no luck but I finally solved that.

Here is my updated sources list:
[I]               
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://nz2.archive.ubuntu.com/ubuntu/](http://nz2.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
[/I]

Are those *#Added by software-properties* suppose to be there?
Is there a way of telling whether I am receiving security updates from Ubuntu? I have received in the past OpenOffice updates, Wine updates, Cups etc but nothing that looks like a security update.

I have attached screenshots of my Software Sources set-up.

Regards
JoeNZ

---

### Post by x33a on 2009-07-04
so, you finally got rid of the problem?

as for security updates, you'll have to read the changelog of each package to find out if it's a security update, or a bug fix or anything else. are you getting kernel updates? if yes, then i guess it's nothing to worry about.

---

### Post by JoeNZ on 2009-07-04
Yes thank you.

I got the kernel update that came through last week or the week before. Ok, if that's the case then sweet as. Did those screenshots look right?

---

### Post by x33a on 2009-07-04
yes, the screenshots seem fine.

---

### Post by JoeNZ on 2009-07-04
Thank you for your help, much appreciated.

---

