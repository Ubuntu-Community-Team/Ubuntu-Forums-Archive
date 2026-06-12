---
title: "Wpa-problems"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by Dendagard on 2005-10-21
Hello,

i get my YakumoQuickwlan USB-Stick with ndiswrapper 1.4 to work (zydas-chip 1211) and now i am trying to get wpa also to work. But i had no success. For configuration i used this wiki:  [wiki](https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA)



```
felix@klapperkiste:~$ sudo sh -c 'ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd'
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapp er'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 7 - start of a new network block
ssid - hexdump_ascii(len=5):
     46 65 6c 69 78                                    <my ssid>
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='<my ssid>'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: <Mac adress>
Setting scan request: 0 sec 100000 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Wireless event: cmd=0x8b06 len=8
Starting AP scan (broadcast SSID)
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 305 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: <Mac adress router> ssid='<my ssid>' wpa_ie_len=24 rsn_ie_len=0
   selected
Trying to associate with <Mac adress router> (SSID='<my ssid>' freq=2467 MHz)
Cancelling scan request
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Own WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
RX EAPOL from <Mac Adresse vom Router>
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 a 5 e6 40 f4 55 7a ff 98 a5 b2 e5 c5 a1 69 c0 04 1c ba 72 b7 00 41 82 3e 20 30 9c c0 c9 e1 8d 8e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00
Setting authentication timeout: 10 sec 0 usec
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 0 0 00 01 a5 e6 40 f4 55 7a ff 98 a5 b2 e5 c5 a1 69 c0 04 1c ba 72 b7 00 41 82 3e 20 30 9c c0 c9 e1 8d 8e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00 00 00 00
WPA: RX message 1 of 4-Way Handshake from <Mac adress router> (ver=1)
WPA: No SSID info found (msg 1 of 4).
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:00:00:00:00:00 into blacklist
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Disconnect event - remove keys
RX EAPOL from <Mac adress router>
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 02 a 5 e6 40 f4 55 7a ff 98 a5 b2 e5 c5 a1 69 c0 04 1c ba 72 b7 00 41 82 3e 20 30 9c c0 c9 e1 8d 8e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 0 0 00 02 a5 e6 40 f4 55 7a ff 98 a5 b2 e5 c5 a1 69 c0 04 1c ba 72 b7 00 41 82 3e 20 30 9c c0 c9 e1 8d 8e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00 00 00 00
WPA: RX message 1 of 4-Way Handshake from <Mac adresse router> (ver=1)
WPA: No SSID info found (msg 1 of 4).
Starting AP scan (broadcast SSID)
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 305 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: <Mac adress router> ssid='<my ssid>' wpa_ie_len=24 rsn_ie_len=0
   selected
Trying to associate with <Mac adress router> (SSID='<my ssid>' freq=2467 MHz)
Cancelling scan request
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Own WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
RX EAPOL from <Mac adress router>
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 0 c f6 e7 c1 d8 24 5a 0b d1 c9 52 44 7d bc 27 01 ed 11 fb 95 ca 78 6f 60 4b 22 49 d4 6d 9d 46 62 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 0 0 00 01 0c f6 e7 c1 d8 24 5a 0b d1 c9 52 44 7d bc 27 01 ed 11 fb 95 ca 78 6f 60 4b 22 49 d4 6d 9d 46 62 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00 00 00 00
WPA: RX message 1 of 4-Way Handshake from <Mac Adresse vom Router> (ver=1)
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 0 1 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Renewed SNonce - hexdump(len=32): 9e 8e 8e 0d 5b 2d 52 25 db bc d5 63 7a 2f  69 ac d8 ac b4 7f 9a 11 2a 87 58 52 31 d7 05 f5 f2 43
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: EAPOL-Key MIC - hexdump(len=16): 29 b6 85 8e 85 ce 1b 9a 80 2b 69 bf 74 a9 14 a5
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key 2/4 - hexdump(len=137): 00 a0 c5 ec 4e 44 00 01 36 0b 21 22 88  8e 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 9e 8e 8e 0d 5b 2d 52 25 d b bc d5 63 7a 2f 69 ac d8 ac b4 7f 9a 11 2a 87 58 52 31 d7 05 f5 f2 43 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 29 b6 85 8e 85 ce 1b 9a 80 2b 69 bf 74 a9 14 a5 00 18 dd 16 00 50 f2 01 0 1 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
RX EAPOL from <Mac adress router>
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 02 0 c f6 e7 c1 d8 24 5a 0b d1 c9 52 44 7d bc 27 01 ed 11 fb 95 ca 78 6f 60 4b 22 49 d4 6d 9d 46 62 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 0 0 00 02 0c f6 e7 c1 d8 24 5a 0b d1 c9 52 44 7d bc 27 01 ed 11 fb 95 ca 78 6f 60 4b 22 49 d4 6d 9d 46 62 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00 00 00 00
WPA: RX message 1 of 4-Way Handshake from <Mac Adresse vom Router> (ver=1)
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 0 1 00 00 50 f2 02 01 00 00 50 f2 02
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: EAPOL-Key MIC - hexdump(len=16): f0 73 8d ce cb 4c d5 74 9d 4a cb 1f 76 40 67 87
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key 2/4 - hexdump(len=137): 00 a0 c5 ec 4e 44 00 01 36 0b 21 22 88  8e 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 02 9e 8e 8e 0d 5b 2d 52 25 d b bc d5 63 7a 2f 69 ac d8 ac b4 7f 9a 11 2a 87 58 52 31 d7 05 f5 f2 43 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 f0 73 8d ce cb 4c d5 74 9d 4a cb 1f 76 40 67 87 00 18 dd 16 00 50 f2 01 0 1 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from <Mac adress router>
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 03 0c f6 e7 c1 d8 24 5a 0b d1 c9 52 44 7d bc 27 01 ed 11 fb 95 ca 78 6f 60 4b 22 49  d4 6d 9d 46 62 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00 00 00 00 00 00 00 00 00 00 96 ba 8d 90 cc 6d 60 7e 9d 12 5f 68 61 bb 20 31 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 03 0c f6 e7 c1 d8 24 5a 0b d1 c9 52 44 7d bc 27 01 ed 11 fb 95 ca 78 6f 60  4b 22 49 d4 6d 9d 46 62 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00 00 00 00 00 00 00 00 00 00 00 00 00 96 ba 8d 90 cc 6d 60 7e 9d 12 5f 68 61 bb 20 31 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50  f2 02
WPA: RX message 3 of 4-Way Handshake from <Mac adress router> (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key 4/4 - hexdump(len=113): 00 a0 c5 ec 4e 44 00 01 36 0b 21 22 88  8e 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 03 9e 8e 8e 0d 5b 2d 52 25 d b bc d5 63 7a 2f 69 ac d8 ac b4 7f 9a 11 2a 87 58 52 31 d7 05 f5 f2 43 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 cb 0b 49 60 e5 e9 45 27 97 54 ad 1a 14 96 e9 44 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
RX EAPOL from <Mac adress router>
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 04 e2 6f dc 0c 38 0e 29 38 43 9a 11 c2 a5 c5 69 ee 4d 3d e0 a6 f0 78 fc 8b 31 3c 02  c6 c3 cc 73 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00 00 00 00 00 00 00 00 00 00 a1 67 1a e6 52 96 b4 af f7 ee 5b 5d 9c bc 8d 1c 00 20 fd b9 a7 b7 38 90 62 17 df bd 92 a5 7b 53 e4 40 f2 4d 31 ad c9 5a 4e d8 e1  d4 fc 1b 9c 10 9e 98
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 04 e2 6f dc 0c 38 0e 29 38 43 9a 11 c2 a5 c5 69 ee 4d 3d e0 a6 f0 78 fc 8b  31 3c 02 c6 c3 cc 73 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0 0 00 00 00 00 00 00 00 00 00 00 00 00 00 a1 67 1a e6 52 96 b4 af f7 ee 5b 5d 9c bc 8d 1c 00 20 fd b9 a7 b7 38 90 62 17 df bd 92 a5 7b 53 e4 40 f2 4d 31 ad c9 5a  4e d8 e1 d4 fc 1b 9c 10 9e 98
WPA: RX message 1 of Group Key Handshake from <Mac adress router> (ver=1)
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key 2/2 - hexdump(len=113): 00 a0 c5 ec 4e 44 00 01 36 0b 21 22 88  8e 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 04 00 00 00 00 00 00 00 00 0 0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  00 00 12 2d 7c 2c f6 c5 02 d8 a2 42 38 31 e8 86 f4 c9 00 00
WPA: Key negotiation completed with <Mac adress router> [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
Removed BSSID 00:00:00:00:00:00 from blacklist
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAP: EAP entering state DISABLED
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Signal 2 received - terminating
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0

```

my wpa_supplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="my ssid"
        #psk="my key"
        proto=WPA
	key_mgmt=WPA-PSK
        psk=a lot of numbers and letters
        
}
```

my wpasupplicant
```
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>		Wireless Driver
#  -i <ifname>		Interface (required, unless specified in config)
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

OPTIONS="-w"
```

Is there somebaody, who can give me some help??

---

### Post by firecat53 on 2005-10-21
Trying adding 'sudo' in front of the command to run wpa_supplicant. That's an error in one of the how-to's that never got updated!  I also think you can get rid of the lines:
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

in your .conf file and it should still work fine. But, try the sudo thing first, then take out the other lines one at a time to make sure things are ok.

Good luck!
Scott

---

### Post by Dendagard on 2005-10-23
Hello,

now it works. The problem about "sudo" was not new to me. My only problem was, that my notebook didn't get a ip from my Router. After "sudo sh -c 'ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf ' " i had to restart /etc/init.d/networking and my notebook became a ip from the router. 

Now i've written a new /etc/network/interfaces and my WLAN-connection starts after booting. That works great.

But now i have the problem, that i am switching often between two dfferent wlans. Firts at home (WPA) and second at my university (no encryption). I hat it after the booting at university to kill wpa_supplicant and to edit my /etc/network/interfaces to get access to the wlan.

So i tried wifi-radar (i've installed it from the breezy universe to a hoary-system) and had no success. I get a connection to the wlan at university. But no connection at home. I think wifi-Radar has problems to communicate with wpa_supplicant.

What settings have i to do at wifi-radar and at the wifi-radar.conf respectively.

---

### Post by lonetree on 2005-10-24
Hi Dendagard,

can you tell me how you rewrite your interfaces file?

I can't get my wpa to work on startup and I will have to try many times with command line to make it obtain IP from the router. Can you show your supplicant.conf file too?

Thanks in advance.

Regards,

---

### Post by Dendagard on 2005-10-24
thats no problem. But now i am at work. I can post it for you in the evening.

Dendagard

---

### Post by lonetree on 2005-10-24
Thanks Dendagard.

Hope your configuration could help me solve my problem. 

I am using a Dlink DWL-G650 (Atheros chipset) for my wireless card, Dlink DI-724P+ and DI-624+ (at home and at work)

once again, thank you for your help

regards,

---

### Post by mjwood0 on 2005-10-24
If you have the Atheros chipset, why don't you use the Madwifi drivers that are native to linux?  Not that Ndiswrapper isn't nice, but native support is better.

Just curious.

---

### Post by lonetree on 2005-10-24
Yes. I am using madwifi. Is there anything different with the wpa configuration from what Dendagard posted?

regards,

:rolleyes:

---

### Post by Dendagard on 2005-10-24
/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

/etc/wpa_supplicant.conf
```

network={
        ssid="my ssid"
	key_mgmt=WPA-PSK
        proto=WPA
	pairwise=TKIP
	group=TKIP CCMP
        psk=my key
}

```

/etc/default/wpasupplicant
```
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>		Wireless Driver
#  -i <ifname>		Interface (required, unless specified in config)
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

OPTIONS="-w"
```

I hope, it helps you (you have to replace ndiswrapper and wlan0 with your wireless driver and wlan0, eth0, eth1...)

---

### Post by mjwood0 on 2005-10-24
@lonetree:

I got confused as Dendagard seems to be using NDiswrapper.

Sorry -- my file looks a lot like his! ;)

---

### Post by lonetree on 2005-10-24
not a problem mjwood1. Thanks for your info anyway.

Dendagard, thanks for your config too, btw, do I have to do a shell script to make it work on boot up? I saw one posting here said that I have to create a shell script like "wpa_wifi.sh"

---

### Post by Dendagard on 2005-10-25
No you don't have to do this.

first step: install wpasupplicant
second step: edit your /etc/wpa_supplicant.conf, /etc/default/wpasupplicant and /etc/network/interfaces
third step: test it by /etc/init.d/networking restart

If that works you can reboot your computer (your /etc/init.d/networking should work at every boot automatically)

---

### Post by lonetree on 2005-10-27
HI pple,

sorry to have reply late, like I said, I am using Atheros chipset, wonder if there is any different compared to Dendagard's config.

Btw, I tried using Den's method and it din work for me, the interface din get any IP from the router, but one thing I find it strange, although no IP is assigned, I can see that the DNS is obtained from the router, what I have to do it start the networking-manager, choose wireless network, then deactivate, and reactivate it a few times until the router gives an IP to my notebook.

Sigh. Any ideas, guys?

regards,

---

### Post by lonetree on 2005-10-30
Hi Dendagard,

I am still having problem with getting connected during startup. Have followed your configuration and still to no avail.

Any idea?

Any help would be appreciated.

Regards,

---

### Post by sohni on 2006-05-27
If Atheros chip uses kernel drivers you could try -D wext instead of -D ndiswrapper with wpasupplicant or -D madwifi if you are using madwifi drivers.

Rest of the conf should be the same.

---

