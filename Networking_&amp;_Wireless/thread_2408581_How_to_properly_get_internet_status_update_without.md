---
title: "How to properly get internet status update without network manager"
date: 2018-12-20
forum: Networking &amp; Wireless
---

### Post by niti19 on 2018-12-20
Hello All,

According to my application requirements, sometimes I need to switch between static ip & dhcp ip. I used to set static ip using /etc/network/interfaces, once I am unplugging & plugging internet cable, it is reverting to DHCP IP. So I have changed /etc/NetworkManager/NetworkManager.conf and set managed true, still problem is there.

Also I have tried to uninstall network manager completely, then every thing is working fine. But whenever I was in DHCP mode and restarts my computer without internet, internet is not resuming after timeout set in /etc/dhcp/dhclient.conf.

---

