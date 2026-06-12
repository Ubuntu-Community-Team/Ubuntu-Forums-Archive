---
title: "pNFS block"
date: 2017-06-23
forum: Networking &amp; Wireless
---

### Post by zkab on 2017-06-23
After upgrading to 4.8.0-56 (Ubuntu 16.04.2 LTS server) I have following in dmesg ...

jurka@farbaute:~$ dmesg | grep -i depe
[    8.302701] systemd[1]: Dependency failed for pNFS block layout mapping daemon.
[    8.302765] systemd[1]: nfs-blkmap.service: Job nfs-blkmap.service/start failed with result 'dependency'.

What is wrong ?

---

