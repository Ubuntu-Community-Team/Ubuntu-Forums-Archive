---
title: "Panda PAU05 - ok under 14.04, excessive TX retries under 18.04"
date: 2018-06-02
forum: Networking &amp; Wireless
---

### Post by mynot on 2018-06-02
[Sorry, it's a Panda PAU06, not 05]

This problem first appeared after a complete re-install from Xubuntu 14.04 to Xubuntu 18.04. Prior to that everything was working fine. After a fortnight of trying to sort out why crowsers and email took so long to reach servers I think I've discovered the reason.

The output of iwconfig is:

wlx7cdd90828526  IEEE 802.11  ESSID:"Telstra6C1DB9"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: F4:6B:EF:6C:1D:BF   
          Bit Rate=86.7 Mb/s   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:821  Invalid misc:456   Missed beacon:0

[Afraid I don't know how to put this in nice scrollable windows]. The TX excessive retries can be in the thousands.

sudo lshw -C network gives:
 *-usb:1
       description: Wireless interface
       product: 802.11 n WLAN
       vendor: Ralink
       physical id: 4
       bus info: usb@5:1.4
       logical name: wlx7cdd90828526
       version: 1.01
       serial: 7c:dd:90:82:85:26
       capabilities: usb-2.00 ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.15.0-22-generic firmware=0.36 ip=10.0.0.42 link=yes maxpower=450mA multicast=yes speed=480Mbit/s wireless=IEEE 802.11

nmcli:
wlx7cdd90828526: connected to Telstra6C1DB9
        "Ralink 802.11 n WLAN"
        wifi (rt2800usb), 7C:DD:90:82:85:26, hw, mtu 1500
        ip4 default, ip6 default
        inet4 10.0.0.42/24
        route4 0.0.0.0/0
        route4 10.0.0.0/24
        route4 169.254.0.0/16
        inet6 2001:8003:a036:8900:f53b:7355:7dda:a2d/64
        inet6 2001:8003:a036:8900:37a0:26bb:7af5:165a/64
        inet6 fe80::e513:4d52:db84:fec1/64
        route6 2001:8003:a036:8900::/64
        route6 ::/0
        route6 ff00::/8
        route6 fe80::/64
        route6 fe80::/64
        route6 2001:8003:a036:8900::/64

The pc is in a domestic situation, it's location has not changed, the three other devices using the wifi have not changed and none show any performance issues.

Any help will be greatly appreciated.
Thanks

---

### Post by mynot on 2018-06-07
No help as yet. I've just discovered wifi-info and pastebinit, so here is the output:

[http://paste.ubuntu.com/p/YvbmY6N6yZ/](http://paste.ubuntu.com/p/YvbmY6N6yZ/)

Still hoping someone can help.
Thanks

---

### Post by praseodym on 2018-06-09
Lets try
```

echo "options rt2800usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf
```
Reboot

---

### Post by mynot on 2018-06-16
Thanks, but if anything it made it worse.
tony

---

