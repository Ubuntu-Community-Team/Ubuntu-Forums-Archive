---
title: "HP NC364T Quad port ethernet card: Inconsistent port assignment at boot"
date: 2023-02-27
forum: Networking &amp; Wireless
---

### Post by drwizard2 on 2023-02-27
I have an old HP Z600 workstation I use as a home server.
The ethernet port on the motherboard is bad. The system recognizes it, but it won't actually communicate with the network. The system always sees it as eth0.
I installed an HP NC364T PCI Express Quad Port Gigabit Server Adapter. It was cheap used, it has 4 ports and someday I may wish to tinker with routing and firewalls, and being a server adapter much of the communication overhead is offloaded onto the card instead of the main CPU (not that there is really enough to worry about).
I have 2 problems, likely related.
First, when the system boots it always only recognizes 2 of the 4 ports. They become ens4f0 and ens4f1. I only need one (for now) so I don't care about that (for now). But---
Second, which of those 4 ports becomes ens4f0 and which of them becomes ens4f1 at boot time is totally random! Sometimes the one with the cable plugged in becomes 0, and sometimes it becomes 1, and since I configured both, if it happens to be 0 or 1 I can connect to the network.
However, sometimes the one with the cable plugged in becomes what would/should be 2 or 3 and when that happens I have no network connection. I have to keep rebooting until I get lucky! (or about 50% of the time).
**How can I fix this inconsistency?**
Clues: The card has two Intel 82571EB (e1000e) processors and is supposed to show up as 2 dual port ethernet adapters. Running lspci returns:
```
2a:00.0 Ethernet controller: Intel Corporation 82571EB/82571GB Gigabit Ethernet Controller (Copper) (rev 06)
2a:00.1 Ethernet controller: Intel Corporation 82571EB/82571GB Gigabit Ethernet Controller (Copper) (rev 06)
2b:00.0 Ethernet controller: Intel Corporation 82571EB/82571GB Gigabit Ethernet Controller (Copper) (rev 06)
2b:00.1 Ethernet controller: Intel Corporation 82571EB/82571GB Gigabit Ethernet Controller (Copper) (rev 06)
```
And when I check the logs I find this:
```
Feb 26 22:18:43 server kernel: e1000e 0000:2b:00.1 ens4f1: renamed from eth3
Feb 26 22:18:43 server kernel: e1000e 0000:2a:00.0 ens4f0: renamed from eth0
Feb 26 22:18:43 server systemd-udevd[467]: eth1: Failed to rename network interface 3 from 'eth1' to 'ens4f1': File exists
Feb 26 22:18:43 server systemd-udevd[463]: eth2: Failed to rename network interface 4 from 'eth2' to 'ens4f0': File exists
```
The driver according to ethtool is:
```



driver: e1000e
version: 3.2.6-k
firmware-version: 5.12-2
expansion-rom-version: 
bus-info: 0000:2b:00.1
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no
```

---

### Post by chili555 on 2023-02-27
We may find another clue in: ```
cat /etc/netplan/*.yaml
```

Please run and post.

---

