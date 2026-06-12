---
title: "Update error"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by bipinbaglung on 2010-02-07
[COLOR="Blue"]In synaptic package manager after click reload button it starts downloading packages.And at last it comes with this message:
[/COLOR]

"{
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)  

W: Failed to fetch [http://np.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.bz2](http://np.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://np.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.bz2](http://np.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.bz2)  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.
}"

[COLOR="Blue"]Then I close the window and [COLOR="DarkRed"]"mark all upgrades"[/COLOR] then This message appears:
[/COLOR]
"{
W: Duplicate sources.list entry [http://np.archive.ubuntu.com](http://np.archive.ubuntu.com) karmic/multiverse Packages (/var/lib/apt/lists/np.archive.ubuntu.com_ubuntu_dists_karmic_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://np.archive.ubuntu.com](http://np.archive.ubuntu.com) karmic/multiverse Packages (/var/lib/apt/lists/np.archive.ubuntu.com_ubuntu_dists_karmic_multiverse_binary-amd64_Packages)
}"
[COLOR="DarkRed"]
How can i solve this?[/COLOR]

---

### Post by jken146 on 2010-02-07
Please post the contents of /etc/apt/sources.list

---

### Post by bipinbaglung on 2010-02-07
> **jken146 said:**
> Please post the contents of /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
deb-src [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic main restricted
deb-src [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-updates main restricted
deb-src [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic universe
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic multiverse
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-security main restricted
deb-src [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-security universe
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-security multiverse

---

### Post by jken146 on 2010-02-07
You do have some repeated entries, which is causing apt to get confused.  Really you want something like this:

```

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ karmic-partner main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse

```

Change the server from [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) to one near you and comment out the entries you don't want (put a # at the start of the line).

Edit this file with sudo, e.g.
```
$ sudo nano /etc/apt/sources.list
```

Then do
```
$ sudo apt-get update
```

---

