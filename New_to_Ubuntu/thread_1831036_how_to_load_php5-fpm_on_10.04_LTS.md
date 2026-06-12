---
title: "how to load php5-fpm on 10.04 LTS?"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-22
how to load php5-fpm on 10.04 LTS?

it is not on the repo.

aptitude install php5-fpm

Couldn't find any package whose name or description matched "php5-fpm"
Couldn't find any package whose name or description matched "php5-fpm"

---

### Post by 007casper on 2011-08-22
[https://launchpad.net/~brianmercer/+archive/php](https://launchpad.net/~brianmercer/+archive/php)
> 
sudo aptitude install python-software-properties
sudo add-apt-repository ppa:brianmercer/php

sudo aptitude -y update

sudo aptitude -y install php5-cli php5-common php5-mysql php5-suhosin php5-gd
sudo aptitude -y install php5-fpm php5-cgi php-pear php5-memcache php-apc
sudo service php5-fpm start

does that look ok?

---

### Post by 007casper on 2011-08-22
check these link out
[https://launchpad.net/~brianmercer/+archive/php](https://launchpad.net/~brianmercer/+archive/php)

[https://launchpad.net/~nginx/+archive/php5/+packages](https://launchpad.net/~nginx/+archive/php5/+packages)

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

---

