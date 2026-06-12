---
title: "no internet connection"
date: 2018-03-23
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-03-23
I am running Ubuntu server.  In my interfaces file, I've tried for my external facing nic card to pull an address via dhcp, which fails.  I've attached my router to my modem, and it pulls an ip just fine (and internet works).  So I assigned the static info to the external interface, and it still won't work.  What could be causing it to not work on the server?

---

### Post by TheFu on 2018-03-24
Rather than trying to describe the issues, please provide some facts:
```
more /etc/lsb*
ifconfig
more /etc/network/interfaces
sudo lshw -C network
route -n
ping {router by IP address}  # replace with YOUR router IP.
ping 8.8.8.8
ping google.com
```
Please use code tags like I have, so things line up. Include the command AND the output.

---

