---
title: "vnuml tun device /dev/net/tun not found."
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by asalford on 2007-01-30
Thanks in advance for reading this post

running Dapper on an old laptop and trying to setup vnuml and keep getting the following error.  the site has almost no info about the problem.

The ultimate goal is to setup a virtual router lab.  if there are easier or better ways of doing this, I will be happy to entertain those ideas also.  I have already loaded quagga & zebra

Here begins the saga.

configure: error: tun device /dev/net/tun not found.  Please set the appropriate device using the --with-tun option.

but I ran config with the following options.

./configure --with-build_modules --with-tun=/dev/net/tun

I tried it with the module loaded and unloaded.
lsmod | grep tun
tun                    11904  0

ubuntu reports the following 
ls /dev/net/tun
/dev/net/tun

---

### Post by asalford on 2007-01-30
found the answer

[http://jungla.dit.upm.es/~vnuml/doc/current/install/index.html#debinstall](http://jungla.dit.upm.es/~vnuml/doc/current/install/index.html#debinstall)
quote:
2. Installing from .deb package

An APT respository has been set up for VNUML related packages. The installation procedure is as follows:

   1. Add the following line to the /etc/apt/sources.list file:

      deb [http://jungla.dit.upm.es/~vnuml/debian](http://jungla.dit.upm.es/~vnuml/debian) binary/

   2. Update package list:

      apt-get update

   3. Install VNUML along the packages it depends on

      apt-get install vnuml

In addition, although they are not mandatory packages to work with VNUML, it is strongly recommended you install the following:

apt-get install vlan xterm bridge-utils screen

end quote:

---

