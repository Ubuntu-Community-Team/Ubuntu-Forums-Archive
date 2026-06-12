---
title: "ASUS WL-138g v2 WPA problems on Fiesty on x64"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by real_sunfire on 2008-09-10
Hi guys,

I'm yet another person with a ASUS WL-138g v2 card who is having problems with it. I've tried the solutions in the forums and various other placess  and nothing has helped yet (forgive me if I have missed the solution)

My problem: I can get the card to connect to my wireless switch using an unsecured connection but I can't seem to get a WPA connection to work.

I'm using Ubuntu 7.04 with the latest WinXP x64 driver (DR_WL138gv2_gE_3100640) for the card via ndiswrapper as my machine didn't even recognise the card using the default bcm43xx driver . I can see the wireless connection on my switch but I'll try can  use wpa_suppliciant I get "Driver does not support WPA" amongst other things (full details below). Everything works fine with  WinXP sadly *:(

Some details from my system below. If took me hours to get to the first step of a getting an unsecured connection with the card can someone please help with WPA please?

Thanks,
Nick.

root@riffraff:~# lshw -C network
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: wlan0
       version: 02
       serial: 00:1e:8c:30:c6:52
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,02/11/2005, 3.100.64.0 latency=32 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f5018000-f5019fff irq:16

root@riffraff:~# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)


root@riffraff:~# iwlist scan
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

eth3      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:50:18:3A:7E:A6
                    ESSID:"mywirelessnet"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.467 GHz (Channel 12)
                    Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 

oot@riffraff:~# cat /etc/wpa_supplicant.conf
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
ssid="mywirelessnet"
scan_ssid=0
proto=WPA
key_mgmt=WPA-PSK
psk="asciipasswordfornet"
pairwise=TKIP
group=TKIP
}

root@riffraff:~# wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=11):
     67 6f 6f 64 6e 65 74 31 39 37 30                  mywirelessnet     
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='mywirelessnet'
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
Own MAC address: 00:1e:8c:30:c6:52
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 324 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:50:18:3a:7e:a6 ssid='mywirelessnet' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:50:18:3a:7e:a6 (SSID='mywirelessnet' freq=2467 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:50:18:3a:7e:a6 into blacklist
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)

---

