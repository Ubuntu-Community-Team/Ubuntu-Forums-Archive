---
title: "Network connection for non-admin users?"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by richq on 2007-11-27
Wireless mode is set to Roaming in the network config window. 

The admin user has an automatic network connection when he logs in to Gutsy. 

Non-admin users do not get network connections. Even if they enter the correct WEP key, exactly as it is entered in the admin user's settings, the connection never completes. 

Anyone heard of anything similar? Same story with manual configuration actually, if the non-privileged user logs in first, she has to log out and the admin log in or else the network never gets set up right.

The syslog from a session is as follows:

```

Nov 27 20:02:27 rich-laptop NetworkManager: <info>  Activation (eth1) started...
Nov 27 20:02:27 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:02:27 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:02:27 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Nov 27 20:02:27 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:02:27 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Nov 27 20:02:27 rich-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'mySSID' is encrypted, but NO valid key exists.  New key needed.
Nov 27 20:02:27 rich-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'mySSID'.
Nov 27 20:02:27 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Nov 27 20:03:05 rich-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'mySSID' received.
Nov 27 20:03:05 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:03:05 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:03:05 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Nov 27 20:03:05 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:03:05 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Nov 27 20:03:05 rich-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'mySSID' is encrypted, and a key exists.  No new key needed. 
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10).
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10).
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant4^I'
Nov 27 20:03:06 rich-laptop kernel: [  513.268000] NET: Registered protocol family 17
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10).
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: response was '0'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6e616461717565766572'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:06 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Nov 27 20:03:09 rich-laptop kernel: [  516.436000] ieee80211_crypt: registered algorithm 'WEP'
Nov 27 20:03:29 rich-laptop NetworkManager: <info>  Activation (eth1/wireless): disconnected during association, asking for new key.
Nov 27 20:03:29 rich-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'mySSID'.
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'mySSID' received.
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  eth1: link timed out.
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0'
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0'
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE'
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:50 rich-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'mySSID' is encrypted, and a key exists.  No new key needed. 
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10).
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10).
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant5^I'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10).
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was '0'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6e616461717565766572'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10).
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10).
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant5^I'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10).
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was '0'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6e616461717565766572'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:03:51 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Nov 27 20:04:14 rich-laptop NetworkManager: <info>  Activation (eth1/wireless): disconnected during association, asking for new key.
Nov 27 20:04:14 rich-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'mySSID'.
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'mySSID' received.
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0'
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 0'
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  SUP: sending command 'TERMINATE'
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  SUP: response was 'OK'
Nov 27 20:04:33 rich-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'mySSID' is encrypted, and a key exists.  No new key needed.
 
```

---

