---
title: "wpa_supplicant Woes"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by JPMaximilian on 2007-01-19
I've got wpa_supplicant working to some extent.  I can connect to wireless networks fine, however i will sporadically lose my connection and then after a brief time wpa_supplicant will reconnect, here is some of the output:

```
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:13:5f:56:2a:00
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:13:5f:56:2a:00
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
```

I experience this on multiple different networks, and the wirless networks did not have this problem when I had a powerbook and OS X.  Heres what I run and the output when I connect.

```
:~$ sudo wpa_supplicant -Dwext -iath0 -cwpa_supplicant.conf
Password:
Trying to associate with 00:13:5f:56:0e:10 (SSID='nhwlan' freq=2462 MHz)
Trying to associate with 00:13:5f:56:2a:00 (SSID='nhwlan' freq=2437 MHz)
Associated with 00:13:5f:56:2a:00
WPA: Tx bit set for GTK, but pairwise keys are used - ignore Tx bit
WPA: Key negotiation completed with 00:13:5f:56:2a:00 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:13:5f:56:2a:00 completed (auth) [id=0 id_str=]

```  

And here is my wpa_supplicant config file (I removed the keys obviously):

```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz for more
#  complete configuration parameters.
#
# Also see the other files in /usr/share/doc/wpasupplicant/examples/ for
#  specific configuration examples.

# sudo killall -q wpa_supplicant
# sudo wpa_supplicant -Dwext -iath0 -cwpa_supplicant.conf


ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

##Newman Hall
network={
	ssid="nhwlan"
	scan_ssid=1
	#proto=RSN
	#key_mgmt=WPA-PSK
	#pairwise=CCMP
	#group=CCMP
	psk="<<changed>>"
	#psk=<<changed>>
	priority=4
}

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
#network={
#	ssid=""
#	key_mgmt=NONE
#	priority=5
#}
```

Any help would be appreciated.  Another question is, is CTRL-C the best way to stop wpa_supplicant?

---

