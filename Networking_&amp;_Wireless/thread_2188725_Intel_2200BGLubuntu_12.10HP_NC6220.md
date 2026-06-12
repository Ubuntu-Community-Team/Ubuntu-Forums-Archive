---
title: "Intel 2200BG/Lubuntu 12.10/HP NC6220"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by Farfrae on 2013-11-18
[FONT=Verdana]
I have used this machine with Lubuntu using WiFI perfectly for a couple of years, normally on the latest version available. I upgraded to 13.10 last week. [/FONT]

[FONT=Verdana]I have since found that the wireless is intermittent at best - occasionally on and working for a couple of minutes, but mostly showing "wireless is disconnected by wireless switch", or not even giving an option to enable Wifi. If I unblock with rfkill it might work after a reboot, but the whole computer will freeze and require powering off after a minute or two. Even if it is showing as not working, there will be random freezes, freezes at reboot and sometimes won't even reach the ROM setup HP logo without removing and reconnecting the battery.[/FONT]

[FONT=Verdana]When the computer is wired to the router all is fine. Perfect internet, no freezes, all well. As soon as it is disconnected, trouble will begin. I have tried various options in ROM set-up with LAN power saving and LAN/WLAN switching but nothing cures the problem.[/FONT]

[FONT=Verdana]I have tried a clean install of Lubuntu for 13.10, and 12.04 (then upgraded to 12.10). and this did not cure the problem.[/FONT]

[FONT=Verdana]Does anyone have any possible solution before I rip it apart to check the hardware (or get a new laptop).[/FONT]

[FONT=Verdana]HP NC6220 with 2GB RAM.[/FONT]

[FONT=Verdana]$lspci:[/FONT]

[FONT=Verdana]02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)[/FONT]

[FONT=Verdana]$iwconfig:[/FONT]

[FONT=Verdana]lo        no wireless extensions.[/FONT]

[FONT=Verdana]eth0      no wireless extensions.[/FONT]

[FONT=Verdana]eth1      IEEE 802.11bg  ESSID:  off/any  [/FONT]
[FONT=Verdana]         Mode:Managed  Channel:0  Access Point: Not-Associated   [/FONT]
[FONT=Verdana]         Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  [/FONT]
[FONT=Verdana]         Retry limit:7   RTS thr:  off   Fragment thr:  off[/FONT]
[FONT=Verdana]         Power Management:  off[/FONT]
[FONT=Verdana]         Link Quality:0  Signal level:0  Noise level:0[/FONT]
[FONT=Verdana]         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/FONT]
[FONT=Verdana]         Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT]


[FONT=Verdana]$ lsmod | grep "ipw2200":[/FONT]

[FONT=Verdana]ipw2200               140514  0 [/FONT]
[FONT=Verdana]libipw                 46389  1 ipw2200[/FONT]
[FONT=Verdana]cfg80211              175574  2 ipw2200,libipw[/FONT]
[FONT=Verdana]lib80211               14041  2 ipw2200,libipw[/FONT]

[FONT=Verdana]$ dmesg | grep "ipw2200":[/FONT]

[FONT=Verdana][   20.027536] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq[/FONT]
[FONT=Verdana][   20.027539] ipw2200: Copyright(c) 2003-2006 Intel Corporation[/FONT]



[FONT=Verdana]$ sudo lshw -C network:[/FONT]

[FONT=Verdana]*-network               [/FONT]
[FONT=Verdana]       description: Ethernet interface[/FONT]
[FONT=Verdana]       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express[/FONT]
[FONT=Verdana]       vendor: Broadcom Corporation[/FONT]
[FONT=Verdana]       physical id: 0[/FONT]
[FONT=Verdana]       bus info: pci@0000:10:00.0[/FONT]
[FONT=Verdana]       logical name: eth0[/FONT]
[FONT=Verdana]       version: 11[/FONT]
[FONT=Verdana]       serial: 00:12:79:be:10:0d[/FONT]
[FONT=Verdana]       size: 100Mbit/s[/FONT]
[FONT=Verdana]       capacity: 1Gbit/s[/FONT]
[FONT=Verdana]       width: 64 bits[/FONT]
[FONT=Verdana]       clock: 33MHz[/FONT]
[FONT=Verdana]       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT]
[FONT=Verdana]       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=5751m-v3.29a ip=192.168.1.75 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s[/FONT]
[FONT=Verdana]       resources: irq:16 memory:d0000000-d000ffff[/FONT]

[FONT=Verdana]uname -mr:[/FONT]
[FONT=Verdana]3.5.0-43-generic i686[/FONT]


[FONT=Verdana]Please let me know if you need any more. Thank you to anyone who can help.[/FONT]

[FONT=Verdana]Thanks[/FONT]

[FONT=Verdana]Andrew[/FONT]

---

