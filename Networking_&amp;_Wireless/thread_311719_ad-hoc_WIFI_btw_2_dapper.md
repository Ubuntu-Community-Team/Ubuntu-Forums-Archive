---
title: "ad-hoc WIFI btw 2 dapper"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by raphaelk on 2006-12-03
Hello guys !

I have 2 computers : on desktop with a D-link DWL-G122 wifi usb key (rt2550 drivers) and a laptop DELL D600 with intel pro wireless chipset.

I'm trying to set up an wifi ad-hoc connection between both computers :

on the desktop, i'm typing this command :
iwconfig rausb0 essid "myEssid" mode Ad-Hoc

The IP adress of rausb0 interface is set manually (192.168.1.1)

on the laptop, I'm typing the same command : iwconfig eth1 essid "myEssid" mode Ad-Hoc.
the IP is set manually too (192.168.1.2)

when I try to ping .1 from the laptop, I have an network unreachable. Same from the desktop with .2

any idea ? ](*,) 

Raphael.

---

### Post by ofehmi on 2006-12-06
first install wifi manager
if wifi manager defines signal you are lucky
then on wifi manager edit settings and save

network name:yours
key :your key
manage must be ad-hoc

ip may be dhcp or manual
after saving settings connect ad-hoc network

---

