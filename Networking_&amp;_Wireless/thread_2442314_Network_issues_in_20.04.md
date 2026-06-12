---
title: "Network issues in 20.04"
date: 2020-05-02
forum: Networking &amp; Wireless
---

### Post by speartip on 2020-05-02
This is happening across all the latest 'buntus. My network is using the rt2800pci driver. All has been well in previous editions. But now my network connection speed is all over the place, cutting out or varying between 1mbps & 75mbps according to the connection information on the network icon. All other devices in the house are stable. Any ideas?

---

### Post by speartip on 2020-05-06
OK. After much Googling I finally nailed down the problem. Apparently Ubuntu resets the TLP configuration, & WiFi power management comes on. To rectify I edited the file,
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
and changed the value from 3 to 2, rebooted, and voila, problem solved.

---

