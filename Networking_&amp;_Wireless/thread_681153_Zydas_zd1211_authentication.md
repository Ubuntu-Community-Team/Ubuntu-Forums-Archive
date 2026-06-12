---
title: "Zydas zd1211 authentication"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by zacmarco on 2008-01-28
Hi all!!
First of all, let me say I've tried to solve the problem reading previous posts, but NO WAY!
So... my problem is that I've a Zydas wireless card, I'm using the zd1211rw driver (I've compiled a Vanilla Kernel) and downloaded latest firmware for the card.
I've a wireless router (Xavi... uhu?!?), with the following configuration:

SECURITY: wpa/wpa2-psk
ENCRYPTION: AES/CCMP(WPA2)
ESSID: ZacNET

It follows my wpa_supplicant.conf file

-----------------------------------------------
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="ZacNET"
    scan_ssid=1
    psk="<my_password>i"
    key_mgmt=WPA-PSK    
    proto=RSN WPA
    pairwise=CCMP TKIP
}
------------------------------------------------

I'm trying launching wpa_supplicant with the command

wpa_supplicant -i eth2 -c /etc/wpa_supplicant.conf -D wext -d

But it doesn't work. Here's command's output

--------------------------------------------------------
Initializing interface 'eth2' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='ZacNET'
Initializing interface (2) 'eth2'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Interface eth2 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=20 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:02:72:57:a1:34
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
Added interface eth2
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth2' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     5a 61 63 4e 45 54                                 ZacNET          
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 1058 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:17:c2:49:fd:9d ssid='Alice-38545662' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:1b:63:2a:be:60 ssid='Airport' wpa_ie_len=24 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
2: 00:01:38:8e:5f:43 ssid='ZacNET' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:01:38:8e:5f:43 ssid='ZacNET'
Try to find non-WPA AP
Trying to associate with 00:01:38:8e:5f:43 (SSID='ZacNET' freq=2457 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 05 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
ioctl[SIOCSIWFREQ]: Operation not permitted
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: added PMKSA cache candidate 00:01:38:8e:5f:43 prio 1000
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 1549 bytes of scan results (6 BSSes)
Scan results: 6
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:01:38:8e:5f:43 ssid='ZacNET' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:01:38:8e:5f:43 ssid='ZacNET'
Try to find non-WPA AP
Already associated with the selected AP.
RSN: added PMKSA cache candidate 00:01:38:8e:5f:43 prio 1000
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth2
State: ASSOCIATING -> DISCONNECTED
------------------------------------------------------------

I can't understand the reason for it can't work!

Can you help me? Thanks a lot!

Marco

--------------------------------------------------------------
**************************************************************

OK! I've found the solution!
It was a too old version of the zd1211rw driver (it seems an ioctl not correctly implemented), the one in the 2.6.19.2 kernel.
Now I've compiled the 2.6.24 Vanilla Kernel and it's all OK.

Thanks

    Marco

---

