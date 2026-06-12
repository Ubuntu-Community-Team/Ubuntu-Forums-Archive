---
title: "Get the full speed out of ALFA AWUS036ACHM in AP mode"
date: 2022-01-04
forum: Networking &amp; Wireless
---

### Post by fr0gr0 on 2022-01-04
I bought an ALFA AWUS036ACHM wifi usb dongle which works phenomenal as a Wifi AP/Hotspot on a Raspberry Pi 4 with Raspberry Pi OS after having optimized the hostapd.conf. I tried to get it working as a Wifi AP/Hotspot on my Dell Intel tablet with Ubuntu Studio as well. I created a Hotspot by following the suggested way - network settings - add a new wifi network in Hotspode mode, band A 5GHz, channel 36, MTU automatic, no proxy. I recognized that hostadp.conf is not used with this way of configuration in Ubuntu. Unfortunately the connection rate is far behind the one I reach with my Rasperry Pi using hostapd.conf and Raspberry Pi OS. Is there a way to optimize the AP settings like the way I have done in my hostapd.conf? 
Following the content of my hostapd.conf:

ssid=raspi-webgui
country_code=DE
driver=nl80211
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
interface=wlan1
beacon_int=100

# Security
wpa_passphrase=ChangeMe
wpa=2
auth_algs=1
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP
rsn_pairwise=CCMP

hw_mode=a
# Channel
channel=36
# Channel width
vht_oper_chwidth=1
# VHT center channel (chan + 6)
vht_oper_centr_freq_seg0_idx=42

#ieee80211d=1

ieee80211n=1
wmm_enabled=1
# mt7610u
ht_capab=[HT40+][HT40-][GF][SHORT-GI-20][SHORT-GI-40]

ieee80211ac=1
# mt7610u
vht_capab=[SHORT-GI-80][MAX-A-MPDU-LEN-EXP3][RX-ANTENNA-PATTERN][TX-ANTENNA-PATTERN]

---

