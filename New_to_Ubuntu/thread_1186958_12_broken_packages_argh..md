---
title: "12 broken packages argh."
date: 2009-06-14
forum: New to Ubuntu
---

### Post by Crunchy the Headcrab on 2009-06-14
Ubuntu 9.04 AMD64 Fresh Install, Good Disc, No installation Errors.  Try to update:

> You have 12 broken packages on your system!

Use the "Broken" filter to locate them.> noneya@m-pc:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  e2fsprogs: PreDepends: libuuid1 (>= 1.15) but it is not installed
  libblkid1: Depends: libuuid1 (>= 1.05) but it is not installed
  libnm-glib0: Depends: libuuid1 (>= 1.05) but it is not installed
  libnm-util1: Depends: libuuid1 (>= 1.36) but it is not installed
  libparted1.8-10: Depends: libuuid1 (>= 1.05) but it is not installed
  libsm6: Depends: libuuid1 (>= 1.36) but it is not installed
  libuuid-perl: Depends: libuuid1 (>= 1.05) but it is not installed
  network-manager: Depends: libuuid1 (>= 1.05) but it is not installed
  reiserfsprogs: Depends: libuuid1 but it is not installed
  samba-common: Depends: libuuid1 (>= 1.05) but it is not installed
  util-linux: PreDepends: libuuid1 (>= 1.05) but it is not installed
  uuid-runtime: Depends: libuuid1 (>= 1.40.4) but it is not installed
E: Unmet dependencies. Try using -f.
noneya@m-pc:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libuuid1
The following NEW packages will be installed:
  libuuid1
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/47.4kB of archives.
After this operation, 119kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2465 package `gnome-system-monitor':
 `Depends' field, reference to `libsigc++-2.0-0c2a': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

I have two questions:

1: Is this fixable>
2: How the crap can it be broken when I just installed it?

Sorry for the abruptness, but I really like Ubuntu and I want it to work but man are all these errors annoying.

---

### Post by alphacrucis2 on 2009-06-14
Try

```
sudo apt-get update
sudo apt-get dist-upgrade


```

---

### Post by Crunchy the Headcrab on 2009-06-14
Well for whatever reason it worked after rebooting.
I did this:
noneya@m-pc:~$ sudo apt-get -f install

It ran something that appeared to be working (it didn't give me any errors and it output something that sounded like it was working).  Now synaptic says I have no broken packages and my system is up to date.

Strange since it said it never updated anything, but at least it's not giving me error messages.

BTW thanks for your timely response :D

---

### Post by powel212 on 2009-06-14
This has also happened to me twice with Jaunty.

P.

---

