---
title: "networkmanager fails to resolve IP, manual works"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by iluva on 2006-12-21
networkmanager sees the wireless networks, but when i try to connect by the nm-applet it can't bind an adress. setting it up manually works.
the log of syslog:
> ge 1 of 5 (Device Prepare) scheduled... 
Dec 21 19:13:07 eddy-laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Dec 21 19:13:07 eddy-laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Dec 21 19:13:07 eddy-laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Dec 21 19:13:07 eddy-laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Dec 21 19:13:07 eddy-laptop NetworkManager: <information>^IActivation (eth1/wireless): access point 'Cafe Transformateur' is unencrypted, no key needed. 
Dec 21 19:13:08 eddy-laptop NetworkManager: <WARNING>^I real_act_stage2_config (): Activation (eth1/wireless): couldn't connect to the supplicant. 
Dec 21 19:13:08 eddy-laptop NetworkManager: <information>^IActivation (eth1) failure scheduled... 
Dec 21 19:13:08 eddy-laptop NetworkManager: <information>^IActivation (eth1) failed for access point (Cafe Transformateur) 
Dec 21 19:13:08 eddy-laptop NetworkManager: <information>^IActivation (eth1) failed. 
Dec 21 19:13:08 eddy-laptop NetworkManager: <information>^IDeactivating device eth1. 
Dec 21 19:13:08 eddy-laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete.

is there a problem with dbus or hal?

---

### Post by LordYama on 2006-12-27
I've got the same problem. Unfortunately, I haven't found a solution yet ](*,)

---

### Post by iluva on 2006-12-27
... still didn't find a solution for this problem...
```
Dec 21 19:13:08 eddy-laptop NetworkManager: <WARNING>^I real_act_stage2_config (): Activation (eth1/wireless): couldn't connect to the supplicant.
```
it says that it couldn't connect to the supplicant... what does it mean by that? wpa-supplicant is correctly installed and even shouldn't have to do smth with it....
probabely the problem lies in the self compiled IEEE80211 stack? or the self compiled ipw3945 module?
any1 any ideas?

---

