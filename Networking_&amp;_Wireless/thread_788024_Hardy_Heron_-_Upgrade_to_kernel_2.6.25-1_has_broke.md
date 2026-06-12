---
title: "Hardy Heron - Upgrade to kernel 2.6.25-1 has broken NetworkManager"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by breadlord on 2008-05-09
Please bear with me - this is my first time posting on Ubuntu forums, but I'm a Debian user with five years of experience behind me so I'm not completely clueless...

I was using the stock 2.6.26-16 kernel that comes on the apt tree and NetworkManager worked flawlessly, but, as is my wont, I upgraded to 2.6.25-1 and although the card works (I'm using patched in drivers from mad-wifi.org - it's an atheros card...) and it stopped. The relevant content of syslog is as follows...

```

May  9 16:44:45 molly NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/ath0 / Etranger 
May  9 16:44:45 molly NetworkManager: <info>  Deactivating device ath0. 
May  9 16:44:45 molly NetworkManager: <info>  Device ath0 activation scheduled... 
May  9 16:44:45 molly NetworkManager: <info>  Activation (ath0) started... 
May  9 16:44:45 molly NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
May  9 16:44:45 molly NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
May  9 16:44:45 molly NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
May  9 16:44:45 molly NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
May  9 16:44:45 molly NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
May  9 16:44:45 molly NetworkManager: <info>  Activation (ath0/wireless): access point 'Etranger' is encrypted, but NO valid key exists.  New key needed. 
May  9 16:44:45 molly NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'Etranger'. 
May  9 16:44:45 molly NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
May  9 16:44:57 molly NetworkManager: <info>  Activation (ath0) New wireless user key for network 'Etranger' received. 
May  9 16:44:57 molly NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
May  9 16:44:57 molly NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
May  9 16:44:57 molly NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
May  9 16:44:57 molly NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
May  9 16:44:57 molly NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
May  9 16:44:57 molly NetworkManager: <info>  Activation (ath0/wireless): access point 'Etranger' is encrypted, and a key exists.  No new key needed. 
May  9 16:44:59 molly NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May  9 16:44:59 molly NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
May  9 16:44:59 molly kernel: [ 1885.304248] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
May  9 16:44:59 molly NetworkManager: <info>  SUP: response was 'OK' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: response was 'OK' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: response was '0' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 457472616e676572' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: response was 'OK' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: response was 'OK' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: response was 'OK' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: response was 'OK' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May  9 16:44:59 molly NetworkManager: <info>  SUP: response was 'OK' 
May  9 16:44:59 molly NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
May  9 16:45:00 molly avahi-daemon[4690]: Registering new address record for fe80::40e:9bff:fe1b:f57 on ath0.*.
May  9 16:45:07 molly NetworkManager: <info>  Old device 'ath0' activating, won't change. 
May  9 16:45:09 molly kernel: [ 1895.400569] ath0: no IPv6 routers present
May  9 16:45:20 molly NetworkManager: <info>  Old device 'ath0' activating, won't change. 
May  9 16:45:58 molly last message repeated 3 times
May  9 16:45:59 molly NetworkManager: <info>  Activation (ath0/wireless): association took too long (>60s), failing activation. 
May  9 16:45:59 molly NetworkManager: <info>  Activation (ath0) failure scheduled... 
May  9 16:46:00 molly NetworkManager: <info>  Activation (ath0) failed for access point (Etranger) 
May  9 16:46:00 molly NetworkManager: <info>  Activation (ath0) failed. 
May  9 16:46:00 molly NetworkManager: <info>  Deactivating device ath0. 
May  9 16:46:00 molly avahi-daemon[4690]: Withdrawing address record for fe80::40e:9bff:fe1b:f57 on ath0.

```

I've heard that NetworkManager is patched to hell under Ubuntu - is there a quick fix / patch? I've not tried doing a source build of NM yet, but I'm hoping I don't have to...

---

### Post by breadlord on 2008-05-12
Take it no-one has any idea what's wrong with this, then?

Guess I'll look on Bugzilla.

---

### Post by Darrena on 2008-05-21
> **breadlord said:**
> Take it no-one has any idea what's wrong with this, then?

Guess I'll look on Bugzilla.

Are you using the new Ath5k driver or the older madwifi?

It looks like NetworkManager is sending -Dmadwifi which may not be needed with the ath5k driver.   Another solution might be to switch to the Madwifi drivers until Ath5k stabilizes a bit more.

---

