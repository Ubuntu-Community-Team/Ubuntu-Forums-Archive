---
title: "Apt-mirror under the chroot environment failure"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-05-19
I used the apt-mirror tool to mirror the ubuntu hardy repositories. Now when I try to make my live cd, and go in to chroot edit I mv my repository folder to that filesystem, and change the sources.list accordingly, but its not picking up the repository folder, any ideas?

---

### Post by ericeclifford on 2009-05-19
Now this is weird, Ok My repository under the chroot enviroment installs ubuntu-restricted-extras and the medibuntu keyring, but their are like tons of broken packages, heres a few.

The following packages have unmet dependencies:
  boxee: Depends: libcurl4-openssl-dev but it is not going to be installed
         Depends: python-sqlite but it is not going to be installed
         Depends: libmozjs-dev but it is not going to be installed
  mplayer: Depends: libcucul0 (>= 0.99.beta13b-1) but it is not going to be installed
  openoffice.org: Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.1) but 1:3.0.1-9ubuntu3 is to be installed
                  Depends: openoffice.org-filter-binfilter but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
  serpentine: Depends: python-4suite-xml but it is not going to be installed
              Depends: python-gnome2-extras (>= 2.14.2-1) but it is not going to be installed
E: Broken packages





AND some of these have more broken depends as well if I try to single them out, And the one thats broken for mplayer, saids it can be installed but will erase lots of packages including ubuntu-desktop.

BUT, these same programs work perfectly using the local repository I created in the MAIN root environment, but it will not work in the chroot environment, Which is the edit folder for my live cd. Anyone know if I am missing something? I am using 8.04.2 and the iso image 8.04.2 for my live cd.

---

### Post by ericeclifford on 2009-05-19
Perhaps its possible to go to my original root while in chroot environment, and get the repository that way?

---

### Post by ericeclifford on 2009-05-19
Is there no one familiar with this program(apt-mirror)?

---

### Post by ericeclifford on 2009-05-19
help

---

### Post by ericeclifford on 2009-05-20
bump

---

