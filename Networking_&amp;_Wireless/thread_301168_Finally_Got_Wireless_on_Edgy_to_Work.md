---
title: "Finally Got Wireless on Edgy to Work"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by rvickers on 2006-11-16
I finally after a full week of trying got wireless to work and it was so simple.
1 - do an iwlist scan and get the essid of the wireless access point
2 - sudo ifconfig eth1 down
2 - completely wipe out the contents of /etc/network/interfaces. (sudo nano /etc/network/interfaces)
3 - System -> networks and configure the wireless with the essid and dhcp.

... update ...
rebooted and ubuntu reconfig'd the /etc/network/interfaces file and I had to wipe it out again, wonder if there's away to prevent that?

Tomorrow, I'll push the envelope and reconfigure for the wireless at work that uses a static IP and a WEP key :rolleyes:

... update ...
I performed 1,2,3,4 with a static ip, WIP(HEX) and it worked. However, after about 5 min of inactivity it won't connect. The solution is to go to System->Networks uncheck and check the checkbox and it comes right up. Not great but useable...

Hope this helps someone connect...

---

