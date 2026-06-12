---
title: "ubuntu web server 8.10 - Can't install anything"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by sujeewa on 2011-02-05
Dear All,

when i try to install any SW i got below error.

-------------------------------------------------------------------------------

root@firefoxlanka:~# sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libapache2-mod-php5 php5-common
Suggested packages:
  php-pear php5-timezonedb
The following NEW packages will be installed:
  libapache2-mod-php5 php5 php5-common
0 upgraded, 3 newly installed, 0 to remove and 34 not upgraded.
Need to get 1110B/2850kB of archives.
After this operation, 6320kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  php5-common libapache2-mod-php5 php5
Install these packages without verification [y/N]?

--------------------------------------------------------------------------------

pls help me to overcome this problem.

---

### Post by waynefoutz on 2011-02-05
8.10 is dead. the repositories got shut down last October. This is why you should stick with LTS releases, especially on a web server, it's supported for 5 years, not 18 months.

---

### Post by sandyd on 2011-02-05
> **waynefoutz said:**
> 8.10 is dead. the repositories got shut down last October. This is why you should stick with LTS releases, especially on a web server, it's supported for 5 years, not 18 months.
naw.
the repos are still here
[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

in your /etc/apt/sources.list
replace
[http://archives.ubuntu.com](http://archives.ubuntu.com) (or something similar, just replace whats before the third slash)
with 
[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

