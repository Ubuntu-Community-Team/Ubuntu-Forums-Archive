---
title: "AR5005G + WPA2 Problems (AR2413, AR5BMB5)"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by Tsume on 2008-06-06
The issue I am having is this:  I can connect to my dad's D-Link DGL-4300 (fw 1.9) just fine (he is using WPA with AES) however I cannot connect to my D-Link DIR-655 (fw 1.11) when it is configured with WPA2 with AES  If I switch it to WPA with AES it works.  I need it to be WPA2 or my shed pc's mimo card throws a hissy.

This problem has always occured since I put ubuntu on this laptop at verison 7.04.  I just wiped the whole thing, installed 8.04, patched all the way, and the problem still occurs :(  Here's what shows up in the syslog file... any ideas?  I tried WICD but it just froze when I told it to connect, and I was never able to open WICD again after that.  I took the easy way out and just reinstalled 8.04.

```

Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Device ath0 activation scheduled... 
Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Activation (ath0) started... 
Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Activation (ath0/wireless): access point 'KWolf' is encrypted, but NO valid key exists.  New key needed. 
Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'KWolf'. 
Jun  5 20:47:52 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jun  5 20:48:07 tsumeone-laptop NetworkManager: <info>  Activation (ath0) New wireless user key for network 'KWolf' received. 
Jun  5 20:48:07 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  5 20:48:07 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jun  5 20:48:07 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jun  5 20:48:07 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jun  5 20:48:07 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jun  5 20:48:07 tsumeone-laptop NetworkManager: <info>  Activation (ath0/wireless): access point 'KWolf' is encrypted, and a key exists.  No new key needed. 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was '0' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4b576f6c66' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise CCMP' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group CCMP' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun  5 20:48:08 tsumeone-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jun  5 20:48:16 tsumeone-laptop NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Jun  5 20:48:52 tsumeone-laptop last message repeated 5 times
Jun  5 20:49:07 tsumeone-laptop last message repeated 2 times
Jun  5 20:49:08 tsumeone-laptop NetworkManager: <info>  Activation (ath0/wireless): association took too long (>60s), failing activation. 
Jun  5 20:49:08 tsumeone-laptop NetworkManager: <info>  Activation (ath0) failure scheduled... 
Jun  5 20:49:09 tsumeone-laptop NetworkManager: <info>  Activation (ath0) failed for access point (KWolf) 
Jun  5 20:49:09 tsumeone-laptop NetworkManager: <info>  Activation (ath0) failed. 
Jun  5 20:49:09 tsumeone-laptop NetworkManager: <info>  Deactivating device ath0. 
```

---

### Post by Tsume on 2008-06-06
I'm stupid.  The router was set to 802.11n only mode.  Sorry to waste post space ><

---

