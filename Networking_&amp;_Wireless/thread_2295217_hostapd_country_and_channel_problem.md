---
title: "hostapd country and channel problem"
date: 2015-09-16
forum: Networking &amp; Wireless
---

### Post by philwild on 2015-09-16
Hi,

I'm trying to get hostapd running under 14.04.
I cannot start the service when the channel is set to 13 (or 12)
I'm pulling what little hair I have left out. Any assistance would be gratefully accepted =)

If I bring the interface up and run iwlist wlan0 scan I can see an AP running on channel 13 and can connect to it so I know my interface is working.

This is my config file /etc/hostapd/hostapd.con

```
country_code=AU
driver=nl80211
macaddr_acl=0
ssid=Media
wpa_passphrase=XXXXX
interface=wlan0
auth_algs=3
channel=13
hw_mode=g
logger_stdout=-1
logger_stdout_level=2
max_num_sta=5
rsn_pairwise=CCMP
wpa=2
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
```

This is what is reported

```
Configuration file: /etc/hostapd/hostapd.conf
wlan0: interface state UNINITIALIZED->COUNTRY_UPDATE
wlan0: IEEE 802.11 Configured channel (13) not found from the channel list of current mode (1) IEEE 802.11g
wlan0: IEEE 802.11 Hardware does not support configured channel
Could not select hw_mode and channel. (-3)
wlan0: Unable to setup interface.
hostapd_free_hapd_data: Interface wlan0 wasn't started
```

If I set the channel to 11

It works but reports the following

```
Configuration file: /etc/hostapd/hostapd.conf
wlan0: interface state UNINITIALIZED->COUNTRY_UPDATE
Using interface wlan0 with hwaddr e8:b1:fc:45:2d:9c and ssid "Media"
random: Only 15/20 bytes of strong random data available from /dev/random
random: Not enough entropy pool available for secure operations
WPA: Not enough entropy in random pool for secure operations - update keys later when the first station connects
wlan0: interface state COUNTRY_UPDATE->ENABLED
wlan0: AP-ENABLED 

```

I've run

iw reg set AU

and iw reg get returns

```
country AU:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (3, 23)
	(5250 - 5330 @ 40), (3, 23), DFS
	(5735 - 5835 @ 40), (3, 30)
```

crda report

```
Failed to set regulatory domain: -7
```

crda is installed and /etc/default/crda contains

```
REGDOMAIN=AU
```

lspci reports

```
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)
```

and /etc/lsb-release is

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
```

---

