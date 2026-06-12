---
title: "The wireless interface of H370N WiFi cannot be a access point"
date: 2018-09-22
forum: Networking &amp; Wireless
---

### Post by tomhsiung on 2018-09-22
My motherboard is Gigabyte H370N WiFi and I want to turn its wireless interface into a access point.

This is the result of hostapd command.

```
[COLOR=#000000][FONT=Menlo]Configuration file: /etc/hostapd/hostapd.conf[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]wlo1: interface state UNINITIALIZED->COUNTRY_UPDATE[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ACS: Automatic channel selection started, this may take a bit[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlo1: interface state COUNTRY_UPDATE->ACS[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlo1: ACS-STARTED [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ACS: Unable to collect survey data[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ACS: All study options have failed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Interface initialization failed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlo1: interface state ACS->DISABLED[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlo1: AP-DISABLED [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ACS: Possibly channel configuration is invalid, please report this along with your config file.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ACS: Failed to start[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlo1: AP-DISABLED [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]hostapd_free_hapd_data: Interface wlo1 wasn't started[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: deinit ifname=wlo1 disabled_11b_rates=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlo1: interface state DISABLED->DISABLED[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlo1: interface state DISABLED->DISABLED[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlo1: AP-DISABLED [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]hostapd_free_hapd_data: Interface wlo1 wasn't started[/FONT][/COLOR]
```

This is the settings of hostapd.conf
```
[COLOR=#000000][FONT=Menlo]interface=wlo1[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]driver=nl80211[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]country_code=CN[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ssid=H370N[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]hw_mode=a[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]channel=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]macaddr_acl=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]auth_algs=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ignore_broadcast_ssid=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa=3[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_passphrase=xxxxxxxx[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_key_mgmt=WPA-PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_pairwise=TKIP[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]rsn_pairwise=CCMP[/FONT][/COLOR]
```

---

### Post by chili555 on 2018-09-22
I wouldn't use auto channel selection, nor would I suggest TKIP.

Does your device support AP mode? Not all do.```
iw list
```Do you see this?> Supported interface modes:
		 * IBSS
		 * managed
		 * [COLOR="#FF0000"]**AP**[/COLOR]
		 * AP/VLAN
		 * monitor
		 * P2P-client
		 * P2P-GO
		 * P2P-device


---

### Post by tomhsiung on 2018-09-23
Yes, AP mode is there.

```
[COLOR=#000000][FONT=Menlo]Supported interface modes:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]		 * IBSS[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]		 * managed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]		 * AP[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]		 * AP/VLAN[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]		 * monitor[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]		 * P2P-client[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]		 * P2P-GO[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]		 * P2P-device[/FONT][/COLOR]

```

---

### Post by chili555 on 2018-09-24
Is the interface wlo1 running correctly when conneted to the internet? Does it help to click the Network Manager icon and disconnect from the router before you start hostap?

Is there any improvement if you manually switch to Master mode first?```
sudo ifconfig wlo1 down
sudo iwconfig wlo1 mode Master
sudo ifconfig wlo1 up
```

---

### Post by tomhsiung on 2018-09-30
Yes, I had tried the command of ```
sudo ifconfig wlo1 down/up
``` but no luck.

The wlo1 interface runs correctly when as an wireless client.

BTW, if I add configuration of wlo1 to ```
/etc/network/interfaces
```, my PPPoE (ppp0 over en0) will disappear after the next rebooting. The ppp0 should connect automatically when the system boots up.

```
ppp0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1492
        inet x.x.x.x  netmask 255.255.255.255  destination x.x.x.x
        ppp  txqueuelen 3  (Point-to-Point Protocol)
        RX packets 7849742  bytes 7557173984 (7.5 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7680170  bytes 1133348976 (1.1 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet x.x.x.x  netmask 255.255.255.0  broadcast x.x.x.x
        inet6 x  prefixlen 64  scopeid 0x20<link>
        ether x:x:x:x:x:x  txqueuelen 1000  (Ethernet)
        RX packets 1107618  bytes 404651515 (404.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 413159  bytes 49390147 (49.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

---

