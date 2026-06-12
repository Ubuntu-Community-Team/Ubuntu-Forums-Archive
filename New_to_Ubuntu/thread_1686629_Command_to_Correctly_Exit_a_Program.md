---
title: "Command to Correctly Exit a Program"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by dalekirkwood on 2011-02-12
Hi All,

Basically I download using a P2P but my ISP only gives me unlimited download between 12pm and 8am so I use Gnome Schedule 2.1.1 to run qBittorrent at 11:59pm and then use the command 'killall qbittorrent' to close it at 7:59am but it regularly freezes and when I reload qBittorrent it has to check all the files. What would be the correct command to close qbittorrent so it can do a legal proper shut down. 

Thanks

---

### Post by dalekirkwood on 2011-02-12
Just found a way of doing it I installed wmctrl using apt-get and then used the command 'wmctrl -c  qbittorrent' :-)

---

