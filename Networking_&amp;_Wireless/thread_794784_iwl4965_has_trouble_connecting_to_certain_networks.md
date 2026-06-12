---
title: "iwl4965 has trouble connecting to certain networks"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by lexxonnet on 2008-05-14
Hi Everyone...

I've posted this before in another thread, but I believe it is annoying enough to warrant its own. I'm not sure where to file this as a bug report, so I'd appreciate some suggestions on that too :)

Anyway, I'm having trouble connecting to my uni network using the iwl4965 wireless card. I have tried on a couple of other laptops (one with an atheros card, and one with an ipw2200). Both of them are better at it than the iwl4965. 

Basically, on the atheros, and the ipw2200, it connects on the first attempt (using wpa_supplicant or networkmanager). On the atheros, this might drop off from time to time however, and after that, reconnecting can be a pain. However, it is mostly stable. The ipw2200 is quite stable, and I haven't had any drop offs with gutsy. I have only tried it briefly with hardy, and it seems fine.

With the iwl4965, network manager just doesn't work. I need to use wpa_supplicant and it takes several attempts (associates, authenticates, associates again, deauthenticates etc), and sometimes gets the better of my patience. However, it mostly eventually connects after about 5-6 minutes of trying. Problem here is, in order for it to connect, I need to run wpa_supplicant twice - once with ap_scan set to 2, kill it and then again with ap_scan set to 1. 

Anyway, it is important to note that it only has trouble connecting to the uni network, for which the config file is shown below.

```

eapol_version=2
ap_scan=1
fast_reauth=1

network={
        ssid="ACHERNAR-BG"
        key_mgmt=WPA-EAP
        proto=WPA
        eap=PEAP
        pairwise=TKIP
        group=TKIP
        identity="*****"
        password="********"
        ca_cert="/etc/ssl/certs/Thawte_Premium_Server_CA.pem"
        phase1="peaplabel=0" include_tls_length=1"
        phase2="auth=MSCHAPV2"
        priority=1
        scan_ssid=1

```

For my home, network (simple WPA-PSK), it connects fine every time.

I've run wpa_supplicant a few times with verbosity to the maximum, and will attach a couple of results here.

dmesg output when it connects after a couple of tries
```

[  740.224968] wlan0: Initial auth_alg=0
[  740.224976] wlan0: authenticate with AP 00:0f:23:ea:58:70
[  740.228165] wlan0: Initial auth_alg=0
[  740.228169] wlan0: authenticate with AP 00:0f:23:ea:58:70
[  740.229820] wlan0: RX authentication from 00:0f:23:ea:58:70 (alg=0 transaction=2 status=0)
[  740.229824] wlan0: authenticated
[  740.229826] wlan0: associate with AP 00:0f:23:ea:58:70
[  740.231953] wlan0: RX ReassocResp from 00:0f:23:ea:58:70 (capab=0x431 status=0 aid=149)
[  740.231957] wlan0: associated
[  749.145721] wlan0: CTS protection disabled (BSSID=00:0f:23:ea:58:70)
[  759.513344] wlan0: RX deauthentication from 00:0f:23:ea:58:70 (reason=23)
[  759.513353] wlan0: deauthenticated
[  760.164658] wlan0: authenticate with AP 00:0f:23:ea:58:70
[  760.166240] wlan0: RX authentication from 00:0f:23:ea:58:70 (alg=0 transaction=2 status=0)
[  760.166248] wlan0: authenticated
[  760.166253] wlan0: associate with AP 00:0f:23:ea:58:70
[  760.168336] wlan0: RX ReassocResp from 00:0f:23:ea:58:70 (capab=0x431 status=0 aid=150)
[  760.168345] wlan0: associated
[  760.168351] wlan0: CTS protection enabled (BSSID=00:0f:23:ea:58:70)
[  760.222945] wlan0: CTS protection disabled (BSSID=00:0f:23:ea:58:70)
[  783.222302] wlan0: RX deauthentication from 00:0f:23:ea:58:70 (reason=23)
[  783.222306] wlan0: deauthenticated
[  783.222314] wlan0: authenticate with AP 00:0f:23:ea:58:70
[  783.223931] wlan0: RX authentication from 00:0f:23:ea:58:70 (alg=0 transaction=2 status=0)
[  783.223934] wlan0: authenticated
[  783.223936] wlan0: associate with AP 00:0f:23:ea:58:70
[  783.225966] wlan0: RX ReassocResp from 00:0f:23:ea:58:70 (capab=0x431 status=0 aid=151)
[  783.225969] wlan0: associated
[  796.905021] wlan0: CTS protection enabled (BSSID=00:0f:23:ea:58:70)
[  807.504998] wlan0: CTS protection disabled (BSSID=00:0f:23:ea:58:70)
[  859.009707] wlan0: CTS protection enabled (BSSID=00:0f:23:ea:58:70)
[  877.826532] wlan0: CTS protection disabled (BSSID=00:0f:23:ea:58:70)

```

corresponding wpa_supplicant output
```

sudo wpa_supplicant -ddd -iwlan0 -Dwext -c/home/lexxonnet/.wpa/uow.conf
Initializing interface 'wlan0' conf '/home/lexxonnet/.wpa/uow.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/home/lexxonnet/.wpa/uow.conf' -> '/home/lexxonnet/.wpa/uow.conf'
Reading configuration file '/home/lexxonnet/.wpa/uow.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group='0' (DEPRECATED)
eapol_version=2
ap_scan=1
fast_reauth=1
Line: 8 - start of a new network block
ssid - hexdump_ascii(len=11):
     41 43 48 45 52 4e 41 52 2d 42 47                  ACHERNAR-BG
key_mgmt: 0x1
proto: 0x1
eap methods - hexdump(len=16): 00 00 00 00 19 00 00 00 00 00 00 00 00 00 00 00
pairwise: 0x8
group: 0x8
identity - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
ca_cert - hexdump_ascii(len=43):
     2f 65 74 63 2f 73 73 6c 2f 63 65 72 74 73 2f 54   /etc/ssl/certs/T
     68 61 77 74 65 5f 50 72 65 6d 69 75 6d 5f 53 65   hawte_Premium_Se
     72 76 65 72 5f 43 41 2e 70 65 6d                  rver_CA.pem
phase1 - hexdump_ascii(len=33):
     70 65 61 70 6c 61 62 65 6c 3d 30 22 20 69 6e 63   peaplabel=0" inc
     6c 75 64 65 5f 74 6c 73 5f 6c 65 6e 67 74 68 3d   lude_tls_length=
     31                                                1
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3d 4d 53 43 48 41 50 56 32            auth=MSCHAPV2
priority=2 (0x2)
password - hexdump_ascii(len=8): [REMOVED]
Priority group 2
   id=0 ssid='ACHERNAR-BG'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1d:e0:86:8d:17
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
ctrl_interface_group=0
ctrl_iface bind(PF_UNIX) failed: Address already in use
ctrl_iface exists, but does not allow connections - assuming it was leftover from forced program termination
Successfully replaced leftover ctrl_iface socket '/var/run/wpa_supplicant/wlan0'
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 2
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 366 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 589 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0f:23:ea:58:70 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:0f:23:ea:58:70 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 599 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0f:23:ea:58:70 ssid='ACHERNAR-BG' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:0f:23:ea:58:70 ssid='ACHERNAR-BG'
Try to find non-WPA AP
Trying to associate with 00:0f:23:ea:58:70 (SSID='ACHERNAR-BG' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 1 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=19
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=169
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE040b160c12182432043048606cdd160050f20101000050f20201000050f20201000050f201 RespIEs=01088b160c12182430483202606c)'
Association info event
req_ies - hexdump(len=53): 00 0b 41 43 48 45 52 4e 41 52 2d 42 47 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
resp_ies - hexdump(len=14): 01 08 8b 16 0c 12 18 24 30 48 32 02 60 6c
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:0f:23:ea:58:70
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:0f:23:ea:58:70
No keys have been configured - skip key clearing
Associated with 00:0f:23:ea:58:70
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=60): 01 00 00 38 01 01 00 38 01 00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52 4e 41 52 2d 42 47 2c 6e 61 73 69 64 3d 42 33 35 53 41 50 31 61 67 2e 6e 65 74 2c 70 6f 72 74 69 64 3d 30
Setting authentication timeout: 70 sec 0 usec
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_PAE entering state RESTART
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=1 method=1 vendor=0 vendorMethod=0
EAP: EAP entering state IDENTITY
CTRL-EVENT-EAP-STARTED EAP authentication started
EAP: EAP-Request Identity data - hexdump_ascii(len=51):
     00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52   _networkid=ACHER
     4e 41 52 2d 42 47 2c 6e 61 73 69 64 3d 42 33 35   NAR-BG,nasid=B35
     53 41 50 31 61 67 2e 6e 65 74 2c 70 6f 72 74 69   SAP1ag.net,porti
     64 3d 30                                          d=0
EAP: using real identity - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=14): 02 00 00 0a 02 01 00 0a 01 61 6d 33 39 34
EAPOL: SUPP_BE entering state RECEIVE
EAPOL: startWhen --> 0
EAPOL: authWhile --> 0
EAPOL: SUPP_BE entering state TIMEOUT
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:0f:23:ea:58:70 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=169
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE040b160c12182432043048606cdd160050f20101000050f20201000050f20201000050f201 RespIEs=01088b160c12182430483202606c)'
Association info event
req_ies - hexdump(len=53): 00 0b 41 43 48 45 52 4e 41 52 2d 42 47 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
resp_ies - hexdump(len=14): 01 08 8b 16 0c 12 18 24 30 48 32 02 60 6c
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:0f:23:ea:58:70
State: SCANNING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:0f:23:ea:58:70
No keys have been configured - skip key clearing
Associated with 00:0f:23:ea:58:70
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=60): 01 00 00 38 01 01 00 38 01 00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52 4e 41 52 2d 42 47 2c 6e 61 73 69 64 3d 42 33 35 53 41 50 31 61 67 2e 6e 65 74 2c 70 6f 72 74 69 64 3d 30
Setting authentication timeout: 70 sec 0 usec
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_PAE entering state RESTART
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=1 method=1 vendor=0 vendorMethod=0
EAP: EAP entering state IDENTITY
CTRL-EVENT-EAP-STARTED EAP authentication started
EAP: EAP-Request Identity data - hexdump_ascii(len=51):
     00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52   _networkid=ACHER
     4e 41 52 2d 42 47 2c 6e 61 73 69 64 3d 42 33 35   NAR-BG,nasid=B35
     53 41 50 31 61 67 2e 6e 65 74 2c 70 6f 72 74 69   SAP1ag.net,porti
     64 3d 30                                          d=0
EAP: using real identity - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=14): 02 00 00 0a 02 01 00 0a 01 61 6d 33 39 34
EAPOL: SUPP_BE entering state RECEIVE
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 2
Try to find WPA-enabled AP
Try to find non-WPA AP
No APs found - clear blacklist and try again
Removed BSSID 00:0f:23:ea:58:70 from blacklist (clear)
Selecting BSS from priority group 2
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
EAPOL: startWhen --> 0
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 366 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 796 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0f:23:ea:58:70 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:0f:23:e5:db:c0 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:0f:23:ea:58:70 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:0f:23:e5:db:c0 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 796 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0f:23:ea:58:70 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:e5:db:c0 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:0f:23:ea:58:70 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:e5:db:c0 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
EAPOL: authWhile --> 0
EAPOL: SUPP_BE entering state TIMEOUT
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 796 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0f:23:ea:58:70 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:e5:db:c0 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:0f:23:ea:58:70 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0f:23:7f:2d:0f ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:e5:db:c0 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:0f:23:ef:d0:00 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:0f:23:ea:58:70 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=169
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE040b160c12182432043048606cdd160050f20101000050f20201000050f20201000050f201 RespIEs=01088b160c12182430483202606c)'
Association info event
req_ies - hexdump(len=53): 00 0b 41 43 48 45 52 4e 41 52 2d 42 47 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
resp_ies - hexdump(len=14): 01 08 8b 16 0c 12 18 24 30 48 32 02 60 6c
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:0f:23:ea:58:70
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:0f:23:ea:58:70
No keys have been configured - skip key clearing
Associated with 00:0f:23:ea:58:70
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=60): 01 00 00 38 01 01 00 38 01 00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52 4e 41 52 2d 42 47 2c 6e 61 73 69 64 3d 42 33 35 53 41 50 31 61 67 2e 6e 65 74 2c 70 6f 72 74 69 64 3d 30
Setting authentication timeout: 70 sec 0 usec
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_PAE entering state RESTART
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=1 method=1 vendor=0 vendorMethod=0
EAP: EAP entering state IDENTITY
CTRL-EVENT-EAP-STARTED EAP authentication started
EAP: EAP-Request Identity data - hexdump_ascii(len=51):
     00 6e 65 74 77 6f 72 6b 69 64 3d 41 43 48 45 52   _networkid=ACHER
     4e 41 52 2d 42 47 2c 6e 61 73 69 64 3d 42 33 35   NAR-BG,nasid=B35
     53 41 50 31 61 67 2e 6e 65 74 2c 70 6f 72 74 69   SAP1ag.net,porti
     64 3d 30                                          d=0
EAP: using real identity - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=14): 02 00 00 0a 02 01 00 0a 01 61 6d 33 39 34
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=46): 01 00 00 15 01 8f 00 15 11 01 00 08 5d 02 c9 3c 4f 94 b9 ad 61 6d 33 39 34 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=143 method=17 vendor=0 vendorMethod=0
EAP: EAP entering state GET_METHOD
EAP: configuration does not allow: vendor 0 method 17
EAP: vendor 0 method 17 not allowed
EAP: Building EAP-Nak (requested type 17 vendor=0 method=0 not allowed)
EAP: allowed methods - hexdump(len=1): 19
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=10): 02 00 00 06 02 8f 00 06 03 19
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=46): 01 00 00 06 01 90 00 06 19 21 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=144 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state GET_METHOD
EAP: Initialize selected EAP method: vendor 0 method 25 (PEAP)
EAP-PEAP: Phase2 EAP types - hexdump(len=8): 00 00 00 00 1a 00 00 00
TLS: Trusted root certificate(s) loaded
TLS: Include TLS Message Length in unfragmented packets
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
EAP: EAP entering state METHOD
SSL: Received packet(len=6) - Flags 0x21
EAP-PEAP: Start (server ver=1, own ver=1)
EAP-PEAP: Using PEAP version 1
SSL: (where=0x10 ret=0x1)
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:before/connect initialization
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write client hello A
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read server hello A
SSL: SSL_connect - want more data
SSL: 87 bytes pending from ssl_out
SSL: 87 bytes left to be sent out (of total 87 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=101): 02 00 00 61 02 90 00 61 19 81 00 00 00 57 16 03 01 00 52 01 00 00 4e 03 01 48 03 1f ba 00 2e d5 cd be ae e3 25 63 ca d3 db 30 f5 73 90 ce bf 15 36 99 76 7e dd a2 f2 5a 80 00 00 26 00 39 00 38 00 35 00 16 00 13 00 0a 00 33 00 32 00 2f 00 05 00 04 00 15 00 12 00 09 00 14 00 11 00 08 00 06 00 03 02 01 00
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=1016): 01 00 03 f4 01 91 03 f4 19 c1 00 00 07 bf 16 03 01 00 4a 02 00 00 46 03 01 48 03 1f b3 73 ce 25 d1 dd a9 07 df 69 d3 97 9c 09 b2 1a dc c9 ac fe d1 ab cb 14 ad e0 03 6a 3d 20 71 24 be dd d9 11 11 d8 90 d2 3d 85 f0 9a 92 3d c9 b5 59 fa b7 7a 97 90 b7 78 5a 70 33 1b 63 e4 00 35 00 16 03 01 07 62 0b 00 07 5e 00 07 5b 00 04 2a 30 82 04 26 30 82 03 8f a0 03 02 01 02 02 10 76 b4 32 52 e2 93 bb 5b 94 6e 11 11 63 16 9f b2 30 0d 06 09 2a 86 48 86 f7 0d 01 01 05 05 00 30 81 ce 31 0b 30 09 06 03 55 04 06 13 02 5a 41 31 15 30 13 06 03 55 04 08 13 0c 57 65 73 74 65 72 6e 20 43 61 70 65 31 12 30 10 06 03 55 04 07 13 09 43 61 70 65 20 54 6f 77 6e 31 1d 30 1b 06 03 55 04 0a 13 14 54 68 61 77 74 65 20 43 6f 6e 73 75 6c 74 69 6e 67 20 63 63 31 28 30 26 06 03 55 04 0b 13 1f 43 65 72 74 69 66 69 63 61 74 69 6f 6e 20 53 65 72 76 69 63 65 73 20 44 69 76 69 73 69 6f 6e 31 21 30 1f 06 03 55 04 03 13 18 54 68 61 77 74 65 20 50 72 65 6d 69 75 6d 20 53 65 72 76 65 72 20 43 41 31 28 30 26 06 09 2a 86 48 86 f7 0d 01 09 01 16 19 70 72 65 6d 69 75 6d 2d 73 65 72 76 65 72 40 74 68 61 77 74 65 2e 63 6f 6d 30 1e 17 0d 30 37 31 31 30 36 32 33 32 36 32 36 5a 17 0d 30 38 31 31 30 35 32 33 32 36 32 36 5a 30 81 a6 31 0b 30 09 06 03 55 04 06 13 02 41 55 31 18 30 16 06 03 55 04 08 13 0f 4e 65 77 20 53 6f 75 74 68 20 57 61 6c 65 73 31 13 30 11 06 03 55 04 07 13 0a 57 6f 6c 6c 6f 6e 67 6f 6e 67 31 21 30 1f 06 03 55 04 0a 13 18 55 6e 69 76 65 72 73 69 74 79 20 6f 66 20 57 6f 6c 6c 6f 6e 67 6f 6e 67 31 28 30 26 06 03 55 04 0b 13 1f 49 6e 66 6f 72 6d 61 74 69 6f 6e 20 54 65 63 68 6e 6f 6c 6f 67 79 20 53 65 72 76 69 63 65 73 31 1b 30 19 06 03 55 04 03 13 12 63 73 65 63 2e 61 64 2e 75 6f 77 2e 65 64 75 2e 61 75 30 82 01 22 30 0d 06 09 2a 86 48 86 f7 0d 01 01 01 05 00 03 82 01 0f 00 30 82 01 0a 02 82 01 01 00 ac e6 d8 e2 c5 db 3b 6e 44 3a 79 1f 01 da eb b5 98 14 f3 cc 2d 3f 5a 78 c2 42 cb 0b 62 35 d1 34 d4 be 4f da 77 d7 d8 a0 67 87 78 09 b1 1c 64 fc 7c 9e 1c b7 fd 45 1f 89 7a 41 3d d8 0b 41 4c 4d d0 82 e1 0b 70 c1 94 5f ae 58 77 46 b2 00 6e d3 1a 3b c5 c5 11 e0 a1 29 a7 57 92 ee c1 c6 ed b6 9a ab 3a bd 72 59 ba 26 79 93 2a 14 e2 87 d2 63 d2 9a 83 17 b7 04 66 54 5c f2 66 35 3d 45 47 38 9f 3a 06 77 6f 34 db 49 06 cd 54 3f 6f 83 2e a3 63 67 29 b5 80 46 db d5 6d bb 7b 55 63 95 da ca 34 db 64 a3 54 99 38 b7 b9 3a d3 5e bb 50 d7 75 97 d5 57 52 4a 3e 69 3c 7d c6 83 37 30 95 5c d8 db 65 76 0c ee af dc 4f 3f e2 82 05 e0 b8 20 f2 d7 10 e0 d9 e3 b0 92 b6 af c1 77 cd 62 87 d2 f6 88 dc 73 61 34 70 fa 00 80 38 a1 07 01 6f 02 a9 dd c1 cf 04 2a 8a b2 25 cf 80 21 27 ba 3b a9 c3 02 03 01 00 01 a3 81 a6 30 81 a3 30 1d 06 03 55 1d 25 04 16 30 14 06 08 2b 06 01 05 05 07 03 01 06 08 2b 06 01 05 05 07 03 02 30 40 06 03 55 1d 1f 04 39 30 37 30 35 a0 33 a0 31 86 2f 68 74 74 70 3a 2f 2f 63 72 6c 2e 74 68 61 77 74 65 2e 63 6f 6d 2f 54 68 61 77 74 65 50 72 65 6d 69 75 6d 53 65 72 76 65 72 43 41 2e 63 72 6c 30 32 06 08 2b 06 01 05 05 07 01 01 04 26 30 24 30 22 06 08 2b 06 01 05 05 07 30 01 86 16 68 74 74 70 3a 2f 2f 6f 63 73 70 2e 74 68 61 77 74 65 2e 63 6f 6d 30 0c 06
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=145 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=1012) - Flags 0xc1
SSL: TLS Message Length: 1983
SSL: Need 981 bytes more input data
SSL: Building ACK
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=10): 02 00 00 06 02 91 00 06 19 01
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=991): 01 00 03 db 01 92 03 db 19 01 03 55 1d 13 01 01 ff 04 02 30 00 30 0d 06 09 2a 86 48 86 f7 0d 01 01 05 05 00 03 81 81 00 92 09 00 ac a3 eb f5 f7 94 d6 cd 24 dc 8a bc eb 04 44 64 6e 1b a9 1d 8b 12 5d c4 98 7c b6 b7 5e 1e a5 5d da b1 85 56 44 c2 bb 53 4f bd f5 2d a1 5d a0 31 13 5b c7 33 43 00 f2 7c 36 fb 0e 62 c5 14 94 ed 2b d2 9a 1c 90 e8 cf a9 e7 06 4b 97 9e 0b 16 84 a5 cd d4 e9 21 fd 68 5a 7b d7 8a 42 c4 db 9c a9 1b 15 ac 56 f8 20 48 c1 a0 22 b4 69 9c 62 b1 53 94 df 9c 18 ba b4 51 c4 a7 53 99 e2 41 00 03 2b 30 82 03 27 30 82 02 90 a0 03 02 01 02 02 01 01 30 0d 06 09 2a 86 48 86 f7 0d 01 01 04 05 00 30 81 ce 31 0b 30 09 06 03 55 04 06 13 02 5a 41 31 15 30 13 06 03 55 04 08 13 0c 57 65 73 74 65 72 6e 20 43 61 70 65 31 12 30 10 06 03 55 04 07 13 09 43 61 70 65 20 54 6f 77 6e 31 1d 30 1b 06 03 55 04 0a 13 14 54 68 61 77 74 65 20 43 6f 6e 73 75 6c 74 69 6e 67 20 63 63 31 28 30 26 06 03 55 04 0b 13 1f 43 65 72 74 69 66 69 63 61 74 69 6f 6e 20 53 65 72 76 69 63 65 73 20 44 69 76 69 73 69 6f 6e 31 21 30 1f 06 03 55 04 03 13 18 54 68 61 77 74 65 20 50 72 65 6d 69 75 6d 20 53 65 72 76 65 72 20 43 41 31 28 30 26 06 09 2a 86 48 86 f7 0d 01 09 01 16 19 70 72 65 6d 69 75 6d 2d 73 65 72 76 65 72 40 74 68 61 77 74 65 2e 63 6f 6d 30 1e 17 0d 39 36 30 38 30 31 30 30 30 30 30 30 5a 17 0d 32 30 31 32 33 31 32 33 35 39 35 39 5a 30 81 ce 31 0b 30 09 06 03 55 04 06 13 02 5a 41 31 15 30 13 06 03 55 04 08 13 0c 57 65 73 74 65 72 6e 20 43 61 70 65 31 12 30 10 06 03 55 04 07 13 09 43 61 70 65 20 54 6f 77 6e 31 1d 30 1b 06 03 55 04 0a 13 14 54 68 61 77 74 65 20 43 6f 6e 73 75 6c 74 69 6e 67 20 63 63 31 28 30 26 06 03 55 04 0b 13 1f 43 65 72 74 69 66 69 63 61 74 69 6f 6e 20 53 65 72 76 69 63 65 73 20 44 69 76 69 73 69 6f 6e 31 21 30 1f 06 03 55 04 03 13 18 54 68 61 77 74 65 20 50 72 65 6d 69 75 6d 20 53 65 72 76 65 72 20 43 41 31 28 30 26 06 09 2a 86 48 86 f7 0d 01 09 01 16 19 70 72 65 6d 69 75 6d 2d 73 65 72 76 65 72 40 74 68 61 77 74 65 2e 63 6f 6d 30 81 9f 30 0d 06 09 2a 86 48 86 f7 0d 01 01 01 05 00 03 81 8d 00 30 81 89 02 81 81 00 d2 36 36 6a 8b d7 c2 5b 9e da 81 41 62 8f 38 ee 49 04 55 d6 d0 ef 1c 1b 95 16 47 ef 18 48 35 3a 52 f4 2b 6a 06 8f 3b 2f ea 56 e3 af 86 8d 9e 17 f7 9e b4 65 75 02 4d ef cb 09 a2 21 51 d8 9b d0 67 d0 ba 0d 92 06 14 73 d4 93 cb 97 2a 00 9c 5c 4e 0c bc fa 15 52 fc f2 44 6e da 11 4a 6e 08 9f 2f 2d e3 f9 aa 3a 86 73 b6 46 53 58 c8 89 05 bd 83 11 b8 73 3f aa 07 8d f4 42 4d e7 40 9d 1c 37 02 03 01 00 01 a3 13 30 11 30 0f 06 03 55 1d 13 01 01 ff 04 05 30 03 01 01 ff 30 0d 06 09 2a 86 48 86 f7 0d 01 01 04 05 00 03 81 81 00 26 48 2c 16 c2 58 fa e8 16 74 0c aa aa 5f 54 3f f2 d7 c9 78 60 5e 5e 6e 37 63 22 77 36 7e b2 17 c4 34 b9 f5 08 85 fc c9 01 38 ff 4d be f2 16 42 43 e7 bb 5a 46 fb c1 c6 11 1f f1 4a b0 28 46 c9 c3 c4 42 7d bc fa ab 59 6e d5 b7 51 88 11 e3 a4 85 19 6b 82 4c a4 0c 12 ad e9 a4 ae 3f f1 c3 49 65 9a 8c c5 c8 3e 25 b7 94 99 bb 92 32 71 07 f0 86 5e ed 50 27 a6 0d a6 23 f9 bb cb a6 07 14 42 16 03 01 00 04 0e 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=146 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=987) - Flags 0x01
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server hello A
TLS: tls_verify_cb - preverify_ok=1 err=0 (ok) depth=1 buf='/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com'
TLS: tls_verify_cb - preverify_ok=1 err=0 (ok) depth=0 buf='/C=AU/ST=New South Wales/L=Wollongong/O=University of Wollongong/OU=Information Technology Services/CN=csec.ad.uow.edu.au'
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server certificate A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server done A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write client key exchange A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write change cipher spec A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write finished A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 flush data
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read finished A
SSL: SSL_connect - want more data
SSL: 326 bytes pending from ssl_out
SSL: 326 bytes left to be sent out (of total 326 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=340): 02 00 01 50 02 92 01 50 19 81 00 00 01 46 16 03 01 01 06 10 00 01 02 01 00 7b 06 83 67 74 cd ec 31 95 23 1d 13 54 bd f1 97 73 f0 3c 1f 52 ff 35 11 55 57 ac 99 fb 82 38 44 56 68 fa 86 de 45 12 00 ee 61 27 ff 39 af b3 4c 08 ec b7 30 59 ba 5b 64 75 e0 47 5d 0a c8 34 e6 d8 14 db f6 97 36 6f a6 07 de 49 3f e8 62 d1 95 28 4b 3f a7 9f e6 98 aa 4c ed ca c9 30 b0 5f f0 68 d8 08 7e b1 c4 e0 3b 81 c1 fb 41 73 f7 46 e5 9a 5d 51 b2 28 0b 13 6f 4a fa 45 1c 1e 12 6e 30 a8 86 d2 7f 96 8f be 1f 0f f1 c3 ef b4 f2 5e a7 f1 1b c7 06 09 84 e6 69 3b 67 bf 54 b5 12 f4 56 c1 95 f4 54 5c a9 86 d7 cf 0d 5a d4 61 9a af 62 11 86 e8 6d 40 7d 9a 4c 95 b8 48 a9 eb 80 a6 6e c0 6f 88 b1 4a 0b f1 58 48 2e 8c 31 e3 ad ee 49 49 1e df ce 9a 78 5e 79 9e 8e 8c 42 d3 37 73 fa 68 f7 30 02 b3 5c 6c dc cf 84 69 c1 df 47 dc 77 98 a7 d4 04 3e e8 17 ed 58 1d 59 0d e8 22 23 fe 14 03 01 00 01 01 16 03 01 00 30 c9 48 52 fb 9e b2 da 72 9d 51 5e 2c a3 cc 64 7b 05 f8 35 94 5f cb 07 e1 7b 52 29 7c fb 2f 18 74 51 be 71 55 be 51 4b 90 01 ce 1d 1b 7a d2 22 c8
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=73): 01 00 00 45 01 93 00 45 19 81 00 00 00 3b 14 03 01 00 01 01 16 03 01 00 30 66 07 32 32 c0 d0 68 ce 83 53 c9 73 ca f2 73 c8 b8 8f f6 00 54 be b9 c4 40 33 60 24 2b 06 b3 85 3e 4e 1a 1b d4 12 6a 26 ea 15 b4 8a e0 61 7c 36
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=147 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=69) - Flags 0x81
SSL: TLS Message Length: 59
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read finished A
SSL: (where=0x20 ret=0x1)
SSL: (where=0x1002 ret=0x1)
SSL: 0 bytes pending from ssl_out
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
SSL: No data to be sent out
EAP-PEAP: TLS done, proceed to Phase 2
EAP-PEAP: using label 'client EAP encryption' in key derivation
EAP-PEAP: Derived key - hexdump(len=64): [REMOVED]
SSL: Building ACK
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=10): 02 00 00 06 02 93 00 06 19 01
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=47): 01 00 00 2b 01 94 00 2b 19 01 17 03 01 00 20 fd 75 30 e6 7c f9 33 f7 01 d0 4a 25 88 be 8d 2d dc d7 93 06 79 c6 55 aa ff 0a 1d 2a 28 bf 79 1e
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=148 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=43) - Flags 0x01
EAP-PEAP: received 37 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=5): 01 75 00 05 01
EAP-PEAP: received Phase 2: code=1 identifier=117 length=5
EAP-PEAP: Phase 2 Request: type=1
EAP: using real identity - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=10): [REMOVED]
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=84): 02 00 00 50 02 94 00 50 19 01 17 03 01 00 20 41 25 14 f4 2c cc 9f 12 f5 47 95 a7 f1 36 c9 8b 6a 80 e7 cf b1 0b 1f 14 22 de 23 d3 3b 57 19 86 17 03 01 00 20 20 3e 0e cf 70 26 54 23 42 39 d2 75 1d ac a7 9d 7c 8f bf 80 f2 c5 cd 76 98 44 16 b0 d4 42 8d 57
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=63): 01 00 00 3b 01 95 00 3b 19 01 17 03 01 00 30 f0 70 bd ea ac 6b 4a 39 b8 48 0d 29 70 55 0f c9 80 2c b5 4b 0f ed 18 86 86 cb 8c 8d d8 6b 29 1a b2 5f 8a 70 17 5e 60 93 5e f4 45 33 c9 22 b1 65
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=149 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=59) - Flags 0x01
EAP-PEAP: received 53 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=24): 01 76 00 18 06 45 6e 74 65 72 20 79 6f 75 72 20 70 61 73 73 77 6f 72 64
EAP-PEAP: received Phase 2: code=1 identifier=118 length=24
EAP-PEAP: Phase 2 Request: type=6
EAP-PEAP: Phase 2 Request: Nak type=6
EAP-PEAP: Allowed Phase2 EAP types - hexdump(len=8): 00 00 00 00 1a 00 00 00
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=6): [REMOVED]
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=84): 02 00 00 50 02 95 00 50 19 01 17 03 01 00 20 c3 2c f5 9c 40 23 dd bf 7b 85 46 8d 2d ff 88 3f 46 2b 69 cf 8d 6c e0 a0 b7 39 f7 2a 7c 39 0c f6 17 03 01 00 20 88 ea 04 4f fe e8 fd 62 ac 22 68 d8 64 0e 1e 9c dc 27 50 e6 79 45 d9 2f 5c 8a 57 11 10 84 52 43
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=79): 01 00 00 4b 01 96 00 4b 19 01 17 03 01 00 40 d9 9a f1 88 3a f9 2c dd c4 74 6b a5 42 4a 39 d6 f2 1d 4b ba a2 ac c1 df 86 26 0d 8d c7 47 9b 21 41 e4 49 0f 35 b4 dd 0a 34 7a 5e d6 22 c5 e4 3b 13 9e e9 e0 7b c1 80 61 b5 8c 2b 83 1c 1c ee c0
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=150 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=75) - Flags 0x01
EAP-PEAP: received 69 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=31): 01 77 00 1f 1a 01 77 00 1a 10 fc a2 33 1e e8 06 99 28 ce 9f e0 24 34 7d 55 13 43 53 45 43 31
EAP-PEAP: received Phase 2: code=1 identifier=119 length=31
EAP-PEAP: Phase 2 Request: type=26
EAP-PEAP: Selected Phase 2 EAP vendor 0 method 26
EAP-MSCHAPV2: RX identifier 119 mschapv2_id 119
EAP-MSCHAPV2: Received challenge
EAP-MSCHAPV2: Authentication Servername - hexdump_ascii(len=5):
     43 53 45 43 31                                    CSEC1
EAP-MSCHAPV2: Generating Challenge Response
EAP-MSCHAPV2: auth_challenge - hexdump(len=16): fc a2 33 1e e8 06 99 28 ce 9f e0 24 34 7d 55 13
EAP-MSCHAPV2: peer_challenge - hexdump(len=16): 9d 08 a1 cf 2c 6a 05 e2 3e fa 97 41 9f e5 97 de
EAP-MSCHAPV2: username - hexdump_ascii(len=5):
     61 6d 33 39 34                                    am394
EAP-MSCHAPV2: password - hexdump_ascii(len=8): [REMOVED]
EAP-MSCHAPV2: response - hexdump(len=24): 49 f2 fe 71 b5 0e 4c 81 be 21 c4 ba 8c b1 17 08 97 6b af 8c 8f cd a8 29
EAP-MSCHAPV2: TX identifier 119 mschapv2_id 119 (response)
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=64): [REMOVED]
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=148): 02 00 00 90 02 96 00 90 19 01 17 03 01 00 20 6d 36 57 2c c6 ad bc eb ff ee a3 ae cf be 27 e0 89 b6 3b a5 20 f9 41 5a 77 b1 d3 60 e8 6b 73 b7 17 03 01 00 60 75 b8 98 54 ff 6e eb e8 8d d3 af 43 bd a6 05 fa 0f d4 a7 07 26 ca eb 0b 51 c3 cc 07 8f 39 60 a8 b9 de ca ea c4 82 0b 55 f7 f4 98 c8 42 cf d5 69 c0 c5 b8 6e ef e9 7b dc 24 33 93 ac ee 88 43 73 33 7f 26 82 83 15 1d f2 b0 d3 1c d1 81 92 c9 9c b6 58 39 73 b1 57 f4 34 08 75 5e 9c c8 67 77 72
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=95): 01 00 00 5b 01 97 00 5b 19 01 17 03 01 00 50 cc ee f4 21 2f 1b d4 cc 45 aa 89 37 23 12 98 cc 84 87 7f c4 c3 e5 26 8d 2d 5f 76 7b 10 37 b2 b8 68 9d 27 7f 6b 96 45 39 c4 d2 94 49 54 03 c6 68 7c 00 60 36 f9 a1 54 a1 25 eb 4f 9e 1c c7 e8 b2 20 30 99 a7 30 0d 8f c6 62 2f d3 39 e1 b8 55 6e
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=151 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=91) - Flags 0x01
EAP-PEAP: received 85 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=51): 01 78 00 33 1a 03 77 00 2e 53 3d 35 43 32 33 43 42 44 45 34 34 31 38 37 34 44 34 39 32 30 36 31 30 36 31 34 31 46 33 32 39 36 42 32 39 41 43 38 45 38 30
EAP-PEAP: received Phase 2: code=1 identifier=120 length=51
EAP-PEAP: Phase 2 Request: type=26
EAP-MSCHAPV2: RX identifier 120 mschapv2_id 119
EAP-MSCHAPV2: Received success
EAP-MSCHAPV2: Success message - hexdump_ascii(len=0):
EAP-MSCHAPV2: Authentication succeeded
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=6): [REMOVED]
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=84): 02 00 00 50 02 97 00 50 19 01 17 03 01 00 20 00 11 cf ab 2c 9b e9 2d 37 3e d0 38 4f 9b 92 83 50 63 d5 b8 2d f0 7d 55 d7 a7 71 a7 ef 22 9b c1 17 03 01 00 20 3a 15 be 9b da 3f 45 71 9e 5a fa 5f 27 12 5e 60 1f 13 f1 a3 fa b9 5c 6e 2b a3 20 44 1c f1 b9 30
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=47): 01 00 00 2b 01 98 00 2b 19 01 17 03 01 00 20 16 a2 d0 25 b0 04 f3 1e 01 be e7 44 98 46 ab 16 4e 5f 52 2e 40 7b 83 4f 88 60 35 36 7b b8 19 91
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=152 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=43) - Flags 0x01
EAP-PEAP: received 37 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=11): 01 79 00 0b 21 80 03 00 02 00 01
EAP-PEAP: received Phase 2: code=1 identifier=121 length=11
EAP-PEAP: Phase 2 Request: type=33
EAP-TLV: Received TLVs - hexdump(len=6): 80 03 00 02 00 01
EAP-TLV: Result TLV - hexdump(len=2): 00 01
EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=11): [REMOVED]
EAP: method process -> ignore=FALSE methodState=DONE decision=UNCOND_SUCC
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=84): 02 00 00 50 02 98 00 50 19 01 17 03 01 00 20 96 f3 d3 45 c2 01 9d 50 ce e7 af 82 74 6e d2 49 c4 b6 d2 22 60 74 ec 6e 30 ed 40 c6 39 8e 39 94 17 03 01 00 20 58 ac 00 79 1c 42 0f 20 28 68 e5 17 f3 1e bb 76 10 4b 2c 3c 42 1f e4 04 91 62 15 1d ea 52 93 2d
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=46): 01 00 00 04 03 98 00 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Success
EAP: EAP entering state SUCCESS
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
EAPOL: SUPP_BE entering state RECEIVE
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_BE entering state IDLE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 24 cf 50 84 d7 b9 73 4e a1 b0 b7 1c 44 ff 19 80 3c 3a a4 f8 1d 76 ab 2e 45 8c 6e d0 3e 8b bf 92 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 24 cf 50 84 d7 b9 73 4e a1 b0 b7 1c 44 ff 19 80 3c 3a a4 f8 1d 76 ab 2e 45 8c 6e d0 3e 8b bf 92
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 24 cf 50 84 d7 b9 73 4e a1 b0 b7 1c 44 ff 19 80 3c 3a a4 f8 1d 76 ab 2e 45 8c 6e d0 3e 8b bf 92 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:0f:23:ea:58:70 (ver=1)
WPA: PMK from EAPOL state machines - hexdump(len=32): [REMOVED]
WPA: Renewed SNonce - hexdump(len=32): a4 70 ba d7 4e ad 84 f5 4e f3 6a 5e 7f e6 04 9a f8 68 35 cf a0 3c fc 37 96 42 25 6c 79 98 73 c4
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 02 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 a4 70 ba d7 4e ad 84 f5 4e f3 6a 5e 7f e6 04 9a f8 68 35 cf a0 3c fc 37 96 42 25 6c 79 98 73 c4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0d 6b 67 a1 a3 5e 21 d4 0c 3a 37 21 47 4d 70 19 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 24 cf 50 84 d7 b9 73 4e a1 b0 b7 1c 44 ff 19 80 3c 3a a4 f8 1d 76 ab 2e 45 8c 6e d0 3e 8b bf 92 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 40 ab a1 56 42 51 a4 8e 10 13 da 14 0e b0 75 84 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=121
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=26
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 24 cf 50 84 d7 b9 73 4e a1 b0 b7 1c 44 ff 19 80 3c 3a a4 f8 1d 76 ab 2e 45 8c 6e d0 3e 8b bf 92
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 40 ab a1 56 42 51 a4 8e 10 13 da 14 0e b0 75 84
WPA: RX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 24 cf 50 84 d7 b9 73 4e a1 b0 b7 1c 44 ff 19 80 3c 3a a4 f8 1d 76 ab 2e 45 8c 6e d0 3e 8b bf 92 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 40 ab a1 56 42 51 a4 8e 10 13 da 14 0e b0 75 84 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:0f:23:ea:58:70 (ver=1)
WPA: IE KeyData - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 02 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 1c ea e4 ab 2f 6f d2 3f 59 90 81 5f f7 df ae 43 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:0f:23:ea:58:70
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 03 24 cf 50 84 d7 b9 73 4e a1 b0 b7 1c 44 ff 19 80 3c 3a a4 f8 1d 76 ab 2e 45 8c 6e d0 3e 8b bf 90 b8 83 e7 40 f1 85 71 c6 ea 52 76 84 e7 14 76 a8 c1 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 27 f5 60 3a 3c e0 bd 43 e5 d7 18 6b 6a 31 cc 9e 00 20 57 28 e6 84 36 c2 fd 1d 36 0c 71 67 e2 71 c1 4e c7 71 7a 17 2a d1 48 b6 28 31 1e c2 2d 98 03 22
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x3a1 (ver=1 keyidx=2 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 24 cf 50 84 d7 b9 73 4e a1 b0 b7 1c 44 ff 19 80 3c 3a a4 f8 1d 76 ab 2e 45 8c 6e d0 3e 8b bf 90
  key_iv - hexdump(len=16): b8 83 e7 40 f1 85 71 c6 ea 52 76 84 e7 14 76 a8
  key_rsc - hexdump(len=8): c1 05 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 27 f5 60 3a 3c e0 bd 43 e5 d7 18 6b 6a 31 cc 9e
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 03 24 cf 50 84 d7 b9 73 4e a1 b0 b7 1c 44 ff 19 80 3c 3a a4 f8 1d 76 ab 2e 45 8c 6e d0 3e 8b bf 90 b8 83 e7 40 f1 85 71 c6 ea 52 76 84 e7 14 76 a8 c1 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 27 f5 60 3a 3c e0 bd 43 e5 d7 18 6b 6a 31 cc 9e 00 20 57 28 e6 84 36 c2 fd 1d 36 0c 71 67 e2 71 c1 4e c7 71 7a 17 2a d1 48 b6 28 31 1e c2 2d 98 03 22
WPA: RX message 1 of Group Key Handshake from 00:0f:23:ea:58:70 (ver=1)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=2 tx=0).
WPA: RSC - hexdump(len=6): c1 05 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 02 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6a f9 3e a2 13 4f cb 3e ae 59 7e a4 d1 74 52 de 00 00
WPA: Key negotiation completed with 00:0f:23:ea:58:70 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
Removed BSSID 00:0f:23:ea:58:70 from blacklist
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:0f:23:ea:58:70 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: SUPP_PAE entering state AUTHENTICATED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: authWhile --> 0
EAPOL: idleWhile --> 0
zRTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 440 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0f:23:ea:58:70 ssid='ACHERNAR-BG' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:0f:23:ea:58:70 ssid='ACHERNAR-BG'
Try to find non-WPA AP
Already associated with the selected AP.
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_deauthenticate
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
EAP: deinitialize previously used EAP method (25, PEAP) at EAP deinit
ENGINE: engine deinit
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6

```

Note that the above case deauthenticates at the end because I hit ^C.

This is a case when it connects successfully and then disconnects for some reason

```

State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=2 tx=0).
WPA: RSC - hexdump(len=6): 55 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 02 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
00 00 00 00 00 5d ce 37 03 84 3a 70 b7 29 97 8e 8b e6 c0 1c 7d 00 00
WPA: Key negotiation completed with 00:0f:23:ea:58:70 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
Removed BSSID 00:0f:23:ea:58:70 from blacklist
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:0f:23:ea:58:70 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: SUPP_PAE entering state AUTHENTICATED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 2
Try to find WPA-enabled AP
Try to find non-WPA AP
Selecting BSS from priority group 1
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=11):
     41 43 48 45 52 4e 41 52 2d 42 47                  ACHERNAR-BG
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 583 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 2
Try to find WPA-enabled AP
0: 00:0e:d7:52:33:2d ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0e:83:ce:06:a8 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:ef:d0:00 ssid='ACHERNAR-BG' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:0e:d7:52:33:2d ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0e:83:ce:06:a8 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:ef:d0:00 ssid='ACHERNAR-BG' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Selecting BSS from priority group 1
Try to find WPA-enabled AP
0: 00:0e:d7:52:33:2d ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:0e:83:ce:06:a8 ssid='' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:23:ef:d0:00 ssid='ACHERNAR-BG' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:0f:23:ef:d0:00 ssid='ACHERNAR-BG'
Try to find non-WPA AP
Trying to associate with 00:0f:23:ef:d0:00 (SSID='ACHERNAR-BG' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 1 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_drop_unencrypted
State: COMPLETED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=19
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=149
WEXT: Custom wireless event: 
'ASSOCINFO(ReqIE040b160c12182432043048606cdd160050f20101000050f20201000050f20201000050f201 
RespIEs=01028b16)'
Association info event

```

I cant think of anything else that would be useful. Hopefully, someone figures out whats going wrong here!

---

### Post by lexxonnet on 2008-05-19
Hmm... no one else having any similar problems? From what I've seen at my uni, it seems to be a fairly common occurence. Anyone has any idea where I should file a bug report?

---

### Post by wasutton3 on 2008-08-08
i have the exact same problem and as far as i can tell, no solution has been found. this is a major issue and at my university is the only thing keeping so many from switching to ubuntu.

---

