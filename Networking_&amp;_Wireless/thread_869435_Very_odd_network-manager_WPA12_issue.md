---
title: "Very odd network-manager WPA1/2 issue"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Malviolent on 2008-07-24
Alright, so I've tried many things to get my wireless working.  I have an Atheros card and I'm currently messing with the madwifi drivers, and I have successfully installed them.  Now, I can iwlist scan and pick up wireless access points, which is awesome.

However, I cannot connect to any of them!  I currently have my network manager set up to connect to a WPA2 network with a static IP address (as I've read DHCP doesn't work well with WPA2 & madwifi).

The strange problem is that, when I set up network manager as WPA2, I'll save my settings and have no access.  When I go back to edit that same configuration, network manager saved it as WPA and not WPA2!  I can't seem to get it to save as WPA2!

---

### Post by DapperMe17 on 2008-07-24
Download Wicd, from the repositories. It's a great tool that "should" help your cause.

---

### Post by Malviolent on 2008-07-24
thanks but I already tried using wicd, and it picks up networks but does not connect to any of them.  I've switched to trying out madwifi and network manager hoping I can get some success.

---

