---
title: "[SOLVED] Clients on Server 8.04 WPA2 AP Can't Browse"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by sjokomunn on 2008-11-06
Hey Folks,

I've put in a lot of hours over the past week getting this server together. I've got it almost working now but I've reached the point where I really need some outside advice.

It's a home server which I aim to use as a wireless router/gateway between our laptops here in the flat and the internet beyond. It has two interfaces eth0 (WAN) and ath0 (WLAN). There is no wired LAN interface. I set up the AP using hostapd and IPs are assigned to connecting clients by dhcp3-server. All of this seems to be working as clients can connect successfully using the pre-shared key. However, connected computers cannot access the internet. The results are the same whether shorewall is running with masq configured or whether it is disabled entirely. I will paste some config files which I believe are relevant in hopes that someone can spot an error. I'm guessing it has something to with my /etc/network/interfaces or/etc/dhcp3/dhcpd.conf since I'm still somewhat foggy on how these work. Thank you in advance!
```
#/etc/network/interfaces

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0

auto eth0
iface eth0 inet dhcp
```


Something tells me the following file is the problem. I have declared the static IP of ath0 as the router. Is this correct? Do I need to include the gateway option and if so, what IP would I assign?
```
#/etc/dhcp3/dhcpd.conf

ddns-update-style none;
default-lease-time 86400;
max-lease-time 604800;
authoritative;
subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.200 192.168.0.204;
        option broadcast-address 192.168.0.255;
        option routers 192.168.0.1;
	}
```

```
#/etc/hostapd/hostapd.conf

driver=madwifi
interface=ath0
hw_mode=g
ssid=ubuntu
wpa=3
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
wpa_passphrase=<my pre-shared key> 
```

from syslog
```
Nov  5 20:40:40 ubuntu dhcpd: DHCPOFFER on 192.168.0.204 to 00:19:7d:a7:d2:6b (sjokomunn) via ath0
Nov  5 20:40:40 ubuntu dhcpd: DHCPREQUEST for 192.168.0.204 (192.168.0.1) from 00:19:7d:a7:d2:6b (sjokomunn) via ath0
Nov  5 20:40:40 ubuntu dhcpd: DHCPACK on 192.168.0.204 to 00:19:7d:a7:d2:6b (sjokomunn) via ath0
Nov  5 20:40:40 ubuntu dhcpd: DHCPREQUEST for 192.168.0.204 (192.168.0.1) from 00:19:7d:a7:d2:6b (sjokomunn) via ath0
Nov  5 20:40:40 ubuntu dhcpd: DHCPACK on 192.168.0.204 to 00:19:7d:a7:d2:6b (sjokomunn) via ath0
Nov  5 20:41:03 ubuntu hostapd: ath0: STA 00:19:7d:a7:d2:6b WPA: pairwise key handshake completed (RSN)
```

ifconfig
```
ath0      Link encap:Ethernet  HWaddr 00:1d:6a:17:c4:2d
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:6aff:fe17:c42d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:2290  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23720 (23.1 KB)  TX bytes:20583 (20.1 KB)

eth0      Link encap:Ethernet  HWaddr 00:e0:18:7e:b7:8f
          inet addr:xx.xx.xxx.xx  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::2e0:18ff:fe7e:b78f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8299878 (7.9 MB)  TX bytes:544617 (531.8 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:76 (76.0 B)  TX bytes:76 (76.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1D-6A-17-C4-2D-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1165 errors:0 dropped:0 overruns:0 frame:116
          TX packets:694 errors:25 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280
          RX bytes:74060 (72.3 KB)  TX bytes:120605 (117.7 KB)
          Interrupt:20
```

Cheers.

-Sjoko

---

### Post by sjokomunn on 2008-11-06
Once masqing was configured correctly with shorewall, the only change required in the .confs above was the addition my ISPs nameservers (found in /etc/resolv.conf) to /etc/dhcp3/dhcpd.conf My router/WPA2 access point now works very well. I hope this will be helpful to someone else.

---

