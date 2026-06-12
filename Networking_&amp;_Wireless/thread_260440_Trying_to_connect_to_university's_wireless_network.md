---
title: "Trying to connect to university's wireless network"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by jjramsey on 2006-09-18
I'm trying to connect to my university's wireless network under Linux. They use LEAP authentication. I know my username, jjr19, and my password, and I know the domain is called UANET, which I've been told is in all caps. The university network uses Cisco access points. On Windows XP, I can indeed connect to the network. My wireless card is an ipw3945.

I tried this HOWTO:

[http://www.ubuntuforums.org/showthread.php?t=235655](http://www.ubuntuforums.org/showthread.php?t=235655)

but the CVS version of NetworkManager just keeps popping up a dialog asking for the passphrase (and IIRC, if I use the "Wireless security:" dropdown menu, and choose "LEAP" it asks for my username and password again).

I also tried wpa_supplicant, with no success. This is the config file that I have:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="tsunami"
        key_mgmt=IEEE8021X
        eap=LEAP
        identity="jjr19"
        password="XXXX"
}

```

This is the output from running "sudo wpa_supplicant -c/home/jjramsey/Wireless-stuff/mywpasupp.conf -ieth1 -Dwext -dd":

```
Initializing interface 'eth1' conf '/home/jjramsey/Wireless-stuff/mywpasupp.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/home/jjramsey/Wireless-stuff/mywpasupp.conf' -> '/home/jjramsey/Wireless-stuff/mywpasupp.conf'
Reading configuration file '/home/jjramsey/Wireless-stuff/mywpasupp.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 8 - start of a new network block
ssid - hexdump_ascii(len=7):
     74 73 75 6e 61 6d 69                              tsunami         
key_mgmt: 0x8
eap methods - hexdump(len=2): 11 00
identity - hexdump_ascii(len=5):
     6a 6a 72 31 39                                    jjr19           
password - hexdump_ascii(len=8): [REMOVED]
Priority group 0
   id=0 ssid='tsunami'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=16 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:13:02:9c:47:e4
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 845 bytes of scan results (5 BSSes)
Scan results: 5
Selecting BSS from priority group 0
0: 00:40:96:47:ae:49 ssid='tsunami' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:40:96:51:86:24 ssid='tsunami' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:40:96:47:87:66 ssid='tsunami' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:40:96:40:56:94 ssid='tsunami' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:40:96:51:79:0c ssid='tsunami' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
   selected non-WPA AP 00:40:96:47:ae:49 ssid='tsunami'
Trying to associate with 00:40:96:47:ae:49 (SSID='tsunami' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x4
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=16
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
--snip--

```

This is what I get from running "iwlist eth1 scan":

```
eth1      Scan completed :
          Cell 01 - Address: 00:40:96:51:86:24
                    ESSID:"tsunami"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=54/100  Signal level=-76 dBm  Noise level=-76 dBm
                    Extra: Last beacon: 124ms ago
          Cell 02 - Address: 00:40:96:47:87:66
                    ESSID:"tsunami"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=49/100  Signal level=-79 dBm  Noise level=-79 dBm
                    Extra: Last beacon: 124ms ago
          Cell 03 - Address: 00:40:96:47:AE:49
                    ESSID:"tsunami"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=55/100  Signal level=-75 dBm  Noise level=-75 dBm
                    Extra: Last beacon: 128ms ago
          Cell 04 - Address: 00:17:0E:9E:70:F0
                    ESSID:"tsunami"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=46/100  Signal level=-81 dBm  Noise level=-81 dBm
                    Extra: Last beacon: 248ms ago
          Cell 05 - Address: 00:40:96:51:79:0C
                    ESSID:"tsunami"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=43/100  Signal level=-83 dBm  Noise level=-83 dBm
                    Extra: Last beacon: 168ms ago
          Cell 06 - Address: 00:40:96:51:4D:8B
                    ESSID:"tsunami"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=33/100  Signal level=-89 dBm  Noise level=-89 dBm
                    Extra: Last beacon: 244ms ago
          Cell 07 - Address: 00:40:96:40:56:94
                    ESSID:"tsunami"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=42/100  Signal level=-84 dBm  Noise level=-84 dBm
                    Extra: Last beacon: 196ms ago
          Cell 08 - Address: 00:40:96:51:78:9F
                    ESSID:"tsunami"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=49/100  Signal level=-79 dBm  Noise level=-79 dBm
                    Extra: Last beacon: 116ms ago


```

Apparently, the wireless card itself works. The ipw3945d daemon is running in the background as it should, and the linux-restricted-modules are installed, etc.

What am I missing here? Why can't I authenticate?

---

