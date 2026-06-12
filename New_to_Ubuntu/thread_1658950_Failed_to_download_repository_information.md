---
title: "Failed to download repository information"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by SuperFreak on 2011-01-03
I have been getting the following message when trying updates. There is a red triangle in  right side of top panel with an exclamation mark that says my update information is outdated.


Failed to download repository information

Check your Internet connection.

W:Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by oldos2er on 2011-01-03
[http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/)

There is no repo for Maverick there, it only goes up to Lucid.

---

### Post by endotherm on 2011-01-03
if everything was working fine the other day, then just wait a few hours and update your repo status again (sudo apt-get update or open synaptic/software-center). most repository reachability problems are either intermittent or come from from installing bad repos (or perhaps installing good repos badly I suppose).

---

### Post by SuperFreak on 2011-01-03
Should there be be a Maverick repo. My update manager says it has been 11 days since a successful update

---

### Post by oldos2er on 2011-01-03
You'd need to contact whoever maintains that PPA.

---

### Post by SuperFreak on 2011-01-03
Thanks,

I removed [http://ppa.launchpad.net/aheck/ppa/u...rce/Sources.gz](http://ppa.launchpad.net/aheck/ppa/u...rce/Sources.gz) from software sources, seems to work now

---

### Post by MrPok on 2011-03-14
(Although this says SOLVED)

If you are not using the program RubyRipper anymore, stick with your solution. ;)

Otherwise, you just might want to edit the source location where the update program looks..
[SIZE="1"](background info: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu))[/SIZE]

In Software Sources: go to the "Other Software" tab and look-up your *[http://ppa.launchpad.net/aheck](http://ppa.launchpad.net/aheck)* ..etc. 
If you choose "Edit", then in the next screen you'll notice that after "Distribution:" it says "*maverick*".  This was filled in automagically. [SIZE="1"](however, as mentioned in the posts above, it doesn't exist)[/SIZE]
If you simply change this to "*lucid*", the update process will not give errors anymore.

Hope this clears things up ;)

Kind regards,

Paul

---

### Post by bhavin23 on 2011-07-26
just do

sudo gedit /etc/apt/source.list

search for problematic source (404 not found url), if you don't want to delete the line just add # at the beginning of that line.
After that do in terminal

sudo apt-get update

Moral:

if you are able to sync all other repo, why not this. so just disable it.
:guitar:

---

### Post by SuperFreak on 2011-07-26
```
sudo gedit /etc/apt/source.list
```

Opens any empty file

---

### Post by oldos2er on 2011-07-26
Use 'gksu' with gedit; also the file name is sources.list ```
gksu gedit /etc/apt/sources.list
```

---

### Post by SuperFreak on 2011-07-26
Thanks

---

### Post by G_R_O_N_D on 2011-08-08
I had a similar problem, except that the repositories that failed to download aren't PPAs and (I suppose) seem more important:
-------------------------------------------------------------------------------------------------------
Failed to fetch[ http://]("http://ftp.se.debian.org/debian/dists/etch/main/source/Sources.gz")  -->

[ftp.se.debian.org/debian/dists/etch/main/source/Sources]("http://ftp.se.debian.org/debian/dists/etch/main/source/Sources.gz").gz 
[ftp.se.debian.org/debian/dists/etch/non-free/source/Sources.gz]("http://ftp.se.debian.org/debian/dists/etch/non-free/source/Sources.gz")
[ftp.se.debian.org/debian/dists/etch/main/binary-i386/Packages.gz]("http://ftp.se.debian.org/debian/dists/etch/main/binary-i386/Packages.gz")
[ftp.se.debian.org/debian/dists/etch/non-free/binary-i386/Packages.gz]("http://ftp.se.debian.org/debian/dists/etch/non-free/binary-i386/Packages.gz")

404 Not Found [IP: 130.239.18.163 80]
-------------------------------------------------------------------------------------------------------
I'm running 10.10 Maverick and didn't have any problems up until last week or so when this started happening.

Are these repositories important? Should I even worry about this?

Thanks.

---

### Post by oldos2er on 2011-08-08
Why would you want Debian Etch repos in Maverick? I would disable them if I were you.

---

### Post by G_R_O_N_D on 2011-08-08
What are they? I didn't add them, they were just there.

---

### Post by oldos2er on 2011-08-09
Debian Etch is a different distro than Ubuntu, those repos are not going to be in any default Ubuntu installation. Are you running Ubuntu on your own computer?

---

### Post by s.m.knipe on 2011-08-20
I have been getting this too over the past few days, and although I have it temporarily "resolved" by commenting the problematic sources out of "sources.list," I feel as though there should be an actual answer for the sudden change. Mine are from the jaunty multiverse repos, which I don't remember downloading for anything but must have at some point- this laptop has only been loaded with Maverick and now Natty:


> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.170 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by tetrisalphabet on 2011-08-30
I'm getting this too, but in my case it's a little weirder.

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/mozilla-team/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/mozilla-team/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozilla-team/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozilla-team/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

I added the Mozilla PPAs the other day so I could update to Firefox 6, but now when I go into /etc/apt/sources.list they aren't even there, so I can't even comment them out.

---

### Post by oldos2er on 2011-08-30
PPAs are usually installed to /etc/apt/sources.list.d/

---

### Post by sarang031705 on 2011-08-30
here's What appears when using gksu gedit:

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-security universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-security universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-security multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiverse universe

---

