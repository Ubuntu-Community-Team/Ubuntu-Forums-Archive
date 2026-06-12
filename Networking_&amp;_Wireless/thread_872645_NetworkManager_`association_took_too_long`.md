---
title: "NetworkManager `association took too long`"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by jago25_98 on 2008-07-28
Windows on the same machine works ok. It still has problems if I specify WPA1 TKIP and key manually. 

Can I not get more output from NetworkManager than this:

```
Jul 28 11:46:48 r40 NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 28 11:46:48 r40 NetworkManager: <info> Activation (eth1/wireless): access point 'hillpark' is encrypted, and a key exists. No new key needed.
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> kernel_driver for non broadcast check: ipw2200 (has_scan_capa_ssid=1)
Jul 28 11:46:50 r40 NetworkManager: <info> Using has_buggy_scan_capa fix for ipw2200
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'AP_SCAN 2'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'ADD_NETWORK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was '0'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 ssid 68696c6c7061726b'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 scan_ssid 1'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 proto WPA'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 psk <key>'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 pairwise TKIP'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 group TKIP'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: sending command 'ENABLE_NETWORK 0'
Jul 28 11:46:50 r40 NetworkManager: <info> SUP: response was 'OK'
Jul 28 11:46:50 r40 NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 28 11:46:55 r40 NetworkManager: <info> Old device 'eth1' activating, won't change.
Jul 28 11:47:50 r40 NetworkManager: <info> Activation (eth1/wireless): association took too long (>60s), failing activation.
Jul 28 11:47:50 r40 NetworkManager: <info> Activation (eth1) failure scheduled...
Jul 28 11:47:50 r40 NetworkManager: <info> Activation (eth1) failed for access point (hillpark)
Jul 28 11:47:50 r40 NetworkManager: <info> Activation (eth1) failed.
Jul 28 11:47:50 r40 NetworkManager: <info> Deactivating device eth1.


```

Will more info like NetworkManager version be required? Takes a lot of rebooting to get this you see.

---

### Post by krzysz00 on 2008-11-23
me too

*bump*

---

### Post by drunknmunky1 on 2008-11-24
Having the same problem as well. Using ipw2200 on 8.10.  I'm able to post whatever information is relevant.
I can't even connect using the command line (wpa_supplicant).

---

### Post by Aearenda on 2008-11-24
Have you seen [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/292054?](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/292054?) Installing the updated Network Manager from the PPA mentioned there will probably fix it.

---

### Post by Haldo on 2008-12-02
I have a different problem, but it is related to the Launchpad bug you linked, and the update did not fix it.

This is the log I collected before updating the NM from PPA (just some xxxx for privacy):


```
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Activation (wlan0) starting connection 'Auto xxxx' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto xxxx' has security, and secrets exist.  No new secrets needed. 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: added 'ssid' value 'xxxx' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: added 'key_mgmt' value 'IEEE8021X' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: added 'password' value '<omitted>' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: added 'eap' value 'PEAP' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: added 'fragment_size' value '1300' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: added 'phase1' value 'peapver=1' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: added 'identity' value 'xxxxxxxx' 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  Config: set interface ap_scan to 1 
Dec  1 19:43:07 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 2 
Dec  1 19:43:09 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Dec  1 19:43:15 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Dec  1 19:43:15 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Dec  1 19:43:31 alex-acer NetworkManager: <info>  wlan0: link timed out. 
Dec  1 19:43:32 alex-acer NetworkManager: <info>  Activation (wlan0/wireless): association took too long. 
Dec  1 19:43:32 alex-acer NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Dec  1 19:43:32 alex-acer NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Dec  1 19:43:32 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
```

After this failure Network Manager would ask me to insert authentication data again.

Now I updated NM to the 0.7~~svn20081018t105859-0ubuntu2 version, which should fix the problem.
The difference is that NM does not ask me new data anymore, but it get stuck in the authentication process.
This is the log:
```
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) starting connection 'Auto xxxx' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto xxxx' has security, but secrets are required. 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto xxxx' has security, and secrets exist.  No new secrets needed. 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: added 'ssid' value 'xxxx' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: added 'key_mgmt' value 'IEEE8021X' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: added 'password' value '<omitted>' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: added 'eap' value 'PEAP' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: added 'fragment_size' value '1300' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: added 'phase1' value 'peapver=1' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: added 'identity' value 'xxxxxxxx' 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  Config: set interface ap_scan to 1 
Dec  2 16:00:25 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 2 
Dec  2 16:00:27 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Dec  2 16:00:37 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Dec  2 16:00:37 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Dec  2 16:00:38 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Dec  2 16:00:38 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Dec  2 16:00:48 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Dec  2 16:00:52 alex-acer NetworkManager: <info>  wlan0: link timed out. 
Dec  2 16:00:56 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Dec  2 16:00:56 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Dec  2 16:01:00 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 3 
Dec  2 16:01:10 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Dec  2 16:01:10 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Dec  2 16:01:11 alex-acer NetworkManager: <info>  wlan0: link timed out. 
Dec  2 16:01:12 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Dec  2 16:01:24 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Dec  2 16:01:24 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Dec  2 16:01:32 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Dec  2 16:01:32 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Dec  2 16:01:36 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 3 
Dec  2 16:01:39 alex-acer NetworkManager: <info>  wlan0: link timed out. 
Dec  2 16:01:46 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Dec  2 16:01:46 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Dec  2 16:01:48 alex-acer NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
```

I suppose it could continue like this for ages...

---

### Post by Haldo on 2008-12-02
As it turns out, the new Network Manager version includes the following workaround:

> * fix LP: #292054 - Some drivers take too long to associate (Was:
    network-manager 0.7 always asks for WPA passphrase); we workaround
    this driver/wpasupplicant bug by giving association more time
    (e.g. 60sec instead of 25sec)
    - add debian/patches/lp292054_tune_supplicant_timeout_60s.patch
    - update debian/patches/series

We just have to wait more time before becoming frustrated...

---

