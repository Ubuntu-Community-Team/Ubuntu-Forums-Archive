---
title: "ndiswrapper not installing driver"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by prc292 on 2008-07-16
Hello,

ive used ndiswrapper on many differnt distros but this is a new problem for me.

1.downloaded appropriate driver and extracted
2.installed ndiswrapper
3.blacklisted bcm43xx driver
4.ndiswrapper -l and nothing listed
5.ndiswrapper -i bcmwl5.inf gave following error

/etc/ndiswrapper/bcmwl5: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194.

it's a broadcom wireless on a hp dv6326us laptop. im running 8.04

here is entry in lspci
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 

ive done this so many time before i don't know what could have went wrong. but i am pretty new with ubuntu.

any ideas

---

### Post by prc292 on 2008-07-16
just thought id update. found a thread that said i should do

apt-get build-essentials

although that did download and install it did not help

their is no driver installed in ndiswrapper that is to say when i type

ndiswrapper -l 

nothing happens it goes right back to the normal prompt

obviously missed something or something or a package i need is missing. 

hope someone can offer a suggestion

thx

---

