---
title: "2 NIC configuration?"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by roots on 2007-07-06
hi there,

i got a notebook with both LAN and WLAN interface and wondered if it was possible to set these 2 up as follows:

(1) WLAN interface connecting to access point, which is hooked to a linux DSLrouter serving a small LAN with internet connection
(2) LAN interface connected DIRECTLY (crossed cable) to another box, serving only my notebook

am i supposed to encounter any severe problems to get this setup to work, that is, both interfaces/connections at the same time?

all my boxes are running dapper drake.


cheers,
roots.

---

### Post by spd106 on 2007-07-07
I recommend that you upgrade the laptop to Ubuntu 7.04 (Feisty) as it has Network Manager installed by default and that uses roaming mode, which will make your task easier. You can also install it on Ubuntu 6.06 (Dapper) though it is less integrated.

As long as you can use DHCP for both connections you should have little problem switching between. The AP should have this all set up by default, but the cross-over connection using ICS won't. May I recommend these two wiki pages for setting up the ICS box.
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

