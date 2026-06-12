---
title: "Encrypted Wireless With an RT73, Wpasupplicant, and Ndiswrapper"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by aarmenaa on 2007-03-29
I've been working on this for the better part of a week.  I have an USB wireless adapter (RT73 chipset), and I've tried pretty much every driver I could find for the thing, and finally settled on the Windows driver with ndiswrapper, because it's the only method that was able to connect to an access point at all.  I have tested and can confirm that it works fine with my WEP access point (it doesn't support WPA).

But I use this with my laptop to connect to my school's network.  They provide a software package **[SecureW2 ]("http://www.securew2.com/")** on Windows, along with some information, and the card is able to connect to the network that way (so it's at least theoretically capable of this).  They don't provide instructions for connecting under Linux, but they do give me the following settings:

> SSID: hornet
Authentication Method: 802.1x
Authentication Type: EAP-TTLS
Encryption Type: WPA
Key Style: TKIP
Certificate Authority: Thawte
Domain: (leave blank)
-A username and password that I should enter somewhere

Of course, that's not really all the information.  I looked at someone else's Windows setup and the certificate is actually "Thawte Server CA" which I located in /etc/ssl/certs/Thawte_Server_CA.pem.  I also see that there is a field "select authentication method" labeled "PAP."  Perhaps more telling, a field named "EAP type" is completely grayed out.  Searching around on the internet, it doesn't seem like "PAP" is going to work for "key_mgmt."  All the other configs I've seen use WPA-EAP and then make "phase2" PAP.  So I do my best to cobble something together:

```
ctrl_interface=/var/run/wpa_supplicant
network={
	ssid="hornet"
	scan_ssid=0
	key_mgmt=WPA-EAP
	pairwise=TKIP
	group=TKIP
	eap=TTLS
	ca_cert="/etc/ssl/certs/Thawte_Server_CA.pem"
	identity="<secret!>"
	password="<secret!>"
	phase2="auth=PAP"
}
```

Naturally, it doesn't work, not even a little bit.  I've fiddled with most of the settings, removed some, added a couple, changed key_mgmt to IEEE8021X (which I had high hopes for working), and I just don't know enough.  This is what I run in a terminal:

> ifconfig wlan0 up
iwconfig wlan0 essid "hornet"
wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -d wext -dd >> /home/aarmenaa/wpasupplicantrunlog.txt

And the resulting text file looks like this:
> Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=2
ap_scan=1
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     68 6f 72 6e 65 74                                 hornet          
scan_ssid=0 (0x0)
key_mgmt: 0x1
pairwise: 0x8
group: 0x8
eap methods - hexdump(len=16): 00 00 00 00 15 00 00 00 00 00 00 00 00 00 00 00
ca_cert - hexdump_ascii(len=35):
     2f 65 74 63 2f 73 73 6c 2f 63 65 72 74 73 2f 54   /etc/ssl/certs/T
     68 61 77 74 65 5f 53 65 72 76 65 72 5f 43 41 2e   hawte_Server_CA.
     70 65 6d                                          pem             
identity - hexdump_ascii(len=17):
     6a 64 6f 6e 61 64 65 6f 40 73 70 73 75 2e 65 64   <secret!>
     75                                                u               
password - hexdump_ascii(len=6): [REMOVED]
phase2 - hexdump_ascii(len=8):
     61 75 74 68 3d 50 41 50                           auth=PAP        
Priority group 0
   id=0 ssid='hornet'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0e:2e:b3:80:03
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
Added interface wlan0
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 257 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:0c:e6:0d:66:5f ssid='hornet' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:0c:e6:0d:66:5f (SSID='hornet' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b04 len=12
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c07 len=50
AssocReq IE wireless event - hexdump(len=42): 00 06 68 6f 72 6e 65 74 01 08 82 84 8b 96 0c 12 18 24 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
Wireless event: cmd=0x8c08 len=69
AssocResp IE wireless event - hexdump(len=61): 01 08 82 84 8b 96 0c 12 18 24 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 00 00 dd 17 00 0c e6 00 04 0c 00 00 00 01 06 00 0c e6 00 88 e9 04 04 01 00 00 00
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:0c:e6:0d:66:5f
Association info event
req_ies - hexdump(len=42): 00 06 68 6f 72 6e 65 74 01 08 82 84 8b 96 0c 12 18 24 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
resp_ies - hexdump(len=61): 01 08 82 84 8b 96 0c 12 18 24 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 00 00 dd 17 00 0c e6 00 04 0c 00 00 00 01 06 00 0c e6 00 88 e9 04 04 01 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
State: ASSOCIATING -> ASSOCIATED
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:0c:e6:0d:66:5f
No keys have been configured - skip key clearing
Associated with 00:0c:e6:0d:66:5f
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
TX EAPOL - hexdump(len=4): 02 01 00 00
Authentication with 00:0c:e6:0d:66:5f timed out.
Added BSSID 00:0c:e6:0d:66:5f into blacklist
State: ASSOCIATED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_disassociate
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:0c:e6:0d:66:5f blacklist count incremented to 2
State: SCANNING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
Scan timeout - try to get results
Received 257 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:0c:e6:0d:66:5f ssid='hornet' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - blacklisted
No APs found - clear blacklist and try again
Removed BSSID 00:0c:e6:0d:66:5f from blacklist (clear)
Selecting BSS from priority group 0
0: 00:0c:e6:0d:66:5f ssid='hornet' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:0c:e6:0d:66:5f (SSID='hornet' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b04 len=12
Wireless event: cmd=0x8b1a len=14
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:0c:e6:0d:66:5f into blacklist
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0

Apologies for being so long, but suffice it to say that my log is actually much longer.  What I see is that the card associates with the AP (good!), starts authenticating (good!), but never gets a response back and times out (baaad!).  In my limited understanding, this is the point where the AP should basically give a yes or no answer.

One possibility is that this just flat out doesn't work because of ndis wrapper.  I read in a couple spots that ndiswrapper doesn't really play well with some of the more complex wpasupplicant features, and I should just install the Linux driver.  There's reasons I don't want to do this (I've tried them all, and can't get any of them to work properly).

Anyways, any help, input, or things to try would be greatly appreciated.

---

