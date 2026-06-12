---
title: "[SOLVED] Synaptic won't load package lists"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by ginestre on 2009-01-04
Synaptic won't load the following package lists- what am I doing wrong?

TIA




[http://sm.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://sm.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 193.206.140.37 80]
[http://sm.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://sm.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 193.206.140.37 80]
[http://sm.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://sm.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 193.206.140.37 80]
[http://sm.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://sm.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 193.206.140.37 80]
[http://sm.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://sm.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 193.206.140.37 80]
[http://sm.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://sm.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found [IP: 193.206.140.37 80]
[http://sm.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://sm.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 193.206.140.37 80]
[http://sm.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://sm.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 404 Not Found [IP: 193.206.140.37 80]

---

### Post by azr on 2009-01-04
It could be that that server is down. Try the switching the source in the repositry to the main one.

---

### Post by northern lights on 2009-01-04
These are Feisty repositories.

Feisty's lifetime, as any non-LTS release's, was 18 month. Feisty was released in April 2007 - you can do the math.

Check [here]("http://sm.archive.ubuntu.com/ubuntu/dists/") - ./feisty/ is obsolete and not existent anymore.

Upgrade to a newer release.

You could simply run ```
sudo apt-get dist-upgrade
```to upgrade to Gutsy, but given how old the system is, I'd recommend backing up the data in /home (if it's not on a separate partition) and going for a fresh install of either Intrepid (8.10) or Hardy (8.04).

Given that you've kept Feisty for such a long time, I'd say opt for Hardy, cause it'll be even less likely to give you trouble and further it's an LTS release with three years of support for the desktop version.

---

### Post by namdung on 2009-01-04
Firstly, is there any particular reason why u r stuck with old Feisty 7.04 when the latest Intrepid Ibex 8.10 is available.

Feisty is not supported anymore and the Feisty packages u r looking for are not available in the servers.

I strongly recommend that u upgrade to stable Hardy Heron 8.04.1 LTS which is supported for 3 years. The next release 8.04.2 is out anytime now.

Upgrading from 7.04 to 8.04/8.10 is not supported and I recommend u go for a clean install if possible.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

If ur hardware specs are low then consider the lightweight version Xubuntu.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[http://www.xubuntu.org/](http://www.xubuntu.org/)

Anyways do try the following to update ur current repository list:
```
sudo apt-get update
```

Do write if u need further clarifications.

---

### Post by ginestre on 2009-01-04
(message deleted)

---

