---
title: "newbie; new dapper install on dell 745; no network"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by imagerodeo on 2007-01-10
I just installed on a dual-boot windows xp box. The only interface I'm seeing in ubuntu is "lo". I did *not* have the ethernet cable plugged in when I installed... fatal mistake? (When I boot into windows the network comes up fine w/ DHCP.)

Device (as reported by windows): Broadcom NetXtreme 57xx Gigabit controller

/etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

... and so forth...

sudo ifup -a
... snip ...
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
... snip ...

Any clues? Maybe my spanky new Dell Optiplex 745 is too new for dapper? Maybe I should scrub the disk and re-install w/ the network cable plugged in?

---

