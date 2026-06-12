---
title: "k3B, Squeezecenter, MySql-libraries conflict"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Sceiron on 2010-01-11
I cannot have k3b installed at the same time as Squeezecenter because the applications have different dependencies regarding library verisons of mysql............

How do i get around this problem??

I must have squeezecenter, and i really love k3B.
Brasero is crap, k3B is the only option :D

```

sudo apt-get install k3b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl deluge-common libhtml-template-perl libdbi-perl
  libdbd-mysql-perl mysql-client-5.0 libmysqlclient15-dev
  libboost-thread1.38.0 libplrpc-perl libmysqlclient15off
  libtorrent-rasterbar5 deluge-core zlib1g-dev libboost-filesystem1.38.0
  python-chardet libreadline5 libboost-system1.38.0 python-libtorrent
  libboost-python1.38.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akonadi-server kdebase-workspace-bin mysql-server-core-5.1
  plasma-widgets-workspace
Suggested packages:
  normalize-audio toolame sox movixmaker-2 vcdimager kdebase-kio-plugins
  transcode plasma-scriptengines
The following packages will be REMOVED:
  mysql-server-5.0 mysql-server-core-5.0 squeezeboxserver
The following NEW packages will be installed:
  akonadi-server k3b kdebase-workspace-bin mysql-server-core-5.1
  plasma-widgets-workspace
0 upgraded, 5 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B/9,746kB of archives.
After this operation, 150MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by Sceiron on 2010-01-14
Lazy bump

---

