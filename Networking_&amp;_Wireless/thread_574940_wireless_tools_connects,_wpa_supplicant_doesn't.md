---
title: "wireless_tools connects, wpa_supplicant doesn't"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by lubob on 2007-10-13
Hi All

I am running feisty on an old IBM a20m thinkpad with a wireless pcmcia card from Sitecom, type WL-140

I managed to get up and running by using the windows driver and ndiswrapper.

I can also setup and use WEP encoding when using the Gnome Wireless_tool.
As WEP is not secure I'd like to switch to WPA or WPA2 by using wpa_supplicant.

However, what ever I tried, I can not connect to my Access Point regardless which configuration I am using.

I have tested all kind of settings, none works.

Here is my wpa_supplicant.conf:

[FONT="Lucida Console"]ap_scan=1
network={
        ssid="Zaphod"
        scan_ssid=1
        key_mgmt=NONE
        wep_tx_keyidx=0
        wep_key0="testi"
}[/FONT]


I am testing this configuration with

~# sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d

which will create this output:

[FONT="Lucida Console"]
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=1
Priority group 0
   id=0 ssid='Zaphod'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0c:f6:14:cf:ca
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     5a 61 70 68 6f 64                                 Zaphod          
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 223 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:04:0e:f7:4f:ae ssid='Zaphod' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
   selected non-WPA AP 00:04:0e:f7:4f:ae ssid='Zaphod'
Trying to associate with 00:04:0e:f7:4f:ae (SSID='Zaphod' freq=2447 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=1 seq_len=0 key_len=5
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:04:0e:f7:4f:ae into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=48
AssocReq IE wireless event - hexdump(len=40): 00 06 5a 61 70 68 6f 64 01 04 02 04 0b 16 32 08 0c 12 18 24 30 48 60 6c dd 0e 00 10 91 01 03 00 a8 0c 02 02 00 00 04 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:04:0e:f7:4f:ae
Association info event
req_ies - hexdump(len=40): 00 06 5a 61 70 68 6f 64 01 04 02 04 0b 16 32 08 0c 12 18 24 30 48 60 6c dd 0e 00 10 91 01 03 00 a8 0c 02 02 00 00 04 00
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
WPA: clearing own WPA/RSN IE
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:04:0e:f7:4f:ae
Associated with 00:04:0e:f7:4f:ae
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
Removed BSSID 00:04:0e:f7:4f:ae from blacklist
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:04:0e:f7:4f:ae completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added

[/FONT]

the last line about wlan0 looks fine, but I can not get any connection, for example when using ping.
I can run "dhclient wlan0", this will provide me with an IP, but nothing else.

Thanks a lot for help

Lucius

---

### Post by lubob on 2007-10-13
Additional Information:

Getting an IP Address does not work anymore. I have written so because I think it worked some hours ago, but for the moment I can not reproduce it again.

So let's assume I can't connect at all

Lucius

---

### Post by kevdog on 2007-10-13
See the link about manual connection listed in my signature.

---

### Post by lubob on 2007-10-13
Thanks for the links, but unfortunately they don't help.

The point is: The driver is ok and ndiswrapper is working fine.

When I define WEP as encoding method and activate the WLAN card by using the Gnome Network tool, everything works fine.

What does not work is to use wpa_supplicant at all. Neither for WEP nor for WPA or WPA2.

Any idea ?

Regards

Lucius

---

### Post by kevdog on 2007-10-13
How about posting iwlist scan and wpa_supplicant.conf??? I mean you got to give me more to work with other than "it doesnt work!!"

---

