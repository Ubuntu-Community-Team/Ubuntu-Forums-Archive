---
title: "Wifi can't connect to one access point: Association timed out"
date: 2016-12-21
forum: Networking &amp; Wireless
---

### Post by m0rg on 2016-12-21
Hi,

I have problems connecting to my workplace WiFi network on Ubuntu 16.04 on a Sony Vaio VPCZ1 i5 laptop.
I can connect to nearly all Wifi networks without a problem, but my workplace network doesn't connect.
<disclaimer> I am not the only person who has this problem, although most devices connect with an issue, it happens on various devices particularly android devices as well, but it is more difficult to get good debugging on them. </disclaimer>
Also, Windows 7 on the same laptop connects well.

In NetworkManager I can see the AP, it asks for a password so I type it in, then it tries to connect multiple times and fails.
I caught up with someone who could change some AP settings yesterday for half an hour and we tried with no security and it still failed to connect, and also tried combinations of WEP, 802.11n and 802.11g without it working.

There are 4 AP's all with the same setup in multiple parts of the building, and all fail. I am almost certainly connecting to the one right outside my office, although looking at the logs it sometimes tries other ones.. They are NetGear WAG102 routers.

I have attached the wireless-info log, and have also got full logs available from trying to connect with wpa_supplicant, but I'm not sure whether I need to anonymise apart from the SSID/password. Are MAC addresses OK?

While I don't have access to the router settings myself, I can ask someone to change things, and we would love to fix this problem for all devices, so changing settings on the AP is a good option.

Thank you for your assistance, I would be very happy to get this issue solved!
Pete

The bit where it all goes wrong for wpa_supplicant:
```

wlp2s0: New scan results available (own=1 ext=0)
wlp2s0: Radio work 'scan'@0x816409c0 done in 3.038933 seconds
wlp2s0: Selecting BSS from priority group 0
wlp2s0: 0: e0:46:9a:b1:ed:af ssid='MyAP' wpa_ie_len=26 rsn_ie_len=24 caps=0x411 level=-43
wlp2s0:    selected based on RSN IE
wlp2s0:    selected BSS e0:46:9a:b1:ed:af ssid='MyAP'
wlp2s0: Considering connect request: reassociate: 0  selected: e0:46:9a:b1:ed:af  bssid: 00:00:00:00:00:00  pending: 00:00:00:00:00:00  wpa_state: SCANNING  ssid=0x81631470  current_ssid=(nil)
wlp2s0: Request association with e0:46:9a:b1:ed:af
WPA: Unrecognized EAPOL-Key Key Data IE - hexdump(len=10): 00 08 43 43 57 6f 6b 69 6e 67
WPA: Unrecognized EAPOL-Key Key Data IE - hexdump(len=3): 03 01 08
WPA: Unrecognized EAPOL-Key Key Data IE - hexdump(len=8): 07 06 47 42 20 01 0d 14
WPA: Unrecognized EAPOL-Key Key Data IE - hexdump(len=3): 2a 01 04
WPA: RSN IE in EAPOL-Key - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 02 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: WPA IE in EAPOL-Key - hexdump(len=28): dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02
wlp2s0: Add radio work 'sme-connect'@0x81645100
wlp2s0: First radio work item in the queue - schedule start immediately
wlp2s0: Starting radio work 'sme-connect'@0x81645100 after 0.000015 second wait
wlp2s0: Automatic auth_alg selection: 0x1
RSN: PMKSA cache search - network_ctx=(nil) try_opportunistic=0
RSN: Search for BSSID e0:46:9a:b1:ed:af
RSN: No PMKSA cache entry found
wlp2s0: RSN: using IEEE 802.11i/D9.0
wlp2s0: WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 2
wlp2s0: WPA: Selected mgmt group cipher 32
WPA: set AP WPA IE - hexdump(len=28): <hex removed as I'm not sure if if it's a security issue>
WPA: set AP RSN IE - hexdump(len=26): <hex removed as I'm not sure if if it's a security issue>
wlp2s0: WPA: using GTK TKIP
wlp2s0: WPA: using PTK CCMP
wlp2s0: WPA: using KEY_MGMT WPA-PSK
wlp2s0: WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): <hex removed as I'm not sure if if it's a security issue>
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
RRM: Determining whether RRM can be used - device support: 0x0
RRM: No RRM in network
wlp2s0: Cancelling scan request
wlp2s0: SME: Trying to authenticate with e0:46:9a:b1:ed:af (SSID='MyAP' freq=2447 MHz)
wlp2s0: State: SCANNING -> AUTHENTICATING
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
wlp2s0: Determining shared radio frequencies (max len 1)
wlp2s0: Shared frequencies (len=0): completed iteration
nl80211: Authenticate (ifindex=3)
  * bssid=<hex removed as I'm not sure if if it's a security issue>
  * freq=2447
  * SSID - hexdump_ascii(len=8):
    <hex removed as I'm not sure if if it's a security issue>       
  * IEs - hexdump(len=0): [NULL]
  * Auth Type 0
nl80211: Authentication request send successfully
RTM_NEWLINK: ifi_index=3 ifname=wlp2s0 wext ifi_family=0 ifi_flags=0x1003 ([UP])
nl80211: Event message available
nl80211: Drv Event 19 (NL80211_CMD_NEW_STATION) received for wlp2s0
nl80211: New station e0:46:9a:b1:ed:af
nl80211: Event message available
nl80211: Drv Event 37 (NL80211_CMD_AUTHENTICATE) received for wlp2s0
nl80211: MLME event 37 (NL80211_CMD_AUTHENTICATE) on wlp2s0(00:27:10:0e:f6:f4) <hex removed as I'm not sure if if it's a security issue>
nl80211: MLME event frame - hexdump(len=30): <hex removed as I'm not sure if if it's a security issue>
nl80211: Authenticate event
wlp2s0: Event AUTH (11) received
wlp2s0: SME: Authentication response: peer=e0:46:9a:b1:ed:af auth_type=0 auth_transaction=2 status_code=0
SME: Authentication response IEs - hexdump(len=0): [NULL]
wlp2s0: set_disable_max_amsdu: -1
wlp2s0: set_ampdu_factor: -1
wlp2s0: set_ampdu_density: -1
wlp2s0: set_disable_ht40: 0
wlp2s0: set_disable_sgi: 0
wlp2s0: set_disable_ldpc: 0
wlp2s0: Trying to associate with <hex removed as I'm not sure if if it's a security issue> (SSID='MyAP' freq=2447 MHz)
wlp2s0: State: AUTHENTICATING -> ASSOCIATING
nl80211: Set wlp2s0 operstate 0->0 (DORMANT)
netlink: Operstate: ifindex=3 linkmode=-1 (no change), operstate=5 (IF_OPER_DORMANT)
WPA: set own WPA/RSN IE - hexdump(len=22): <hex removed as I'm not sure if if it's a security issue>
nl80211: Associate (ifindex=3)
  * bssid=<hex removed as I'm not sure if if it's a security issue>
  * freq=2447
  * SSID - hexdump_ascii(len=8):
     <hex removed as I'm not sure if if it's a security issue>                           MyAP
  * IEs - hexdump(len=32): <hex removed as I'm not sure if if it's a security issue>
  * WPA Versions 0x2
  * pairwise=0xfac04
  * group=0xfac02
  * akm=0xfac02
  * htcaps - hexdump(len=26): 63 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  * htcaps_mask - hexdump(len=26): 63 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  * vhtcaps - hexdump(len=12): 00 00 00 00 00 00 00 00 00 00 00 00
  * vhtcaps_mask - hexdump(len=12): 00 00 00 00 00 00 00 00 00 00 00 00
nl80211: Association request send successfully
nl80211: Event message available
nl80211: Drv Event 20 (NL80211_CMD_DEL_STATION) received for wlp2s0
nl80211: Delete station e0:46:9a:b1:ed:af
nl80211: Event message available
nl80211: Drv Event 38 (NL80211_CMD_ASSOCIATE) received for wlp2s0
nl80211: MLME event 38; timeout with e0:46:9a:b1:ed:af
wlp2s0: Event ASSOC_TIMED_OUT (15) received
wlp2s0: SME: Association timed out
wlp2s0: Radio work 'sme-connect'@0x81645100 done in 0.345564 seconds
Added BSSID e0:46:9a:b1:ed:af into blacklist
wlp2s0: Another BSS in this ESS has been seen; try it next
BSSID e0:46:9a:b1:ed:af blacklist count incremented to 2
wlp2s0: Blacklist count 1 --> request scan in 100 ms
wlp2s0: Setting scan request: 0.100000 sec
wlp2s0: State: ASSOCIATING -> DISCONNECTED
nl80211: Set wlp2s0 operstate 0->0 (DORMANT)
netlink: Operstate: ifindex=3 linkmode=-1 (no change), operstate=5 (IF_OPER_DORMANT)
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
wlp2s0: State: DISCONNECTED -> SCANNING
wlp2s0: Starting AP scan for wildcard SSID
wlp2s0: Optimize scan based on previously generated frequency list
wlp2s0: Add radio work 'scan'@0x81640f68
wlp2s0: First radio work item in the queue - schedule start immediately
wlp2s0: Starting radio work 'scan'@0x81640f68 after 0.000022 second wait
wlp2s0: nl80211: scan request
nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
nl80211: Scan frequency 2447 MHz
Scan requested (ret=0) - scan timeout 30 seconds
nl80211: Event message available
nl80211: Drv Event 33 (NL80211_CMD_TRIGGER_SCAN) received for wlp2s0
wlp2s0: nl80211: Scan trigger
wlp2s0: Event SCAN_STARTED (47) received
wlp2s0: Own scan request started a scan in 0.000072 seconds
RTM_NEWLINK: ifi_index=3 ifname=wlp2s0 wext ifi_family=0 ifi_flags=0x1003 ([UP])
nl80211: Event message available
nl80211: Drv Event 34 (NL80211_CMD_NEW_SCAN_RESULTS) received for wlp2s0
wlp2s0: nl80211: New scan results available
nl80211: Scan probed for SSID ''
nl80211: Scan included frequencies: 2447
wlp2s0: Event SCAN_RESULTS (3) received
wlp2s0: Scan completed in 0.034247 seconds
nl80211: Received scan results (25 BSSes)
wlp2s0: BSS: Start scan result update 2
BSS: last_scan_res_used=25/32
wlp2s0: New scan results available (own=1 ext=0)
wlp2s0: Radio work 'scan'@0x81640f68 done in 0.035166 seconds
wlp2s0: Selecting BSS from priority group 0



```

---

