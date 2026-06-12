---
title: "WMP54G driver solution"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by harts12 on 2006-10-02
I just got my WMP54G card working, and it didn't take ndiswrapper. I followed the instructions here:
  [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500).
What actually made it work was putting in the ESSID and WEB Key, then adding the "auto ra0" to /etc/network/interfaces above the stanza beginning with "iface ra0" to make the network run on startup. Next I restarted my computer and it worked. If you are having problems try this.

---

