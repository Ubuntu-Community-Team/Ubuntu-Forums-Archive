---
title: "Ubuntu 14.04 Cannot reconnect to WPS2 Enterprise"
date: 2015-03-17
forum: Networking &amp; Wireless
---

### Post by abishur on 2015-03-17
Every day when I come into work I cannot reconnect to the WPA2 enterprise network.  I have to remove the saved access point name, and re-add it from scratch.  If I just click on the name of the network, it will sit there spinning forever but never pop up a dialog box for me to enter the security information for the network so I have to add it as a "hidden network".  I didn't used to have the problem, and I think it started after the last time the wireless driver was updated, but I've been out in the field so I can't confirm if that was the direct cause or a coincidence.

Every time I disconnect from the network I have to go back through all the steps of re-adding the network from scratch.  We do not use a certificate with the network and I have tried adding the system-ca-cert=false line to my /etc/NetworkManager/system-connections/<access point name> but nothing seems to fix this issue.

---

