---
title: "Ubuntu xsupplicant wireless &amp; Linksys WRT54GL"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by Alf Stockton on 2006-07-31
I am attempting to implement xsupplicant using my laptops Intel Corporation PRO/Wireless 2200BG (rev 05) with the above mentioned configuration.
When I use the following command:-
sudo xsupplicant -w -dasic -i eth1 -f
Password:
Using default config path!
[STATE] Reinit state machine
[INT] Clearing keys!
[INT] Initializing socket for interface eth1..
[INT] Allmulti mode is already enabled on this device!
Not turning on WPA support!
[INT] Interface eth1 is wireless!
[INT] Interface initialized!
[INT] Interface eth1 is wireless!
Your card is currently set for wireless network "stockton".  Looking for a config.
[CONFIG] Working from config file /etc/xsupplicant/xsupplicant.conf.
[INT] Issuing scan request for interface eth1!
[INT] Checking for returned SSID information....
[INT] Reaping data. (Size : 225)
[INT] Reaped Data :
14 00 15 8B 01 00 00 14 - BF C9 0D 2B 02 02 20 00 ...........+....
00 23 56 75 10 00 1B 8B - 08 00 01 00 73 74 6F 63 .#Vu........stoc
6B 74 6F 6E 14 00 01 8B - 49 45 45 45 20 38 30 32 kton....IEEE.802
2E 31 31 62 67 00 56 75 - 08 00 07 8B 03 00 00 00 .11bg.Vu........
0C 00 05 8B 0B 00 00 00 - 00 00 00 32 08 00 2B 8B ...........2..+.
00 00 00 08 0C 00 21 8B - 80 F9 37 03 00 00 00 08 ......!...7.....
38 00 02 8C 30 00 00 08 - 20 52 61 74 65 73 20 28 8...0....Rates.(
4D 62 2F 73 29 3A 20 31 - 20 32 20 35 2E 35 20 36 Mb/s):.1.2.5.5.6
20 39 20 31 31 20 31 32 - 20 31 38 20 32 34 20 33 .9.11.12.18.24.3
36 20 34 38 20 35 34 20 - 08 00 01 8C 62 E6 00 47 6.48.54.....b..G
22 00 05 8C 1A 00 00 00 - DD 18 00 50 F2 01 01 00 "..........P....
00 50 F2 02 01 00 00 50 - F2 02 01 00 00 50 F2 02 .P.....P.....P..
00 00 1F 00 02 8C 17 00 - 00 00 20 4C 61 73 74 20 ...........Last.
62 65 61 63 6F 6E 3A 20 - 32 35 36 6D 73 20 61 67 beacon:.256ms.ag
6F                                                o
[INT] AP MAC : 00 14 BF C9 0D 2B
Segmentation fault

Has anyone else successfully implemented this and/or is there a howto?

---

### Post by x64Jimbo on 2006-07-31
what about wpa_supplicant? or wpa_gui? try those yet?

---

### Post by Alf Stockton on 2006-07-31
Yes but I want to try xsupplicant

---

### Post by Alf Stockton on 2006-07-31
When I try wpa_supplicant I get:-
sudo wpa_supplicant -w -d -i eth1 -D ipw -c /etc/wpa_supplicant.conf
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
Priority group 0
   id=0 ssid='Stockton'
   id=1 ssid='stockton'
   id=2 ssid='Stockton'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:12:f0:6e:2c:50
wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 225 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:14:bf:c9:0d:2b ssid='stockton' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   selected based on WPA IE
Trying to associate with 00:14:bf:c9:0d:2b (SSID='stockton' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
State: SCANNING -> ASSOCIATING
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=17
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 225 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:14:bf:c9:0d:2b ssid='stockton' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
   selected based on WPA IE
Trying to associate with 00:14:bf:c9:0d:2b (SSID='stockton' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
State: SCANNING -> ASSOCIATING
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=17
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_set_wpa: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
No keys have been configured - skip key clearing
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Cancelling scan request
alf@puppypad:~$

and I do not know enough about wireless networking to understand even a little bit of the above.

---

### Post by x64Jimbo on 2006-07-31
It's not connecting to your router. How did you set it up? Did you have a /etc/wpa_supplicant.conf file? What are its contents (password censored, of course)?

---

### Post by Alf Stockton on 2006-08-01
It is connected to the router.

and the wpa_supplicant.conf looks like:-
##### Example wpa_supplicant configuration file ###############################
#
#
# Original Version
# ----------------
#	wpa_supplicant-0.2.3/wpa_supplicant.conf
#
#
# To Reload Changees
# ------------------
#	killall -HUP wpa_supplicant
#
#
# To Generate the WPA network keys
# --------------------------------
#	wpa_passphrase "essid-of-the-ap" "the secret passphrase"
#
#
# To Install the wpa daemon
# -------------------------
#	wpa_supplicant -Bw [ -dd ] -c/etc/wpa_supplicant.conf -iath0
#
#	Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
#	Reading configuration file '/etc/wpa_supplicant.conf'
#	ctrl_interface='/var/run/wpa_supplicant'
#	eapol_version=1
#	Daemonize..
#
#	Trying to associate with <MAC-Address-of-AccessPoint> \
#		(SSID='Testing-ESSID' freq=2437 MHz)
#	WPA key negotiation completed with <MAC-Address-of-AccessPoint>
#
#
# 21-Jun-04 amo Copied from wpa_supplicant-0.2.3/wpa_supplicant.conf
# 27-Jun-04 amo Removed un-necessary comments
#
#
#
ctrl_interface=/var/run/wpa_supplicant

eapol_version=1

#
#
# Only WPA-PSK is used. Any valid cipher combination is accepted.
#
network={
 	ssid="Stockton"
	#
	# if proto is not defined, defaults to: WPA RSN
	proto=WPA
	#
	# if key_mgmt is not defined, defaults to: WPA-PSK WPA-EAP
	# key_mgmt=WPA-PSK
	#
	# if pairwise is not defined, defaults to: CCMP TKIP
	pairwise=TKIP
	#
	# if group is not defined, defaults to: CCMP TKIP WEP104 WEP40
	group=TKIP
	#
	# if eap is not defined, defaults to: MD5 MSCHAPV2 TLS PEAP TTLS
	#
	# psk: WPA preshared key - not needed if wpa-eap is used
	psk=?????????
    #    
}
#
#
# End of file

# reading passphrase from stdin
network={
       ssid="Stockton"
       proto=WPA
       scan_ssid=1
       key_mgmt=WPA-PSK
       psk=?????????
}
#network={
#        ssid="stockton"
#        #psk=????????
#        #psk=????????
#}

#network={
#	ssid="Stockton"
#	# psk=??????????????
#}

---

