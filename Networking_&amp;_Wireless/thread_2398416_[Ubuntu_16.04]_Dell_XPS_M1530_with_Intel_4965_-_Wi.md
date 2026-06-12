---
title: "[Ubuntu 16.04] Dell XPS M1530 with Intel 4965 - Wireless off"
date: 2018-08-11
forum: Networking &amp; Wireless
---

### Post by jbontke on 2018-08-11
I have a dell XPS M1530 that I have been trying to get the wireless workin on. I am stuck after reading other posts with the same wireless card, I have had no luck. It is as if the wireless card is shutoff, but there is not switch to turn it on. Can anyone offer suggestions?


wireless-info
[http://paste.ubuntu.com/p/tjtb9RhHfB/](http://paste.ubuntu.com/p/tjtb9RhHfB/)


Thanks!

---

### Post by chili555 on 2018-08-11
Please run these terminal commands:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo service network-manager restart
```Detach the ethernet and tell us if the interface sees networks:```
sudo iwlist scan
```If not, what is the message that results?

---

