---
title: "wlan0 config blemishes resolv.conf"
date: 2016-01-05
forum: Networking &amp; Wireless
---

### Post by Hacktoupet on 2016-01-05
Hi,

I'd like to provide a wifi "access point" for a bunch of devices. Those devices should be able to communicate with each other, but don't need access to our lan or the internet.

So I grabbed a machine from our lan (Ubuntu 14.4 via Maas, different IP range) with two interfaces, eth0 and wlan0 (let's ignore lo),  installed and configured hostapd and isc-dhcp-server and our devices are able to connect to this machine and to each other.

But: whenever I reboot the server, /etc/resolv.conf (yes, it's a link) contains no name servers. When I remove the wlan0 config from interfaces the correct entries from the dhcp server (from our lan) are there. Any ideas? I don't need dns for wlan0 and 192.168.x.x but need to administrate and update via eth0. 

/etc/network/interfaces:
```

auto eth0
iface eth0 inet dhcp


auto wlan0
iface wlan0 inet static
    address 192.168.0.1
    netmask 255.255.0.0

```

hostapd.conf:
```

interface=wlan0
driver=nl80211
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=...
country_code=...
ieee80211d=1
hw_mode=g
channel=9
beacon_int=100
dtim_period=2
max_num_sta=255
rts_threshold=2347
fragm_threshold=2346
macaddr_acl=0
auth_algs=3
ignore_broadcast_ssid=0
wmm_enabled=1
wmm_ac_bk_cwmin=4
wmm_ac_bk_cwmax=10
wmm_ac_bk_aifs=7
wmm_ac_bk_txop_limit=0
wmm_ac_bk_acm=0
wmm_ac_be_aifs=3
wmm_ac_be_cwmin=4
wmm_ac_be_cwmax=10
wmm_ac_be_txop_limit=0
wmm_ac_be_acm=0
wmm_ac_vi_aifs=2
wmm_ac_vi_cwmin=3
wmm_ac_vi_cwmax=4
wmm_ac_vi_txop_limit=94
wmm_ac_vi_acm=0
wmm_ac_vo_aifs=2
wmm_ac_vo_cwmin=2
wmm_ac_vo_cwmax=3
wmm_ac_vo_txop_limit=47
wmm_ac_vo_acm=0
eap_server=0
own_ip_addr=127.0.0.1
wpa=2
wpa_passphrase=...
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP

```

dhcpd.conf
```

ddns-update-style none;
authoritative;
log-facility local7;


class "..." {
  match if substring (hardware, 1, 3) = ...;
}


host ... {
  hardware ethernet ...;
}


subnet 192.168.0.0 netmask 255.255.0.0 {
  pool {
    allow known-clients;
    range 192.168.0.10 192.168.0.255;
    max-lease-time 86400;
  }
  pool {
    allow members of "...";
    range 192.168.1.0 192.168.1.255;
    max-lease-time 44640;
  }
  pool {
    deny members of "...";
    deny known-clients;
    range 192.168.2.0 192.168.5.255;
    max-lease-time 20160;
  }
}

```

---

### Post by Hacktoupet on 2016-01-06
I switched to 15.10 with systemd and everything works fine.

---

