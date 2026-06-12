---
title: "Keeping resolv.conf with dhcp"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by CptPicard on 2007-06-11
This is an old problem that I've had since I started with (K)Ubuntu at Dapper, and there are old threads discussing the issue, but I didn't want to necro an old thread as I'd like to hear what the current status of this is, as I see I'm still struggling after an upgrade to Feisty...

For some reason Ubuntu has never liked my ADSL router boxes' DNS relay server -- I've had several of them, currently an A-Link, and Ubuntu is the only OS (and only Linux distro) that has ever had any trouble. When DHCP gives DNS server as 10.0.0.2, initial, non-cached DNS lookups are dog slow.

Certainly I can plug my ISPs name servers manually into resolv.conf, but then it gets regularly overwritten with 10.0.0.2, and I lose my settings. None of the solutions I've found here on the forums have been quite satisfactory -- the one about prepend-name-servers in dhclient.conf seemed promising (and "correct") at first, but it seems to write the correct IPs just at network start -- when the DHCP lease gets renewed, I get the wrong kind of resolv.conf again, no matter what it says in the config file.

Certainly I can pull off some ugly hack like I've always done like commenting out the make_resolv_conf() function in the dhclient script, or making resolv.conf read-only, or trying using static IPs, but I really feel like there has to be a better way... especially when Ubuntu is so user-friendly otherwise. This is such basic functionality I wonder why n00bs aren't stumbling on it ... or do they simply not notice? :confused:

So... what do you guys do to either get to keep your DNS servers in resolv.conf, or alternatively to make resolution through the ADSL router faster?

---

### Post by bluetracer on 2007-06-19
Bump.

I also have this issue with slow dns lookups using my Netgear router's dns server, and would therefore like to do the same thing as the OP.  Anyone?

---

### Post by ubernoob on 2008-02-16
In case someone else comes over this thread:

you can edit /etc/dhcp3/dhcpclient.conf and set "supersede domain-name-servers 10.0.0.1;"

But it is probably the network manager in gnome that resets it for you. So you have to fix it there somehow.

---

