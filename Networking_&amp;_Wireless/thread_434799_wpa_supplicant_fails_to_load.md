---
title: "wpa_supplicant fails to load"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by morbid88 on 2007-05-06
I'm trying to run wpa_supplicant in order to connect to my wireless network, but I can't seem to load it.

I've got an MSI M660 laptop, the wifi adapter is an internal card based on the rt73 (RalinkTech) chipset.

I'm using the rt73 drivers from Serialmonkey, which are supposed to contain wpa support.

Below  is the contents of my wpa_supplicant.conf file, and the output of executing ```
sudo wpa_supplicant -Dwext -irausb0 -c/home/morbid/Shemesh_wpa.conf -dd
```

I'm getting several errors: "network is down", "operation not supported", and finally the driver fails to associate, whatever that means.

I've always been able to manually connect to unencrypted and WEP-enabled wireless networks, but never WPA. I don't use network manager (it doesn't work for me with WPA.)

I've probably read just about every single guide on ubuntuforums, and I'm really getting tired of this. Why can't it be easy? Can anyone help me out with this?

Jonathan.

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
	ssid="Shemesh"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP
	#psk=<my passphrase>
	psk=<my_psk>
}
```

```
morbid@morbid-laptop:~$ sudo wpa_supplicant -Dwext -irausb0 -c/home/morbid/Shemesh_wpa.conf -dd
Initializing interface 'rausb0' conf '/home/morbid/Shemesh_wpa.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/home/morbid/Shemesh_wpa.conf' -> '/home/morbid/Shemesh_wpa.conf'
Reading configuration file '/home/morbid/Shemesh_wpa.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=7):
     53 68 65 6d 65 73 68                              Shemesh         
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Shemesh'
Initializing interface (2) 'rausb0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Network is down
ioctl[SIOCSIWMODE]: Network is down
Could not configure driver to use managed mode
SIOCGIWRANGE: WE(compiled)=21 WE(source)=14 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:13:d3:7a:d4:87
wpa_driver_wext_set_wpa
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_countermeasures
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - wpa_driver_wext_set_drop_unencrypted
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Setting scan request: 0 sec 100000 usec
Added interface rausb0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'rausb0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'rausb0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'rausb0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'rausb0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b2a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b2a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b2a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b2a len=8
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'Shemesh'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 6 value 0x1 - WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
WEXT: Driver did not support SIOCSIWAUTH for AUTH_ALG, trying SIOCSIWENCODE
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 0 value 0x2 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 1 value 0x4 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 2 value 0x4 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 3 value 0x2 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 10 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 8 value 0x0 - Association request to the driver failed

```

---

