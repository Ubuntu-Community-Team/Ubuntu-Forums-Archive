---
title: "WPA stops working after Ubuntu madwifi update?"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by Lutze on 2007-05-26
Hi there,

actually, I can't connect to my router via WPA. I use network-manager, and it used to work fine until I installed the latest ubuntu updates today, among them linux-restricted-modules - including the madwifi drivers for my atheros wireless chipset.

Taking a look at the log file, I find 
> 
May 26 22:36:20 conspiracy NetworkManager: <information>^IActivation (ath0) New wireless user key requested for network 'datenkollektiv'. 
May 26 22:36:20 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 2 of 5 (Device Configure) complete. 
May 26 22:36:20 conspiracy avahi-daemon[4793]: Withdrawing address record for fe80::214:a4ff:fe39:3b14 on ath0.
May 26 22:36:20 conspiracy kernel: [  640.172000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
May 26 22:36:20 conspiracy avahi-autoipd(ath0)[6451]: SIOCSIFFLAGS failed: Permission denied
May 26 22:36:20 conspiracy NetworkManager: <information>^IActivation (ath0) New wireless user key for network 'datenkollektiv' received. 
May 26 22:36:20 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
May 26 22:36:20 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 1 of 5 (Device Prepare) started... 
May 26 22:36:20 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
May 26 22:36:20 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 1 of 5 (Device Prepare) complete. 
May 26 22:36:20 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 2 of 5 (Device Configure) starting... 
May 26 22:36:20 conspiracy NetworkManager: <information>^IActivation (ath0/wireless): access point 'datenkollektiv' is encrypted, and a key exists.  No new key needed. 
May 26 22:36:20 conspiracy kernel: [  640.244000] ADDRCONF(NETDEV_UP): ath0: link is not ready
May 26 22:36:20 conspiracy NetworkManager: <information>^IDHCP daemon state is now 11 (unknown) for interface ath0 
May 26 22:36:20 conspiracy NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface ath0 


Before the update, it was
> 
May 26 12:08:09 conspiracy NetworkManager: <information>^IActivation (ath0) New wireless user key requested for network 'datenkollektiv'. 
May 26 12:08:09 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 2 of 5 (Device Configure) complete. 
May 26 12:08:09 conspiracy NetworkManager: <information>^IActivation (ath0) New wireless user key for network 'datenkollektiv' received. 
May 26 12:08:09 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
May 26 12:08:09 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 1 of 5 (Device Prepare) started... 
May 26 12:08:09 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
May 26 12:08:09 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 1 of 5 (Device Prepare) complete. 
May 26 12:08:09 conspiracy NetworkManager: <information>^IActivation (ath0) Stage 2 of 5 (Device Configure) starting... 
May 26 12:08:09 conspiracy NetworkManager: <information>^IActivation (ath0/wireless): access point 'datenkollektiv' is encrypted, and a key exists.  No new key needed. 
May 26 12:08:09 conspiracy NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant^I' 
May 26 12:08:09 conspiracy kernel: [ 3103.004000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready


I have no idea, where to search, and also not what avahi wants to tell me. I can still connect to my unencrypted backup AP. Any ideas how I can debug this - and whether the upate of linux-restricted-modules can affect this behavior?

---

