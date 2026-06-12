---
title: "DLNA network oddity"
date: 2020-11-14
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2020-11-14
Folks,

This is not Ubuntu related so I hope no-one minds my asking this question.

My main system is Ubuntu 18:04 running on a Toshiba laptop.  I also occasionally run Debian, Mate and Arch on an external disk.

Now to my issue;  I run miniDLNA on two different Raspberry Pi devices plus I have a media server on my TP-Link router (experimenting, not really useful).

All these servers show fine on VLC running on Linux (all systems), Windows and Android but do not show on VLC on Firestick.  Here is the odd bit, if on my Raspberry Pi I restart miniDLNA using systemctl they then show up on the Firestick VLC - but only if I have the browse local network option open.  If I navigate away from that folder then return the DLNA links have disappeared.

VLC is fine on every system except Firestick, anyone any suggestions as to why this might be?

Geoff

---

### Post by Geoff_Lane on 2020-11-16
For anyone who may have a similar problem my system is now working perfectly.

Bearing in mind I have two separate Pi devices running miniDLNA and a router running a media server and none were showing on the firestick I altered just one setting in the /etc/minidlna.conf file of just one Pi and strangely all, including the router now show.

tivo_discovery=bonjour is the default, I changed to tivo_discovery=beacon and all now works.

Geoff

---

