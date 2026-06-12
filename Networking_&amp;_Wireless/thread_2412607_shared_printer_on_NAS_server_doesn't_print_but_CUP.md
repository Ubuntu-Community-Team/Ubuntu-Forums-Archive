---
title: "shared printer on NAS server doesn't print but CUPS web interface prints"
date: 2019-02-15
forum: Networking &amp; Wireless
---

### Post by philboo on 2019-02-15
Hi,
I have a problem with my printer : I bought a NAS server which has two USB connectors to share printer over the network. I have two PC on the network. For both PC's I got problems to get them printing on the shared printer. The CUPS interface prints well the test page (thus connection OK, IP OK, ...) but the test page from printer window on each PC doesn't print. 
Yesterday after multiple attempts and config changes on one PC I had succeeded to print, but I don't know why because the parameters were identical ! The problem is today it doesn't work any longer ! ????

---

### Post by philboo on 2019-02-15
I Found the solution : I had several lines "Listen..." in the /etc/cups/cupsd.conf after the instruction "Port 631" . 
Following [http://chschneider.eu/linux/server/cups.shtml](http://chschneider.eu/linux/server/cups.shtml),  when changing the config, you have to replace the "Listen" lines
After suppressing those lines coming from a previous config or my trials, it was printing fine again.

That means that when changing the config, the old config are not automatically deleted, and it's a good idea to go and check the config file.

---

