---
title: "Help regarding ns-2 installation"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by ashwintk on 2010-02-17
Hi,

was trying to install ns2-2.34 version on ubuntu-8.04
I followed these steps:

$ wget [http://nchc.dl.sourceforge.net/sourceforge/nsnam/ns-allinone-2.34.tar.gz](http://nchc.dl.sourceforge.net/sourceforge/nsnam/ns-allinone-2.34.tar.gz)
$ tar -xzvf ns-allinone-2.34.tar.gz
$ cd ns-allinone-2.34
$ sudo apt-get install build-essential autoconf automake libxmu-dev
$ ./install
$ gedit ~/.bashrc 
$ source ~/.bashrc
$ ns

but when i execute 
sudo apt-get install build-essential autoconf automake libxmu-dev

am getting the following error and ns-2 is not running properly

PLS HELP

dpkg: error processing enomalism2 (--configure):[FONT=Verdana]
[/FONT]subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of slapd-dbg:
 slapd-dbg depends on slapd (= 2.4.9-0ubuntu0.8.04.3); however:
  Package slapd is not configured yet.
dpkg: error processing slapd-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 slapd
 enomalism2
 slapd-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zvacet on 2010-02-18
```
sudo dpkg --configure -a
```

---

