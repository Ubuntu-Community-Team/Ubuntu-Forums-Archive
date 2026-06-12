---
title: "Ubuntu server as router - few questions"
date: 2019-03-09
forum: Networking &amp; Wireless
---

### Post by vobo70 on 2019-03-09
I installed clean ubuntu 18.04 server on asrock j4105m mobo, added pcie dual ethernet card(RTL8111E, pcie to nvme card, hardware raid (dell prec h310). But regarding configuration I have some questions:
- how to block incoming connections in UFW only to WAN card and only from internet?
- do I have to put more rules than default (block incoming, allow outgoin and allow forward)?
- to setup dual wireless AP's should I use wifi-ap.config?
( i have two dual adapters already seen by system - realtek RTL8814AU and ralink [FONT=sans-serif]RT5372)[/FONT]
- or use netplan to setup wifi AP?
any suggestions welcome.
thank you

Maciek

---

### Post by TheFu on 2019-03-09
UFW is meant to be used for end-users, not the complexity of routers.  You'll need a lower-level firewall interface like iptables to handle the more complex requirements of a router.

Also, if you can, get Intel NICs. There are many reasons, but performance, lower CPU overhead and rock solid driver support are a few reasons. Just search these forums for all the realtek NIC issues. There are thousands.

I don't connect my wifi with routers. Sorry.  I keep the wifi APs separate. It is just much easier since where I need an AP (ceiling, center of building) is very different from where I need a router (locked wiring closet near ISP demarcation point).

This article might be helpful, [https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) though it doesn't deal with 18.04 which changed the network configurations drastically.

---

### Post by vobo70 on 2019-03-13
Thank you very much. I will read that article.
I exchanged intel dual nic to realtek due to the card was reseting after few seconds from boot. Tried two same model.

---

### Post by vobo70 on 2019-03-15
OK. I read that article. Everything works except wlan AP:
My netplan:
```
network:  ethernets:
    enp3s0:
      dhcp4: false
      dhcp6: false
      optional: true
    enp5s0:
      dhcp4: false
      dhcp6: false
      optional: true
    enp7s0:
      dhcp4: true
      dhcp6: false
    wlx0c9d92b3ad6c:
      dhcp4: false
      dhcp6: false
  bridges:
    br0:
      dhcp4: false
      dhcp6: false
      addresses:
        - 192.168.0.1/24
      gateway4: 192.168.1.1
      nameservers:
        search: [lan]
        addresses: [192.168.1.1, 8.8.8.8, 8.8.4.4]
      interfaces:
        - enp3s0
        - enp5s0
        - wlx0c9d92b3ad6c
  version: 2
  renderer: NetworkManager
```
and hostapd.conf:

```
auth_algs=1
beacon_int=50
channel=3
country_code=TW
disassoc_low_ack=1
driver=nl80211
hw_mode=g
ht_capab=[HT40+][HT40-][SHORT-GI-40][RX-STBC1]
ieee80211d=1
ieee80211n=1
interface=wlx0c9d92b3ad6c
require_ht=0
rsn_pairwise=CCMP
ssid=hotspot
wmm_enabled=1
wpa=2
wpa_key_mgmt=WPA-PSK
wpa_passphrase=xxxxxxxxx
```


my wifi card is Asus USB-N14 using raling 2800 drivers work out of the box seen as wlx0c9d92b3ad6c
and when i try to start hostapd it does not work:

```
maciek@serwer:~$ sudo hostapd /etc/hostapd/hostapd.confConfiguration file: /etc/hostapd/hostapd.conf
nl80211: Could not configure driver mode
nl80211: deinit ifname=wlx0c9d92b3ad6c disabled_11b_rates=0
nl80211 driver initialization failed.
wlx0c9d92b3ad6c: interface state UNINITIALIZED->DISABLED
wlx0c9d92b3ad6c: AP-DISABLED
hostapd_free_hapd_data: Interface wlx0c9d92b3ad6c wasn't started
```

I would like also to allow only specyfic MAC to connect to wifi ap
Any help will be appreciated

---

