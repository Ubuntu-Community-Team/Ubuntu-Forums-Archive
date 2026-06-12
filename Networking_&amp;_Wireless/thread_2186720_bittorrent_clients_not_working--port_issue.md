---
title: "bittorrent clients not working--port issue?"
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by pedal2 on 2013-11-08
I have been using Transmission successfully and with no problems for years, until yesterday when it just stopped downloading anything.  There are plenty of seeders and few leechers on the torrents I'm trying to download (over 1000 seeders, about 100 leechers).  That is not the issue.  I've tried downloading a wide variety of torrents but nothing even tries to connect to peers.  I downloaded Deluge and get the same results--absolutely nothing happening.  In Deluge I went to Preferences-Network and then clicked the "test active port" button (ports are set to "random"--Deluge default) and a little red circle with an exclamation point comes up.  So, it seems like the port is not open.  I have Comcast as my isp, and earlier this week we had to change out the modem and router for a new Comcast modem/router combo.  The internet works great, and I think I've downloaded a torrent since the switch but can't be sure.  From reading it looks like ISPs can block torrents.  How can I check for this and bypass their security, if this is the problem?  Could it be a different thing?  Thanks,

            Tomas

---

### Post by pedal2 on 2013-11-08
bump.  Could really use some help on this.  I've read lot's of other threads here and elsewhere about similar problems but can't figure out how to fix this issue.

---

### Post by utkjamie on 2013-11-13
The problem might be with libtorrent, which I believe Transmission, Deluge and some other torrent apps use. I've experienced similar problems and the Deluge forums led me to believe the problem had something to do with libtorrent.

---

