---
title: "enp1s0 could not get dhcp ip"
date: 2017-09-26
forum: Networking &amp; Wireless
---

### Post by darkdemon2 on 2017-09-26
Hello :p I am new in using Ubuntu and i got a problem in it. I just installed ubuntu 16.04 and it could not get dhcp ip on the enp1s0. I have been tried several things but it can't overcome the problem. On the /etc/network/interfaces file i have added the dhcp on enp1s0 but my computer still could not get the ip. Even when I'm restart the network use /etc/init.d/networking restart it's failed because of timeout. And when I checked on it give information that it's failed to start raise network interfaces and networking.service: Start operation timed out. Terminating


Please is there someone that can help me?

---

### Post by ajgreeny on 2017-09-26
What does command **ifconfig** tell you?
Try ```
sudo systemctl start network-manager.service
``` or maybe change **start** to **restart**.

---

