---
title: "update manager errors"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by dbowlin17 on 2011-05-28
i have an issue with chrome and facebook, SO i went to update manager to see if there was an update i could install. well, that didn't go so well...


Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


I couldn't copy and paste what was in the update manager window... but i tried to google the issue and nothing i could find seemed to match what i had, nor did things i try work.

---

### Post by cogier on 2011-05-28
I am not sure what the issue is but it may be that the repository is just not available. Try again later/tomorrow and see if it works.

---

### Post by Rubi1200 on 2011-05-28
Try this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```

---

### Post by dnairb on 2011-05-28
One of lists of packages available is corrupt. Each list should be of the form:

```
Package: aacgain
Version: 1.8-0.0medibuntu1.1
Architecture: amd64
.
.
.

Package: aacplusenc
Version: 0.17.5-0.0medibuntu1
Architecture: amd64
.
.
.
```

But, as the error states, one of the sections does not start with "Package: "

In an attempt to correct this, in terminal run the following:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

This will remove all the list files, and then update the lists again.
If the problem persists after this, then as cogier stated there may be an issue with the online repositories.

[EDIT]Rubi1200 got there first - I was typing this out while he was posting[/EDIT]

---

