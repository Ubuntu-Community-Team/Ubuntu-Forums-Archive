---
title: "Broadcom 43xx"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by frylock on 2007-10-19
It would be nice if there was an official howto for people who don't have access to alternative connections

[http://fridge.ubuntu.com/taxonomy/term/50](http://fridge.ubuntu.com/taxonomy/term/50) Kind of ignored here.

So far I've managed to get the driver working from following in the terminal

#!/bin/sh

set -e

tarname=kernel-binary-wl-0.5.tar.gz
dname=wl_apsta.o
if [ -e /usr/bin/wget ]; then DL=wget; fi
if [ -e /usr/bin/curl ]; then DL="curl -o $tarname"; fi

cd /tmp
rm -rf wl
# [http://langerland.de/linux/bcm43xx/firmware.html;](http://langerland.de/linux/bcm43xx/firmware.html;) we need
# a microcode11 one; not now atm but to be future-safe. openwrt has
# one (wl_apsta.o)
$DL http://downloads.openwrt.org/sources/$tarname
tar xfvz $tarname
cd wl
bcm43xx-fwcutter $dname
mkdir -p /lib/firmware
for i in *.fw; do
        mv $i /lib/firmware/$i;
done
cd ..
rm -rf wl

but although the driver can find the network it won't connect (gutsy, WPA enabled)

any ideas?

---

### Post by linuxwizard on 2007-10-21
I don't see any docs for Gusty but maybe something here might help

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

---

