---
title: "Network seems to sleep randomly after a seconds of inactivity"
date: 2020-07-02
forum: Networking &amp; Wireless
---

### Post by siegfred2 on 2020-07-02
I am currently setting up some raspberry pi 4 nodes with Ubuntu 20.04 server with wired ethernet.

Problem is after setting up static ip, by disabling cloud-init and then setting up netplan configs,
network seems to start sleeping every now and then.

For example, when connected via ssh, and then left for a few seconds/minutes, when i try to input, it momentary lags for a few seconds, then gets back to normal.

Another example is when i deploy a simple TCP web server, same thing happens, few minutes/seconds of inactivity causes next request to lag for a few seconds.

Note that this does not occur under fresh install with dhcp issued ip, i also tried reserving the IPs in my router to no avail.

Anyone has any idea why this happens?

---

