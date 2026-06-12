---
title: "mysqld failed to start after going fro wired to wireless connection"
date: 2015-10-16
forum: Networking &amp; Wireless
---

### Post by crcarson on 2015-10-16
Have a running mysql server running 15.04 that was connected via ethernet (eno1).  Changed the configuration to wireless (wlp5s0) and the mysql daemon fails to start on boot.  Issuing a "sudo systemctl restart mysql" correctly starts the daemon.  Appears that systemd is starting the mysql.service before the wireless network is available and this causes the daemon start process to fail.  The mysql.service file in /lib/systemd/system has an "after network.target" which is does not allow mysql.service to delay enough.  Changed that line in mysql.service to "after network-online.target" and now on boot then mysql daemon is up and available.

Built a distribution level of 15.10 and changing the "after network.target" to "after network-online.target" doesn't work unless you enable Network Manager wait with the command

systemctl enable NetworkManager-wait-online.service

The systemd boot journal shows that without this enable the network.target and network-online.target occur at the same time, well before the wireless IP address is up and available.
This causes the start of mysqld to fail.

---

