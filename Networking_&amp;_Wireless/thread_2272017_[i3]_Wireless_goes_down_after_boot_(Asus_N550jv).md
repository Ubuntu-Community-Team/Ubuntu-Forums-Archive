---
title: "[i3] Wireless goes down after boot (Asus N550jv)"
date: 2015-04-03
forum: Networking &amp; Wireless
---

### Post by franke-remy on 2015-04-03
[COLOR=#333333][FONT=UbuntuRegular]I've got an asus N550JV running Ubuntu 14.10.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've replaced Unity with i3 and am having networking problems ever since.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Right now my WIFI is connected as soon as i3 loads up, but it disconnects after 1 second. Ethernet stays up in the meantime though.[/FONT][/COLOR]
[B]
Some details:[/B]
```
@dev-Laptop:~$ sudo rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
@dev-Laptop:~$ sudo cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
        wpa-ssid ssid
        wpa-psk password
```


[COLOR=#333333][FONT=UbuntuRegular]If i add rfkill unblock all to /etc/rc.local then it won't boot with any networking at all, allthough rfkill list all shows that everything is unblocked then.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In the above configuration:
[/FONT][/COLOR]
```
@dev-Laptop:~$ sudo ifup wlan0 -v
\Configuring interface wlan0=wlan0 (inet)
run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "ssid" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient -1 -v -pf /run/dhclient.wlan0.pid -lf /var/lib/dhcp/dhclient.wlan0.leases wlan0    
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

RTNETLINK answers: Operation not possible due to RF-kill
Listening on LPF/wlan0/80:86:f2:52:48:15
Sending on   LPF/wlan0/80:86:f2:52:48:15
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x174b3ce0)
send_packet: Network is down
dhclient.c:1993: Failed to send 300 byte long packet over wlan0 interface.
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x174b3ce0)
send_packet: Network is down
dhclient.c:1993: Failed to send 300 byte long packet over wlan0 interface.
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x174b3ce0)
send_packet: Network is down
dhclient.c:1993: Failed to send 300 byte long packet over wlan0 interface.
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x174b3ce0)
send_packet: Network is down
dhclient.c:1993: Failed to send 300 byte long packet over wlan0 interface.
```

[COLOR=#333333][FONT=UbuntuRegular]Any ideas where to take it from here? I've googled about for some time and have managed to get a connection working through wpa_cli but that doesn't persist.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The wifi is secured with WPA/PSK2.

(Full disclosure: This is a copy from [http://askubuntu.com/questions/603051/wifi-on-boot-but-disconnect-immediatly](http://askubuntu.com/questions/603051/wifi-on-boot-but-disconnect-immediatly) wasn't getting much action there)[/FONT][/COLOR]

---

