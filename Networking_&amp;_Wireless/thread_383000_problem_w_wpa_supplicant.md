---
title: "problem w/ wpa_supplicant"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by eldersoares on 2007-03-12
actually, the problem must be w/ me... :) 
outputs:

**$   sudo iwconfig**
[I]Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:150   Missed beacon:0

sit0      no wireless extensions.

[/I]

**$  sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dmadwifi -w -dd**

[I]Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 705 - start of a new network block
ssid - hexdump_ascii(len=12):
     4e 65 74 77 6f 72 6b 45 73 73 69 64               NetworkEssid    
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='NetworkEssid'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=16 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:de:b3:0b:ec
wpa_driver_madwifi_del_key: keyidx=0
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_del_key: keyidx=1
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_del_key: keyidx=2
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_del_key: keyidx=3
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=12):
     4e 65 74 77 6f 72 6b 45 73 73 69 64               NetworkEssid    
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 712 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
0: 00:12:17:d8:4b:8e ssid='ellecktra' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:08:a1:9b:ab:7b ssid='Maipu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:14:51:71:9a:7d ssid='Apple Network 719a7d' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b1a len=8
Scan timeout - try to get results
Received 219 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:08:a1:9b:ab:7b ssid='Maipu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=12):
     4e 65 74 77 6f 72 6b 45 73 73 69 64               NetworkEssid    
Wireless event: cmd=0x8b1a len=21[/I]

and then i ctrl+c'ed
**what is the problem?!?!??!?! **before i move, it worked very well...! now, it only works under win :mad: :mad:
thanx!

---

### Post by eldersoares on 2007-03-14
**PLZZZZ HEEEEELP!!!!!!!!!!!!!!** what can it be? before i move it worked so fine... now the network manager never finds a network!!! :( :confused:

---

