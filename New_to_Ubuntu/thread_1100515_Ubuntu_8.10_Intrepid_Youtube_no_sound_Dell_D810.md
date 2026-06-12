---
title: "Ubuntu 8.10 Intrepid Youtube no sound Dell D810"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Lan on 2009-03-19
**Dell Latitude D810**
[size=1]

Upgraded from 8.04 to 8.10:
Youtube = No sound

Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

lspci: audio

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


My Fix:

Upgraded flash to flash_player_10:

If it's installed:
sudo apt-get remove flashplugin-nonfree

Go to:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Get .deb for Ubuntu 8.04+

Open with: [GDebi package installer]

Works now.

Thanks[/size]

---

