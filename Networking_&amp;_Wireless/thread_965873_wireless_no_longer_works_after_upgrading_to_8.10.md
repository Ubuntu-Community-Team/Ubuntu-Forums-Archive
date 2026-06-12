---
title: "wireless no longer works after upgrading to 8.10"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by EmeraldGreen on 2008-10-31
I upgraded my desktop to Ubuntu 8.10 yesterday. Everything seemed to go well, but when I logged in the network manager asked me for my wireless network key. The new network manager apparently no longer accepts WEP keys in hex format, and it refused to connect when I entered the key itself. I tried connecting through the command-line using this guide [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html) but dhclient did not receive any offers.

I changed the network security on the router to WPA (I'd been meaning to do that for ages anyway, but never got round to it). All the Windows computers in the house connected successfully with the new security, and so did my laptop, which runs Ubuntu 8.04, but my desktop with Ubuntu 8.10 still refuses to connect. I tried the Ubuntu Geek guide again, with the same result as before - no offers.

Any ideas? My desktop is much too far from the router for a wired connection to be an option, so until I can get this fixed I'm going to be stuck using my laptop or (heaven forbid) Windows...

---

### Post by EmeraldGreen on 2008-10-31
Well, it looks like it's fixed itself... I don't know how, but it's working now...

---

