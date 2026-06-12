---
title: "DNS dies when downloading popular torrent"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by BrentNewland on 2008-10-27
I'm not sure what exactly is going on here, but when I download a popular **legal** torrent that has a lot of peers (more than a thousand), my DNS dies. The torrent activity still continues while any DNS lookups fail. Even after shutting off the torrent, and leaving it for a day, still dead.

I have a WRT54G router running DD-WRT v24 RC-5. When the problem occurs, I can still access the router, and the cable modem on the other side of the router, and other computers can still access the internet. When I attempt to connect to or ping/tracert/anything domains, it waits forever and says it can't resolve.

I have OpenDNS set for my DNS server (208.67.222.222, 208.67.220.220) followed by (4.2.2.1, 4.2.2.2). The problem goes away when I restart the computer.

I have tried ifdown eth0 ifup eth0 and these commands as well:
ifconfig eth0 down
route del default
ifconfig eth0 192.168.0.10 netmask 255.255.255.0
route add default gw 192.168.0.1

and none of them did squat. I also checked dmesg (dmesg | tail) and every log in /var/logs and I can't find a single entry related to this problem in any of the logs.


Does anyone have any ideas to try when this happens? Or is there a special log I can check to see if it has info on this problem?



BTW, has been happening since at least Hardy Heron (maybe Gutsy Gibbon), currently on Intrepid Ibex with latest updates, running QBittorrent.

---

### Post by BrentNewland on 2008-10-29
Anyone? I'm running apt-p2p to mirror the Intrepid debs and I'd hate to go down on launch day.

---

### Post by bionnaki on 2008-10-29
sounds more like a problem with your router and not ubuntu. I'd ask your firmware messageboard.

I'd also try reducing the amount of peers/connections in your client. you might be overloading your router.

---

