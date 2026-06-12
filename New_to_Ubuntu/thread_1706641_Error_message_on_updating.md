---
title: "Error message on updating"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by bvpainter on 2011-03-14
I got the following error message when trying to update. Can anyone tell me what to do about it.
"GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>GPG error: [http://www.4pane.co.uk](http://www.4pane.co.uk) lucid Release: The following signatures were invalid: BADSIG 03A5D5784BE0BA7B David Hart (signing rpms and debs) <david@4pane.co.uk>GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 04EED3E377741834 Launchpad GeoDGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG C84E1126DBF01B72 Launchpad PPA for Jakub JankiewiczGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG FAEB83059BD4ED25 Launchpad TrimageGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 17B51370292F6066 Launchpad KupferGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 83FBA1751378B444 Launchpad PPA for LibreOffice PackagingGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriXFailed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (113: No route to host)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/i18n/Translation-en.bz2](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/i18n/Translation-en.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/i18n/Translation-en_GB.bz2](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/i18n/Translation-en_GB.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by Perfect Storm on 2011-03-14
Looks like you have messed up your sourcelist big time.

Which version of Ubuntu do you use? As far I can see you have mixed 3 different releases.
The signing key error you also have is not an error but a warning that you are using some PPA's which are not set to trusted.

But first thing first. Lets check your sourcelist
```
cat /etc/apt/sources.list
```

---

### Post by bvpainter on 2011-03-14
> **Artificial Intelligence said:**
> Looks like you have messed up your sourcelist big time.

Which version of Ubuntu do you use? As far I can see you have mixed 3 different releases.
The signing key error you also have is not an error but a warning that you are using some PPA's which are not set to trusted.

But first thing first. Lets check your sourcelist
```
cat /etc/apt/sources.list
```
here is what I get from putting in the suggested command. I am using Mint 10.02

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib



deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia main upstream import



deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse



deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse



deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse



deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partner



deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free




deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb games
deb [http://www.4pane.co.uk/ubuntu/](http://www.4pane.co.uk/ubuntu/) lucid universe

---

### Post by Perfect Storm on 2011-03-14
If you're using mint, you should go here for help: [http://forums.linuxmint.com/](http://forums.linuxmint.com/) as they have their own forum.

But an advise, don't mix different sourcelist from different distros and different releases.


Thread closed.

---

