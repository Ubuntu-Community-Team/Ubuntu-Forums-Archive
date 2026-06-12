---
title: "[SOLVED] Newbie: 3G Connection Disconnects Immediately"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by supergrover1981 on 2008-11-20
Hi gang,

I'm trying to set up a 3G connection in Intrepid - having a few problems. I'm very new to 3G connections and unsure how to diagnose what's going wrong. Most of all, I'm trying to figure out whether it's the modem/driver or the connection settings causing the problem. Any help most appreciated.

Modem/connection has been tested in XP, all works fine. Modem is a Sierra 885, trying to connect to (Australian) Telstra NextG (HSUPA) network.

Here's my process:

1.) Setup a Telstra 3G Connection in Network Manager-->Edit connections. Current specs are: phone #: *99#  APN: telstra.wap, telstra.internet, telstra.datapack (tried all 3...telstra.internet works in XP). No username/password necessary

2.) Modem did not show up in Network Manager. Added modems.fdi as detailed in [http://ubuntuforums.org/showthread.php?t=946379&highlight=sierra+885](http://ubuntuforums.org/showthread.php?t=946379&highlight=sierra+885). The 3G connection established in (1) now shows up when the modem is in the PC

3.) Upon clicking the 3G connection in network manager, a notification bubble comes up saying "The network connection has been disconnected". This happens almost immediately after clicking to connect - about 0.1 seconds after.

Any suggestions most appreciated. The modem *may* be locked to the Telstra network - could that block Linux OS somehow?

Any help most appreciated.

Cheers,
        - JB

---

### Post by supergrover1981 on 2008-11-22
New guide at [http://sierrawireless.custhelp.com/app/answers/detail/a_id/500](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500) worked for me, the older ones didn't. resolv.conf fixed the problem. Still need to connect through pppd. :-)

---

