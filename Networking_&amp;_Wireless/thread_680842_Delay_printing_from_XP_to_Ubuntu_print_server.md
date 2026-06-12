---
title: "Delay printing from XP to Ubuntu print server"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by Mohonri on 2008-01-28
I've repurposed an old machine as a print server (for a color laserjet 4550) by following [this guide](https://help.ubuntu.com/community/NetworkPrintingFromWinXP), and once I sorted out a little watermarking issue, I can print across the network.  However, when I do a Ctrl-P on one of the other machines on the network (both XP, haven't tried the other Ubuntu box yet), there is a very long delay (approx 30sec) bringing up the Printing dialog box.  Once I hit Ok, sending the actual print job goes at a normal, reasonable speed.

The (new) print server is a Celeron 1GHz/384MB running Gutsy.  Yeah, I know it's a bit underpowered for a full Ubuntu install, but the memory usage at the desktop is well below the 384MB, and it's responsive enough for a local user, so CPU load isn't an issue either.  Until now, the printer was on another machine running Ubuntu (Sempron 2800, 768MB RAM), and there was no significant delay in bringing up the print dialog on the Windows boxes.

I also noticed that bringing up the http://<hostname>:631/printers/ page is very, very slow, similar to the print dialog.

Can someone tell me how I might fix this issue?  Thanks!

---

