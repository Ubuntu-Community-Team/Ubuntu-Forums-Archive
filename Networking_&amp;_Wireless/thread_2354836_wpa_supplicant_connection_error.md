---
title: "wpa_supplicant connection error"
date: 2017-03-07
forum: Networking &amp; Wireless
---

### Post by daniellej on 2017-03-07
[COLOR=#333333][FONT=sans-serif]Hi, I was hoping to get some advises here with the
network connection problem I am been struggling with.
[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]I am using Ubuntu 14.04 running on Minnowboard Turbot,
and I want to have wireless internet connection using Intel 5300 network chip,
but somehow it won't connect.

I can see the list of SSIDs in the network manager,
but after connection attempts, it just fails to connect.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]I've tried using wicd, but it also hangs at the 'Obtaining IP address' stage.
I've checked that it is nto soft or hard blocked and also checked the driver using lspci command, but still doesn't work.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
So I am now trying to follow up the steps listed in the post,
[https://wiki.archlinux.org/index.php/Wireless_network_configuration#Wireless_management](https://wiki.archlinux.org/index.php/Wireless_network_configuration#Wireless_management)
to manually make connection using wpa_supplicant,[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]but it still gives me error.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
This is the /etc/network/interfaces file:
[/FONT][/COLOR]```

[FONT=sans-serif]# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet dhcp

auto wlan2
allow-hotplug wlan2
iface wlan2 inet dhcp
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
[/FONT]
```[COLOR=#333333][FONT=sans-serif]


[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]The /etc/wpa_supplicant/wpa_supplicant.conf file has:[/FONT][/COLOR]
[FONT=sans-serif]```

network={
        ssid="WLAN_5G"
        psk="password"
}

```[/FONT][COLOR=#333333][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]I removed the hashed psk value because it gave me the following error:[/FONT][/COLOR]
```
[FONT=sans-serif]wlan2: WPA: 4-Way Handshake failed - pre-shared key may be incorrect[/FONT]
```
[COLOR=#333333][FONT=sans-serif]When I switched it to a clear text psk value, the error disappeared,
but still no connection...[/FONT][/COLOR]

[COLOR=#333333][FONT=sans-serif]
This is the command I entered:
[/FONT][/COLOR]```

[FONT=sans-serif]wpa_supplicant -D nl80211,wext -i wlan2 -c /etc/wpa_supplicant/wpa_supplicant.conf [/FONT]

```[COLOR=#333333][FONT=sans-serif]
[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]
And this is the result:[/FONT][/COLOR]
```
[FONT=sans-serif]
Successfully initialized wpa_supplicant
wlan2: CTRL-EVENT-SCAN-STARTED 
wlan2: SME: Trying to authenticate with xx:xx:xx:xx:xx:xx (SSID='WLAN_5G' freq=5765 MHz)
wlan2: Trying to associate with [/FONT][FONT=sans-serif]xx:xx:xx:xx:xx:xx[/FONT][FONT=sans-serif] (SSID='WLAN_5G' freq=5765 MHz)
wlan2: Associated with [/FONT][FONT=sans-serif]xx:xx:xx:xx:xx:xx[/FONT][FONT=sans-serif]
wlan2: CTRL-EVENT-DISCONNECTED bssid=c4:04:15:17:8a:98 reason=3 locally_generated=1
wlan2: CTRL-EVENT-SCAN-STARTED 
wlan2: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="HPC_WLAN_5G" auth_failures=1 duration=10[/FONT]

```


[COLOR=#333333][FONT=sans-serif]Anyone knows how to solve this?
It'd be great if anyone can help me solve this problem.[/FONT][/COLOR]

---

