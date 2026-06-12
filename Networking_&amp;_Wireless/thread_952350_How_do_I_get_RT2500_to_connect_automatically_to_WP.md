---
title: "How do I get RT2500 to connect automatically to WPA-PSK at boot"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by mishad on 2008-10-19
H/W: Dell Latitude M233 (233MHz P-MMX, 128MB) with Comtrend RT2500 PCMCIA and no wired network card
OS: Ubuntu 8.04-1 Server (plus LXDE & SLiM, but problem existed before they were installed)

Using /etc/network/interfaces [1] rather than Network Manager/Wicd to minimise overheads on this low-spec machine.

Network is configured and works when brought up manually with sudo ifup wlan0. 
But when I reboot, the connection doesn't come up properly -- get "network unreachable" when trying to connect. sudo ifdown wlan0 ; sudo ifup wlan0 fixes the problem.

Obviously I could add ifdown & ifup commands to rc.local, but I want to fix it "properly" (partly because I'm also trying to speed up the long boot time on this old machine, and bringing up the wifi twice isn't going to help!)

/var/syslog shows that during boot the DHCP failed with "no DHCPOFFERS received" on wlan0. bootchart shows that, after the modprobes, ifup ran (via sh, run_parts) wpasupplicant & wpa_supplicant, then dhclient3, dhclient-script, and sleep.

Any ideas?

[1] /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid xxxxx
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk xxxxxxxxxxx

---

