---
title: "Issues connecting wirelessly"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by dkrushev on 2008-05-23
First of all I'm sorry if this was already discussed, but I couldn't find it. Therefore I'm opening this new thread.
I have Dell Latitude X300 with freshly installed Ubuntu 8.04, Intel® PRO/Wireless 2100 adapter and DLink DI-524 wireless router.

I,ve tried connecting to the router with 3 different configurations of the security settings:

1. WPA2

2. WPA

3. Without securty

All 3 times the result was the following:

May 23 12:40:43 Uknown NetworkManager: <info>  Activation (eth1) started... 
May 23 12:40:43 Uknown NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
May 23 12:40:43 Uknown NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
May 23 12:40:43 Uknown NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
May 23 12:40:43 Uknown NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
May 23 12:40:43 Uknown NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
May 23 12:40:43 Uknown NetworkManager: <info>  Activation (eth1/wireless): access point 'diddo' is unencrypted, no key needed. 
May 23 12:40:44 Uknown NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: response was 'OK' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: response was 'OK' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: response was '0' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 646964646f406d61696c2e6267' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: response was 'OK' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: response was 'OK' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 23 12:40:45 Uknown NetworkManager: <info>  SUP: response was 'OK' 
May 23 12:40:45 Uknown NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
May 23 12:40:50 Uknown NetworkManager: <info>  Old device 'eth1' activating, won't change. 
May 23 12:41:16 Uknown last message repeated 5 times
May 23 12:41:43 Uknown last message repeated 5 times
May 23 12:41:45 Uknown NetworkManager: <info>  Activation (eth1/wireless): association took too long (>60s), failing activation. 
May 23 12:41:45 Uknown NetworkManager: <info>  Activation (eth1) failure scheduled... 
May 23 12:41:45 Uknown NetworkManager: <info>  Activation (eth1) failed for access point (diddo) 
May 23 12:41:45 Uknown NetworkManager: <info>  Activation (eth1) failed. 
May 23 12:41:45 Uknown NetworkManager: <info>  Deactivating device eth1. 


Can somebody tell me what I need to do?

Thank you for your time.

---

