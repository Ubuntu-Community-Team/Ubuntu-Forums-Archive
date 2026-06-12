---
title: "Whats the differents between these terminal commands?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-22
whats the differences?
```
$ sudo apt-get upgrade
```

```
$ sudo apt-get update
```

---

### Post by adult swim on 2008-12-22
update checks for updates to your system and upgrade installs them

---

### Post by ken22 on 2008-12-22
update connects to the repos and downloads an index of current packages

upgrade uses the index you've downloaded using update and installs updates for the currently installed packages.

---

### Post by CatKiller on 2008-12-23
From **man apt-get**:

```
       update
           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.

       upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

```

You should generally check the manpages of an application first to find out what the options mean.

---

