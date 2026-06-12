---
title: "Cisco AP 350 Issues."
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by mariom48 on 2008-07-28
Hello forum,

I have a question that I had posted a bout a month ago although I had received some feedback I am still stuck with the problem.

[B]First:   Does anybody knows if a CISCO 350 SERIES is supported.
[/B]
**Second: Here it's the output of the syslog when I tried to access the CISCO 350**

Jul 28 14:39:48 eljocote NetworkManager: <debug> [1217281188.282110] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '****' 
Jul 28 14:39:48 eljocote NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/ath0 / **** 
Jul 28 14:39:48 eljocote NetworkManager: <info>  Deactivating device ath0. 
Jul 28 14:39:48 eljocote dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 6855
Jul 28 14:39:48 eljocote dhclient: killed old client process, removed PID file
Jul 28 14:39:48 eljocote dhclient: wifi0: unknown hardware address type 801
Jul 28 14:39:48 eljocote dhclient: wifi0: unknown hardware address type 801
Jul 28 14:39:48 eljocote dhclient: DHCPRELEASE on ath0 to 192.168.1.1 port 67
Jul 28 14:39:48 eljocote avahi-daemon[4996]: Withdrawing address record for 192.168.1.103 on ath0.
Jul 28 14:39:48 eljocote avahi-daemon[4996]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.103.
Jul 28 14:39:48 eljocote avahi-daemon[4996]: Interface ath0.IPv4 no longer relevant for mDNS.
Jul 28 14:39:49 eljocote avahi-daemon[4996]: Withdrawing address record for fe80::211:85ff:fe1b:4fad on ath0.
Jul 28 14:39:49 eljocote NetworkManager: <info>  Device ath0 activation scheduled... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) started... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0/wireless): access point '****' is encrypted, but NO valid key exists.  New key needed. 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) New wireless user key requested for network '****'. 
Jul 28 14:39:49 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) New wireless user key for network '****' received. 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jul 28 14:40:04 eljocote NetworkManager: <info>  Activation (ath0/wireless): access point '****' is encrypted, and a key exists.  No new key needed. 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was '0' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 7075746f' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  SUP: response was 'OK' 
Jul 28 14:40:05 eljocote NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jul 28 14:40:21 eljocote NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Jul 28 14:40:53 eljocote last message repeated 2 times
Jul 28 14:41:57 eljocote last message repeated 4 times
Jul 28 14:42:05 eljocote NetworkManager: <info>  Activation (ath0/wireless): association took too long (>120s), asking for new key. 
Jul 28 14:42:05 eljocote NetworkManager: <info>  Activation (ath0) New wireless user key requested for network '****'.

Thank you very much for all your help.

Regards,
Mario

---

