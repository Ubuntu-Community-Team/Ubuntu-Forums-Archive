---
title: "Avahi not starting with 8.10"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by hjlane3 on 2008-11-01
Ever since installing 8.10, I haven't been getting automically assigned IPs with avahi when IP from DNS fails (as I use wired port for direct connect to another computer). 

I can manually run avahi-autoipd and it works perfectly, but it's not doing so automatically.

I set my wired device as Link Local with network-manager, and this occurs in syslog:

Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Nov  1 13:13:08 philia NetworkManager: <info>  (eth0): device state change: 3 -> 4
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov  1 13:13:08 philia NetworkManager: <info>  (eth0): device state change: 4 -> 5
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov  1 13:13:08 philia NetworkManager: <info>  (eth0): device state change: 5 -> 7
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started avahi-autoipd...
Nov  1 13:13:08 philia NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov  1 13:13:28 philia NetworkManager: <info>  eth0: avahi-autoipd timed out.
Nov  1 13:13:28 philia NetworkManager: <debug> [1225559608.982397] aipd_cleanup(): waiting for ppp pid 7396 to exit
Nov  1 13:13:28 philia NetworkManager: <debug> [1225559608.994576] aipd_cleanup(): ppp pid 7396 cleaned up
Nov  1 13:13:28 philia NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled...
Nov  1 13:13:28 philia NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started...
Nov  1 13:13:28 philia NetworkManager: <info>  (eth0): device state change: 7 -> 9
Nov  1 13:13:28 philia NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Nov  1 13:13:28 philia NetworkManager: <info>  Activation (eth0) failed.
Nov  1 13:13:28 philia NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete.
Nov  1 13:13:28 philia NetworkManager: <info>  (eth0): device state change: 9 -> 3
Nov  1 13:13:28 philia NetworkManager: <info>  (eth0): deactivating device (reason: 0).

For some reason avahi-autoipd is timing out when getting called by networkmanager.

I found a bug report, [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/25690](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/25690) 

But seeing the general lack of attention to it (other than the creator's back in August, and mine just an hour ago), 

Anyone have any ideas that could help me pinpoint the trouble? Thanks!

---

