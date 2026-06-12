---
title: "MTU and VPN issues"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by rksite on 2006-12-16
After many hours I figured out that the don't fragment bit is getting set on my interface.  If I ifconfig eth1 mtu 1300 then everything works with my cisco VPN.  I am using WPA and have my wireles device commented out of my interfaces file.  This is the only way I know how to get WPA to work.  Does any one know where I can clear the DF bit issue or change the MTU other then the interface file?

---

