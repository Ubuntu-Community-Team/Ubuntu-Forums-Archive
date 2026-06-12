---
title: "Bandwidth Management"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by prodezigner on 2007-11-09
I turned an old HP Pavilion 7955 into a server (LAMP + TorrentFlux + SAMBA (SWAT Managed) + SSH) and I was wondering if I could set it up so that when torrents are downloading/seeding if I could have the full 10/100 on my network (with a different card). Everything is running fine, I've just always had slow transfers via SAMBA the entire time I've used it.

HP SPECS:
Pentium 4 1.5Ghz
512MB RAM
ATI Radeon 9200SE
20GB - OS / APPS
40GB - Storage
DVD-ROM
CD-Burner (anyway to make this web-based for backups?)
10/100 integrated

It's also headless. Two cords total, AC and CAT5.

---

### Post by mpierce on 2007-11-09
I use deluge as my client on linux and uTorrent on XP. In both, there is a way to configure so you can limit the amount of bandwidth used by the client or by the torrent that is downloading. 

Hope this helps...

---

### Post by prodezigner on 2007-11-09
Not quite... lol. I'm running Ubuntu 7.10 Server Edition, no GUI at all. I just use TorrentFlux for downloading, SWAT for SAMBA management, SSH for system management (headless) and Apache for a basic launchpad.

I guess my question wasn't all to clear however, as that wasn't the reply I was quite looking for.

Let me give you my internet setup.

5Mbs/256Kbs Cable (via NewWave Communications)

Digital Phone / Cable Modem -> Linksys WRT54GS A/B/G Wireless Router -> one computer direct connected, two laptops running wireless, one desktop running wireless -> 5-port hub (two to my computer, one to my fiance's computer, one gets the signal from the router) -> 5-port hub (printer, and linux box, one gets signal from hub #1)

Now... to rephrase my question. When I'm downloading, the 'INTRANET" has slow transfer speeds. Is there any way to speed up my network transfers while downloading? Maybe another NIC card setup somehow? SAMBA has just always seemed slow to me though...

---

### Post by Mithrilhall on 2007-11-09
trickle - user-space bandwidth shaper

And if you want a dedicated packet shaper I would recommend MasterShaper ([www.mastershaper.org](www.mastershaper.org)).

---

