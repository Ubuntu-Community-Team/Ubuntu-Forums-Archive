---
title: "Network just hangs after 1-2 days"
date: 2016-11-24
forum: Networking &amp; Wireless
---

### Post by cristi2k on 2016-11-24
Hello guys im runing a home media server on ubuntu 16. Randomly to me , the network just hangs and i need to reboot the system or use network-manager restart in order to reconnect the wired networking . Where should i start from ? Server runs utserver , plex and samba sharing.

---

### Post by ian-weisser on 2016-11-25
Neither utserver nor plex are community-supported Ubuntu packages, so the support you will get here may be quite limited.

Since you know the problem is with your server, try restarting one application at a time until you discover which one has a full connection cache. Then reduce it's max number of connections.

---

