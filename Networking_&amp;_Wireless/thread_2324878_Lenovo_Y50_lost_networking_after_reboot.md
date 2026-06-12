---
title: "Lenovo Y50 lost networking after reboot"
date: 2016-05-17
forum: Networking &amp; Wireless
---

### Post by sijodk on 2016-05-17
[FONT=arial]Been running 14.04 LTS on my work laptop, a Lenovo Y50 for a few months without problems. I normally run it for a work week, suspending to RAM at night, and shutting down on Friday.

This morning when I powered it up I found that networking was gone. Tried a reboot (can't hurt, right?) which didn't help. Remembered that I ran some updates last week before powering down so tried booting an earlier Kernel; this also did not bring networking back.

ifconfig only finds the lo interface, iwconfig fares slightly better and correctly identifies eth0 as having no wireless extensions, and it finds wlan0. Going to System Settings -> Network I get a popup stating that "The system network services are not compatible with this version."

Anybody else seen anything like this?
[/FONT]

---

### Post by sijodk on 2016-05-17
Also, this:
```

$ dmesg | grep -i net
[    0.029336] Initializing cgroup subsys net_cls
[    0.029345] Initializing cgroup subsys net_prio
[    0.198431] NET: Registered protocol family 16
[    0.417986] NetLabel: Initializing
[    0.417987] NetLabel:  domain hash size = 128
[    0.417987] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.417997] NetLabel:  unlabeled traffic allowed by default
[    0.478757] NET: Registered protocol family 2
[    0.479368] NET: Registered protocol family 1
[    3.938769] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.939092] audit: initializing netlink subsys (disabled)
[    4.113404] NET: Registered protocol family 10
[    4.113661] NET: Registered protocol family 17
[    4.146437] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.860592] audit: type=1400 audit(1463469059.236:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[    4.861006] audit: type=1400 audit(1463469059.236:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[    5.141076] NET: Registered protocol family 31
[    5.144950] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.156753] init: network-manager main process (838) killed by SEGV signal
[    5.156763] init: network-manager main process ended, respawning
[    5.166745] init: network-manager main process (862) killed by SEGV signal
[    5.166751] init: network-manager main process ended, respawning
[    5.172966] init: network-manager main process (866) killed by SEGV signal
[    5.172972] init: network-manager main process ended, respawning
[    5.179353] init: network-manager main process (870) killed by SEGV signal
[    5.179359] init: network-manager main process ended, respawning
[    5.185986] init: network-manager main process (877) killed by SEGV signal
[    5.185992] init: network-manager main process ended, respawning
[    5.191633] init: network-manager main process (881) killed by SEGV signal
[    5.191640] init: network-manager main process ended, respawning
[    5.197273] init: network-manager main process (885) killed by SEGV signal
[    5.197279] init: network-manager main process ended, respawning
[    5.203168] init: network-manager main process (889) killed by SEGV signal
[    5.203176] init: network-manager main process ended, respawning
[    5.209889] init: network-manager main process (901) killed by SEGV signal
[    5.209896] init: network-manager main process ended, respawning
[    5.215178] init: network-manager main process (905) killed by SEGV signal
[    5.215184] init: network-manager main process ended, respawning
[    5.220749] init: network-manager main process (909) killed by SEGV signal
[    5.220755] init: network-manager respawning too fast, stopped
[   22.435563] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev- instead.






```

---

### Post by sijodk on 2016-05-17
Should anybody else experience similar problems I found the solution here:

[http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet](http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet)

---

