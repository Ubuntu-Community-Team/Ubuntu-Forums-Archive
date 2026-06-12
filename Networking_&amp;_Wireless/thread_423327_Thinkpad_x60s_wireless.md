---
title: "Thinkpad x60s wireless"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by B0b on 2007-04-25
Hello!

I just installed Ubuntu 7.04 onto a new thinkpad x60s. It seems that the wireless network card is detected (Atheros HAL is in use) and when I click on network manager I can see my wireless network. However when I try to connect to the network the connection fails. I have tried other network managers, all to no avail.

Any help anyone can provide would be great.

Thanks

---

### Post by speeddemon8803 on 2007-04-25
Did you happen to set up your network name by any chance? I know it doesnt automatically find your networks SSID..but if you go to network...and click on wireless connection i think...and...ack..someone help me out LOL! i'm half way there someone else finish this off.

---

### Post by B0b on 2007-04-25
Did I set up my wireless network SSID? yes, I have been using the wireless network for ages and have several other machines connected to it.

Also, my systems logs show lots of dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 Interval 4, then 5 and so on messages, and then ends with no DHCPOFFERS received.

I thought it might be that the DHCP server is not working or some weird occurence, but tried on a different wireless network and got the same stuff.

The daemon.log is full of stuff like this

Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): No keys have been configured - skip key clearing 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): EAPOL: External notification - portEnabled=0 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): EAPOL: External notification - portValid=0 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Setting scan request: 0 sec 0 usec 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): State: DISCONNECTED -> SCANNING 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Starting AP scan (broadcast SSID) 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Wireless event: cmd=0x8b1a len=8 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Wireless event: cmd=0x8b19 len=8 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Received 3012 bytes of scan results (15 BSSes) 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Scan results: 15 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Selecting BSS from priority group 0 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 0: 00:14:6c:44:e6:0e ssid='krypton' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 1: 00:17:9a:40:84:87 ssid='Groovy Love Inc' wpa_ie_len=26 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):   skip - SSID mismatch 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 2: 00:14:bf:f8:62:1e ssid='linksys_SES_40579' wpa_ie_len=26 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 3: 00:11:95:bb:e1:f7 ssid='leetlink' wpa_ie_len=0 rsn_ie_len=22 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 4: 00:90:4c:7e:00:10 ssid='Rafael' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 5: 00:18:f8:d3:2a:65 ssid='Jen's Wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 6: 00:14:51:6c:4f:39 ssid='Dannykins' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 7: 00:13:10:0a:2b:35 ssid='Home' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 8: 00:09:5b:d7:bf:6a ssid='Friedman' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 9: 00:15:e9:ec:ad:ce ssid='SR Home' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 10: 00:0f:66:9a:69:49 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 11: d6:b0:a5:86:d4:ca ssid='hpsetup' wpa_ie_len=0 rsn_ie_len=0 caps=0x2 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):  ssid='Apple Network 94f451' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 13: 00:e0:98:d1:1d:a0 ssid='04Z411280092' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 14: 00:50:f2:75:71:30 ssid='MSHOME' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    selected non-WPA AP 00:50:f2:75:71:30 ssid='MSHOME' 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Trying to associate with 00:50:f2:75:71:30 (SSID='MSHOME' freq=2437 MHz) 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 38 37 2d 34 00 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Cancelling scan request 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WPA: clearing own WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Automatic auth_alg selection: 0x1 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WPA: clearing AP WPA IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WPA: clearing AP RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WPA: clearing own WPA/RSN IE 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): No keys have been configured - skip key clearing 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): wpa_driver_madwifi_set_drop_unencrypted: enabled=0 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): State: SCANNING -> ASSOCIATING 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 21:01:37 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): wpa_driver_madwifi_associate 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): te: SETMLME[ASSOC] failed 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Association request to the driver failed 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 38 37 2d 34 00 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Setting authentication timeout: 5 sec 0 usec 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): EAPOL: External notification - portControl=ForceAuthorized 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Wireless event: cmd=0x8b1a len=14 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Authentication with 00:00:00:00:00:00 timed out. 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 38 37 2d 34 00 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): BSSID 00:50:f2:75:71:30 blacklist count incremented to 2 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): State: ASSOCIATING -> DISCONNECTED 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): No keys have been configured - skip key clearing 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): EAPOL: External notification - portEnabled=0 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): EAPOL: External notification - portValid=0 
Apr 25 21:01:42 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Setting scan request: 0 sec 0 usec 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): > SCANNING 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Starting AP scan (broadcast SSID) 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Wireless event: cmd=0x8b1a len=8 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Wireless event: cmd=0x8b19 len=8 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Received 3012 bytes of scan results (15 BSSes) 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Scan results: 15 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Selecting BSS from priority group 0 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 0: 00:14:6c:44:e6:0e ssid='krypton' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 1: 00:17:9a:40:84:87 ssid='Groovy Love Inc' wpa_ie_len=26 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 2: 00:14:bf:f8:62:1e ssid='linksys_SES_40579' wpa_ie_len=26 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 3: 00:11:95:bb:e1:f7 ssid='leetlink' wpa_ie_len=0 rsn_ie_len=22 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 4: 00:90:4c:7e:00:10 ssid='Rafael' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 5: 00:18:f8:d3:2a:65 ssid='Jen's Wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 6: 00:14:51:6c:4f:39 ssid='Dannykins' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 7: 00:09:5b:d7:bf:6a ssid='Friedman' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 8: 00:13:10:0a:2b:35 ssid='Home' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 9: 00:15:e9:ec:ad:ce ssid='SR Home' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 10: 00:0f:66:9a:69:49 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 11: d6:b0:a5:86:d4:ca ssid='hpsetup' wpa_ie_len=0 rsn_ie_len=0 caps=0x2 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 12: 00:11:24:94:f4:51 ssid='Apple Network 94f451' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 13: 00:e0:98:d1:1d:a0 ssid='04Z411280092' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 14: 00:50:f2:75:71:30 ssid='MSHOME' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - blacklisted 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): No APs found - clear blacklist and try again 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Removed BSSID 00:50:f2:75:71:30 from blacklist (clear) 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Selecting BSS from priority group 0 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 0: 00:14:6c:44:e6:0e ssid='krypton' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): h 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 1: 00:17:9a:40:84:87 ssid='Groovy Love Inc' wpa_ie_len=26 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 2: 00:14:bf:f8:62:1e ssid='linksys_SES_40579' wpa_ie_len=26 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 3: 00:11:95:bb:e1:f7 ssid='leetlink' wpa_ie_len=0 rsn_ie_len=22 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - SSID mismatch 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 4: 00:90:4c:7e:00:10 ssid='Rafael' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 5: 00:18:f8:d3:2a:65 ssid='Jen's Wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 6: 00:14:51:6c:4f:39 ssid='Dannykins' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 7: 00:09:5b:d7:bf:6a ssid='Friedman' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 8: 00:13:10:0a:2b:35 ssid='Home' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 9: 00:15:e9:ec:ad:ce ssid='SR Home' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 10: 00:0f:66:9a:69:49 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): up' wpa_ie_len=0 rsn_ie_len=0 caps=0x2 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 12: 00:11:24:94:f4:51 ssid='Apple Network 94f451' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 13: 00:e0:98:d1:1d:a0 ssid='04Z411280092' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 14: 00:50:f2:75:71:30 ssid='MSHOME' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    skip - no WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080):    selected non-WPA AP 00:50:f2:75:71:30 ssid='MSHOME' 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Trying to associate with 00:50:f2:75:71:30 (SSID='MSHOME' freq=2437 MHz) 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 38 37 2d 34 00 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Cancelling scan request 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WPA: clearing own WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Automatic auth_alg selection: 0x1 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WPA: clearing AP WPA IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WPA: clearing AP RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WPA: clearing own WPA/RSN IE 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): No keys have been configured - skip key clearing 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): wpa_driver_madwifi_set_drop_unencrypted: enabled=0 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): State: SCANNING -> ASSOCIATING 
Apr 25 21:01:52 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): te: linkmode=-1, operstate=5 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): wpa_driver_madwifi_associate 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): wpa_driver_madwifi_associate: SETMLME[ASSOC] failed 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Association request to the driver failed 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 38 37 2d 34 00 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Setting authentication timeout: 5 sec 0 usec 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): EAPOL: External notification - portControl=ForceAuthorized 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Wireless event: cmd=0x8b1a len=14 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Authentication with 00:00:00:00:00:00 timed out. 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 38 37 2d 34 00 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Added BSSID 00:50:f2:75:71:30 into blacklist 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): State: ASSOCIATING -> DISCONNECTED 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): No keys have been configured - skip key clearing 
Apr 25 21:01:57 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): EAPOL: External notification - portEnabled=0 
Apr 25 21:02:06 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): 0 
Apr 25 21:02:06 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Setting scan request: 0 sec 0 usec 
Apr 25 21:02:06 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): State: DISCONNECTED -> SCANNING 
Apr 25 21:02:06 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Starting AP scan (broadcast SSID) 
Apr 25 21:02:06 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 21:02:06 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): Wireless event: cmd=0x8b1a len=8 
Apr 25 21:02:06 spookyNIX NetworkManager: <information>^Iwpa_supplicant(21080): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 


debug log has this

Apr 25 21:01:33 spookyNIX kernel: [30022.340000] ath0: no IPv6 routers present
Apr 25 21:03:38 spookyNIX kernel: [30146.956000] ath0: no IPv6 routers present
Apr 25 21:03:40 spookyNIX kernel: [30149.756000] eth0: no IPv6 routers present

Kern.log has this

Apr 25 21:01:23 spookyNIX kernel: [30011.912000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Apr 25 21:01:33 spookyNIX kernel: [30022.340000] ath0: no IPv6 routers present
Apr 25 21:03:23 spookyNIX kernel: [30131.856000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Apr 25 21:03:38 spookyNIX kernel: [30146.956000] ath0: no IPv6 routers present
Apr 25 21:03:40 spookyNIX kernel: [30149.756000] eth0: no IPv6 routers present

Messages

Apr 25 21:01:21 spookyNIX dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Apr 25 21:01:23 spookyNIX kernel: [30011.912000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Apr 25 21:03:23 spookyNIX kernel: [30131.856000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready

Syslog looks like the daemon log

---

### Post by B0b on 2007-04-26
Dmesg | grep ath0 returns

[   35.316000] ath0: no IPv6 routers present
[   82.436000] ath0: no IPv6 routers present
[  106.932000] ath0: no IPv6 routers present


Not sure if that helps with a solution, but I thought I would post it anyway

---

