---
title: "any alternative to hostapd or maybe a fix for it dying and being slow?"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by the_jlx on 2013-10-01
So i finally got Hostapd working but it takes up to 3 minutes at times for it to work and when it does it is REALLY slow the information tab was saying 1 to 5 MB/s alternatingly but actual speed maybe 10Kb/s to 100Kb/s.....
and there is no telling how long it stays up  it just dies silently in the background.
i need the main computer to be a acces point 24/7/365
and haven't bothered with this problem earlier as my swinedows was still in working order and all that required was ```
netsh wlan start hostednetwork
```
but since it died and i am in no mood of resurrecting that horribad os i decided to give Linux a go again.
config --->
```

[HOSTAPD]
rsn_pairwise = CCMP
ssid = lol
macaddr_acl = 0
SCRIPT = scripts/hostapd
driver = nl80211
OUTPUT_CONFIG = /etc/py_hostapd.conf
wpa_key_mgmt = WPA-PSK
EXIT_SCRIPT = scripts/hostapd_exit
auth_algs = 1
wpa_passphrase = 1234554321
ignore_broadcast_ssid = 0
hw_mode = g
wpa_pairwise = TKIP
LOGFILE = logs/hostapd
interface = wlan0
wpa = 3
channel = 6

[DHCP]
ip_router = 10.0.0.1
ip_range_min = 10.0.0.3
ip_netmask = 255.255.255.0
ip_subnet = 10.0.0.0
SCRIPT = scripts/dhcpd
OUTPUT_CONFIG = /etc/py_dhcpd.conf
ip_range_max = 10.0.0.12
TEMPLATE_CONFIG = templates/dhcpd
ip_broadcast = 10.0.0.255
dns_1 = 8.8.8.8
dns_2 = 8.8.4.4
LOGFILE = logs/dhcpd
EXIT_SCRIPT = scripts/dhcpd_exit

[NAT]
LOGFILE = logs/nat
SCRIPT = scripts/nat

[GENERAL]
SCRIPT = scripts/init
ip_wlan = 10.0.0.1
netmask = 255.255.255.0
in = wlan0
LOGFILE = logs/init
out = ppp0

```

this might have something to do with the dying thou
```

[ 1903.212779] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct  1 09:31:18 desktop kernel: [ 1903.212944] hostapd[5061]: segfault at 10 ip 0000000000410290 sp 00007fffb1af6970 error 4 in hostapd[400000+d0000]
```

Any help or suggestions would be greatly appreciated.

---

