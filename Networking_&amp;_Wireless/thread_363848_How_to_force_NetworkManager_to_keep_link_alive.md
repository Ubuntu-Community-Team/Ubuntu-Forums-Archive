---
title: "How to force NetworkManager to keep link alive"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by Martybartfast on 2007-02-17
Hi all,
  I'm using NetworkManager to manage my home wireless connection and on the whole it works fine. Occasionally it will lose/drop the connection and I can get it back by clicking the nm-applet icon on the taskbar and choosing my network. My network is WPA encrypted and there aren't usually any other connections in range.

My problem is that sometimes I leave the laptop on overnight to do some stuff (rsync to another pc, update tools...etc.) but if the wireless drops I'm not around to reconnect, so is there a way of either telling NetworkManager to keep trying to re-establish the connection if it goes down, or is there something I can do from a command line in a cron job to tell it to re-establish a connection (I don't have a problem writing a script to monitor the link, detect when it goes down and take appropriate action).

TIA for any help, Martyn.

---

