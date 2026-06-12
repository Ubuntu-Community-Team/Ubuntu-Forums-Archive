---
title: "pptp dropout issues"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by KCormier on 2008-10-16
Howdy everyone.

In order to connect to my network at school I'm forced to vpn in order to get a connection to the outside world.  My windows machines work fine but none of my ubuntu installs can successfully vpn out.

All ubuntu machines are 8.04 with all the latest updates.  i have the pptp plugin for the network manager and i can configure it and connect with it.  whenever i try to load a webpage or download a file it'll connect and begin the download but it never finishes.  I don't know if it times out or what's going wrong but every connection i make only downloads a small amount and then stops.  Has anyone heard of a similar issue? 

-Kevin

---

### Post by john_navarro on 2008-11-05
I experience the same issue - I'm using Intrepid 64-bit. Although this tip won't fix the disconnections, it should help performance. nm-applet 0.66 had a default MTU of 1416 - but with nm-applet 0.70 the value is 1500. The performance issue comes from a high rate of retransmits. Check out /var/log/syslog and you'll see the error messages if the MTU is the problem.

Anyhow, try this - it might help performance:
```
sudo ifconfig ppp0 mtu 1416
```

Issue that command after the tunnel has been established.

---

