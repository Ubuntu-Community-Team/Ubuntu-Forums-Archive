---
title: "Creating wireless hostpot using hostapd causes authentication failure on other system"
date: 2014-03-02
forum: Networking &amp; Wireless
---

### Post by vj41 on 2014-03-02
Hi,

I have Ubuntu 13.10 on my system and tried to run a wireless hotspot on it using ap-hotspot([http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html](http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html) , Github: [https://github.com/hotice/AP-hotspot/](https://github.com/hotice/AP-hotspot/)). THe hotspot is running, however, whenever I try to connect any device to it, authentication failure occurs. My card is Realtek 8188CE, and I tried installing custom drivers for this as well([https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)) but still no luck.

Whenever I see the syslog(/var/log/syslog), I get

```

Mar  1 11:41:33 vatsalj-ThinkPad-X120e avahi-daemon[788]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.150.1.
Mar  1 11:41:33 vatsalj-ThinkPad-X120e avahi-daemon[788]: New relevant interface wlan0.IPv4 for mDNS.
Mar  1 11:41:33 vatsalj-ThinkPad-X120e avahi-daemon[788]: Registering new address record for 192.168.150.1 on wlan0.IPv4.
Mar  1 11:41:33 vatsalj-ThinkPad-X120e whoopsie[1023]: online
Mar  1 11:41:35  whoopsie[1023]: last message repeated 2 times
Mar  1 11:41:35 vatsalj-ThinkPad-X120e dnsmasq[4385]: started, version 2.66 cachesize 150
Mar  1 11:41:35 vatsalj-ThinkPad-X120e dnsmasq[4385]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Mar  1 11:41:35 vatsalj-ThinkPad-X120e dnsmasq-dhcp[4385]: DHCP, IP range 192.168.150.2 -- 192.168.150.10, lease time 12h
Mar  1 11:41:35 vatsalj-ThinkPad-X120e dnsmasq[4385]: reading /var/run/dnsmasq/resolv.conf
Mar  1 11:41:35 vatsalj-ThinkPad-X120e dnsmasq[4385]: using nameserver 127.0.1.1#53
Mar  1 11:41:35 vatsalj-ThinkPad-X120e dnsmasq[4385]: read /etc/hosts - 7 addresses
Mar  1 11:41:36 vatsalj-ThinkPad-X120e kernel: [ 5508.935028] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar  1 11:41:36 vatsalj-ThinkPad-X120e kernel: [ 5508.969469] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Mar  1 11:41:36 vatsalj-ThinkPad-X120e avahi-daemon[788]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar  1 11:41:36 vatsalj-ThinkPad-X120e avahi-daemon[788]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.150.1.
Mar  1 11:41:36 vatsalj-ThinkPad-X120e avahi-daemon[788]: Withdrawing address record for 192.168.150.1 on wlan0.
Mar  1 11:41:36 vatsalj-ThinkPad-X120e NetworkManager[886]: <info> (wlan0): supplicant interface state: inactive -> disabled
Mar  1 11:41:36 vatsalj-ThinkPad-X120e NetworkManager[886]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:04:00.0/net/mon.wlan0, iface: mon.wlan0)
Mar  1 11:41:36 vatsalj-ThinkPad-X120e NetworkManager[886]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:04:00.0/net/mon.wlan0, iface: mon.wlan0): no ifupdown configuration found.
Mar  1 11:41:37 vatsalj-ThinkPad-X120e dnsmasq[4385]: reading /var/run/dnsmasq/resolv.conf
Mar  1 11:41:37 vatsalj-ThinkPad-X120e dnsmasq[4385]: using nameserver 127.0.1.1#53
Mar  1 11:41:37 vatsalj-ThinkPad-X120e avahi-daemon[788]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.150.1.
Mar  1 11:41:37 vatsalj-ThinkPad-X120e kernel: [ 5509.525857] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  1 11:41:37 vatsalj-ThinkPad-X120e avahi-daemon[788]: New relevant interface wlan0.IPv4 for mDNS.
Mar  1 11:41:37 vatsalj-ThinkPad-X120e avahi-daemon[788]: Registering new address record for 192.168.150.1 on wlan0.IPv4.
Mar  1 11:41:37 vatsalj-ThinkPad-X120e NetworkManager[886]: <info> (wlan0): supplicant interface state: disabled -> scanning
Mar  1 11:41:37 vatsalj-ThinkPad-X120e kernel: [ 5509.661624] 8021q: 802.1Q VLAN Support v1.8
Mar  1 11:41:37 vatsalj-ThinkPad-X120e kernel: [ 5509.702684] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar  1 11:41:37 vatsalj-ThinkPad-X120e whoopsie[1023]: online
Mar  1 11:41:38 vatsalj-ThinkPad-X120e NetworkManager[886]: <info> (wlan0): supplicant interface state: scanning -> inactive
Mar  1 11:41:38 vatsalj-ThinkPad-X120e whoopsie[1023]: online
Mar  1 11:41:38 vatsalj-ThinkPad-X120e avahi-daemon[788]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::ee55:f9ff:fec9:68f.
Mar  1 11:41:38 vatsalj-ThinkPad-X120e avahi-daemon[788]: New relevant interface wlan0.IPv6 for mDNS.
Mar  1 11:41:38 vatsalj-ThinkPad-X120e avahi-daemon[788]: Registering new address record for fe80::ee55:f9ff:fec9:68f on wlan0.*.
Mar  1 11:41:38 vatsalj-ThinkPad-X120e whoopsie[1023]: online
Mar  1 11:42:38  whoopsie[1023]: last message repeated 2 times
Mar  1 11:42:48 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:42:48 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:42:52 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:42:52 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:42:52 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:42:56 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:42:56 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:42:58 vatsalj-ThinkPad-X120e whoopsie[1023]: online
Mar  1 11:42:59 vatsalj-ThinkPad-X120e whoopsie[1023]: online
Mar  1 11:43:01 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:43:01 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:43:05 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:43:05 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:43:10 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:43:10 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:43:14 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:43:14 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:43:19 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:43:19 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:43:23 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:43:23 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:43:27 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: authenticated
Mar  1 11:43:28 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: associated (aid 1)
Mar  1 11:43:36 vatsalj-ThinkPad-X120e whoopsie[1023]: online
Mar  1 11:43:37 vatsalj-ThinkPad-X120e hostapd: wlan0: STA 4c:0f:6e:f4:92:13 IEEE 802.11: deauthenticated due to local deauth request
Mar  1 11:43:37 vatsalj-ThinkPad-X120e whoopsie[1023]: online

```

Any help in this regard will be highly appreciated.

---

