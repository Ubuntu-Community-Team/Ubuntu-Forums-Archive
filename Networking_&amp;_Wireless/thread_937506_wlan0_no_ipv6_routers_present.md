---
title: "wlan0: no ipv6 routers present"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by agim on 2008-10-03
I am having trouble using my net connection. It says I am connected every time. but I haven't been able to access a web page. My downloaded kb reading is 0.0. 
the dmesg I get is this 

wlan0: no ipv6 routers present

I just let it be for about 2 hours today, and suddenly it worked, with no new important dmesg results.

Does anyone understand this?

this is the rest of the dmesg results, in case something was important

[  536.234208] wlan0: no IPv6 routers present
[ 1424.103956] kjournald starting.  Commit interval 5 seconds
[ 1424.103980] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[ 1424.104328] EXT3 FS on sda6, internal journal
[ 1424.104335] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by iponeverything on 2008-10-04
you can turn off ipv6 if you want and that message will go away though I don't think that it related to your problem. 

Turn off ipv6 by changing "alias net-pf-10 ipv6" to "alias net-pf-10 off"
in /etc/modprobe.d/aliases

while your trying to connect open a terminal:

cd /var/log
sudo tail -vf syslog messages daemon.log

See if you can get an idea of what is going on.  Do <ctl>+c 
to stop the tail.

---

