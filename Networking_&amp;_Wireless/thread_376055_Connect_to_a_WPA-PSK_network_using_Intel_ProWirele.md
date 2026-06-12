---
title: "Connect to a WPA-PSK network using Intel Pro/Wireless 2100."
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by Arkainium on 2007-03-04
Hi,

I have a [D-Link DI-614+ (Rev. B)]("http://support.dlink.com/products/view.asp?productid=DI%2D614%2B%5FrevB") wireless router using WPA-PSK encryption which I'm trying to connect to from my laptop using an Intel Pro/Wireless 2100 3B adapter.  It works fine on Windows XP but on Linux I've only been able to connect to the network using WEP encryption or no encryption at all.  I've tried both Edgy and Feisty, with wpa_supplicant and through NetworkManager, with no success.

Here's what I've got so far:

**lspci:**
```
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation MIM2000/Centrino
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128 (500ns min, 8500ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
```

**modinfo ipw2100:**
```
filename:       /lib/modules/2.6.20-9-generic/kernel/drivers/net/wireless/ipw2100.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        git-1.2.2
description:    Intel(R) PRO/Wireless 2100 Network Driver
srcversion:     A92EA8FAF926910DC3A6A17
alias:          pci:v00008086d00001043sv00008086sd000025A0bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002598bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002596bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002593bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002591bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002592bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002590bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002587bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002586bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002585bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002581bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002583bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002582bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002580bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002570bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002567bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002566bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002565bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002561bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002563bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002562bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002560bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002555bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002554bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002553bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002551bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002550bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Dbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Cbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Bbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002529bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002528bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002527bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002523bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002522bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002526bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002525bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002524bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002521bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002520bc*sc*i*
depends:        ieee80211
vermagic:       2.6.20-9-generic SMP mod_unload 586 
parm:           debug:debug level (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           channel:channel (int)
parm:           associate:auto associate when scanning (default on) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           dont_disable_c3:don't disable C3 state transitions (default 0 [disable C3 transtitions on errors]) (int)
```

**wpa_supplicant -v**
```
wpa_supplicant v0.5.5
```

**nm-applet --version**
```
GNOME nm-applet 0.6.4
```

NetworkManager just times out after a while so I tried manually with wpa_supplicant.
**wpa_supplicant.conf:**
```
network={
        ssid="manashirov"
        key_mgmt=WPA-PSK
        proto=WPA
        psk="key phrase"
}
```

**iwlist eth0 scanning:**
```
eth1      Scan completed :
          Cell 01 - Address: 00:40:05:61:15:B5
                    ESSID:"manashirov"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Quality:95  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 776ms ago
```

**wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D wext -w -dd:**
```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=10):
     6d 61 6e 61 73 68 69 72 6f 76                     manashirov
key_mgmt: 0x2
proto: 0x1
PSK (ASCII passphrase) - hexdump_ascii(len=22): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='manashirov'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:04:23:62:26:0e
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 1013 bytes of scan results (5 BSSes)
Scan results: 5
Selecting BSS from priority group 0
0: 00:e0:98:db:68:5a ssid='<hidden>' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:40:05:61:15:b5 ssid='manashirov' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:40:05:61:15:b5 (SSID='manashirov' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:40:05:61:15:b5
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:40:05:61:15:b5
No keys have been configured - skip key clearing
Associated with 00:40:05:61:15:b5
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RX EAPOL from 00:40:05:61:15:b5
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 04 05 62 f0 ab 3d 39 14 a9 b3 58 bf ee c9 a2 d1 d9 2b ab 13 a1 5c 9b 66 e5 5f 26 ab 2e f3 6a e8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 04 05 62 f0 ab 3d 39 14 a9 b3 58 bf ee c9 a2 d1 d9 2b ab 13 a1 5c 9b 66 e5 5f 26 ab 2e f3 6a e8
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 04 05 62 f0 ab 3d 39 14 a9 b3 58 bf ee c9 a2 d1 d9 2b ab 13 a1 5c 9b 66 e5 5f 26 ab 2e f3 6a e8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:40:05:61:15:b5 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 79 b0 00 23 91 38 21 bf 1f ef 8e d1 6b 63 cc c7 11 f7 cc 3b 16 58 c5 28 85 3b 6e 77 0c f8 23 e2
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 79 b0 00 23 91 38 21 bf 1f ef 8e d1 6b 63 cc c7 11 f7 cc 3b 16 58 c5 28 85 3b 6e 77 0c f8 23 e2 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3e 4a 7c a1 b3 b5 6b e6 79 03 f6 b7 af 5d 70 34 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:40:05:61:15:b5
RX EAPOL - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 04 05 62 f0 ab 3d 39 14 a9 b3 58 bf ee c9 a2 d1 d9 2b ab 13 a1 5c 9b 66 e5 5f 26 ab 2e f3 6a e8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 41 23 25 81 0d a6 2e d9 3a 0b c5 54 a0 12 1f 92 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
IEEE 802.1X RX: version=1 type=3 length=121
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=26
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 04 05 62 f0 ab 3d 39 14 a9 b3 58 bf ee c9 a2 d1 d9 2b ab 13 a1 5c 9b 66 e5 5f 26 ab 2e f3 6a e8
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 41 23 25 81 0d a6 2e d9 3a 0b c5 54 a0 12 1f 92
WPA: RX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 04 05 62 f0 ab 3d 39 14 a9 b3 58 bf ee c9 a2 d1 d9 2b ab 13 a1 5c 9b 66 e5 5f 26 ab 2e f3 6a e8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 41 23 25 81 0d a6 2e d9 3a 0b c5 54 a0 12 1f 92 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:40:05:61:15:b5 (ver=1)
WPA: IE KeyData - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 45 c7 8e c4 3d d9 98 a0 fe 09 5a 5a 7e 7f 44 5e 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
Authentication with 00:40:05:61:15:b5 timed out.
Added BSSID 00:40:05:61:15:b5 into blacklist
State: GROUP_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_disassociate
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:40:05:61:15:b5 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: DISCONNECTED -> DISCONNECTED
```

Here's my build up of kernel messages during this session:
**dmesg:**
```
[   62.376000] eth0: no IPv6 routers present
[  173.140000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  176.384000] ieee80211_crypt: registered algorithm 'TKIP'
[  183.444000] eth1: no IPv6 routers present 
[  193.352000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[  203.376000] ipw2100: exit - failed to send CARD_DISABLE command
[  203.376000] ipw2100: exit - failed to send CARD_DISABLE command
[  203.376000] ipw2100: exit - failed to send CARD_DISABLE command
[  203.376000] ipw2100: exit - failed to send CARD_DISABLE command
[  210.348000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[  220.376000] ipw2100: exit - failed to send CARD_DISABLE command
[  220.376000] ipw2100: exit - failed to send CARD_DISABLE command
[  220.376000] ipw2100: exit - failed to send CARD_DISABLE command
[  220.376000] ipw2100: exit - failed to send CARD_DISABLE command
[  227.348000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[  250.572000] eth0: no IPv6 routers present
[  287.064000] eth0: link down
[  288.028000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  288.764000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  288.768000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  310.980000] eth0: no IPv6 routers present
[  352.460000] ieee80211_crypt: registered algorithm 'WEP'
[  352.952000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  369.576000] eth1: no IPv6 routers present
[  487.680000] eth0: link down
[  489.344000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  489.348000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  494.628000] eth0: link down
[  496.684000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  498.212000] eth0: link down
[  499.476000] eth0: no IPv6 routers present
[  499.828000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  551.192000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  552.040000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  555.216000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[  562.624000] eth1: no IPv6 routers present
[  572.216000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[  589.216000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[  606.216000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[  614.152000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  625.648000] eth0: no IPv6 routers present
[  665.040000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  676.048000] eth0: no IPv6 routers present
[  758.168000] eth0: no IPv6 routers present
[  795.244000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  809.220000] eth0: link down
[  810.916000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  810.920000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  819.196000] eth0: link down
[  820.932000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  820.936000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  831.692000] eth0: no IPv6 routers present
[  835.224000] eth0: link down
[  836.972000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  841.440000] eth0: link down
[  843.528000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  845.020000] eth0: link down
[  846.672000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  957.108000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  960.024000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[  967.684000] eth1: no IPv6 routers present
[  977.020000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[  994.020000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1011.020000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1035.352000] eth0: no IPv6 routers present
[ 1035.784000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1148.988000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1152.012000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1159.428000] eth1: no IPv6 routers present
[ 1169.012000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1186.008000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1203.008000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1220.008000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1237.008000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1254.008000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1277.456000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1281.944000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1285.004000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1292.320000] eth1: no IPv6 routers present
[ 1302.004000] TKIP: replay detected: STA=00:40:05:61:15:b5 previous TSC 000000000000 received TSC 000000000000
[ 1416.876000] ADDRCONF(NETDEV_UP): eth1: link is not ready 
[ 1537.148000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

I'm not sure what to make out from all this information but if anyone can offer any advice, all help is greatly appreciated.

Thanks.

---

### Post by kabturek on 2007-03-08
Hi
I have the same problem with ipw2100.
i get the "link is no ready" messages in dmesg. my 2nd pc with other wi-fi card (madwifi)can connect to the AP ( wrt-45gl + tomato firmware - both gr8 :) without problems... the AP uses WPA Personal and TKIP encryption. I try to change some settings....

---

### Post by kabturek on 2007-03-08
this is really weird - i've found several threads about it on the net and nothing helped - i've turned on windows (its my girlfriends laptop) and it started working in windows and in ubuntu too when i got back to ubuntu...

---

### Post by Arkainium on 2007-03-08
> **kabturek said:**
> this is really weird - i've found several threads about it on the net and nothing helped - i've turned on windows (its my girlfriends laptop) and it started working in windows and in ubuntu too when i got back to ubuntu...

That's odd.  Is it working consistently in Ubuntu, even after restarting?

I was beginning to think my Dlink router is the problem, but I don't have any extra hardware around to test it.

---

### Post by kabturek on 2007-03-08
It's working ok for 2 restarts... i hope it stays that way ... i was thinking that it was a problem with my router (especially that i have a custom firmware) but after seeing the router logs - i sow that the router isn't contacted at  all ... so it had to be the laptop fault.

---

### Post by Arkainium on 2007-03-08
My router logs show that the machine authenticates and connects but it doesn't distribute an IP.  I'm really not sure what I can do besides use WEP and MAC filtering to keep intruders out.  At least I'll be able to use it.

---

