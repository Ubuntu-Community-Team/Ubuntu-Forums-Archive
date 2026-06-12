---
title: "network-manager won't connect to 802.1x network anymore"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by jbrown96 on 2008-04-30
I can sometimes connect to my university's wireless network, but I can't at all anymore. I used to be able to with Gutsy, but Hardy is being a huge pain (in many, many more ways).
Info on the network:
essid slunet
encryption dynamic wep
Eap type PEAP
phase2 type MSCHAPv2
identity <my username>
password <my password>
everything else blank

Notes on configuration:
I have turned of ipv6 in /etc/modprobe.d/aliases by changing
```
alias net-pf-10 ipv6
``` to ```
alias net-pf-10 off ipv6

``` and I have also tried ```
alias net-pf-10 off
```

Here is a log dump from a connection attempt:
> Apr 30 15:23:36 plum NetworkManager: <info>  Activation (wlan0/wireless): access point 'slunet' is encrypted, and a key exists.  No new key needed. 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was '0' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 736c756e6574' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt IEEE8021X' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 phase2 "auth=MSCHAPV2"' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 eap PEAP' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 identity "mcdanie"' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 password <password>' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 anonymous_identity "fds"' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 fragment_size 1300' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr 30 15:23:38 plum NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 15:23:38 plum NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 30 15:23:38 plum NetworkManager: <debug> [1209587018.446519] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:83:2F:0F to 00:15:C7:83:B1:A0 on wireless network 'slunet' 
Apr 30 15:23:40 plum NetworkManager: <debug> [1209587020.447756] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:83:B1:A0 to 00:15:C7:83:2F:00 on wireless network 'slunet' 
Apr 30 15:23:45 plum NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Apr 30 15:23:52 plum NetworkManager: <debug> [1209587032.447967] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:83:2F:00 to 00:15:C7:83:B1:A0 on wireless network 'slunet' 
Apr 30 15:23:56 plum NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Apr 30 15:24:04 plum NetworkManager: <debug> [1209587044.447962] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:83:B1:A0 to 00:15:C7:83:2F:00 on wireless network 'slunet' 
Apr 30 15:24:08 plum NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Apr 30 15:24:16 plum NetworkManager: <debug> [1209587056.447995] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:83:2F:00 to 00:15:C7:83:2F:0F on wireless network 'slunet' 
Apr 30 15:24:16 plum NetworkManager: <debug> [1209587056.454916] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'slunet' 
Apr 30 15:24:16 plum NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Apr 30 15:24:19 plum NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Apr 30 15:24:20 plum NetworkManager: <debug> [1209587060.447692] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:83:2F:00 to 00:15:C7:83:2F:0F on wireless network 'slunet' 
Apr 30 15:24:25 plum NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr 30 15:24:25 plum NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Apr 30 15:24:28 plum NetworkManager: <debug> [1209587068.447990] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:83:2F:0F to 00:15:C7:83:B2:C0 on wireless network 'slunet' 
Apr 30 15:24:31 plum NetworkManager: <info>  Old device 'wlan0' activating, won't change. 

As you can see, the network card, wlan0, seems to get stuck and keeps roaming from access point to access point. 

Does anyone have an idea about what's going wrong? This exact configuration used to work, so...

---

### Post by jbrown96 on 2008-05-01
I've figured out the problem: iwlwifi3945 driver. The ipw3945 driver project has been depreciated. Some other distros have already moved to it. In the new kernel 2.6.24, the driver is built in, so Ubuntu finally gave up on it. Unfortunately, the new driver is terrible. There are problems keeping connections, connecting to some types (read 802.1x) of networks, and LED status lights don't work anymore.
There isn't any indication that any of this will be fixed. There have been bug reports for over a year about the status LED...

I can't find any info on how to easily enable the old driver. ipw3945.sourceforge.net has some instructions, but I can't figure out how to fix the errors I get. 

Can anyone help?

---

