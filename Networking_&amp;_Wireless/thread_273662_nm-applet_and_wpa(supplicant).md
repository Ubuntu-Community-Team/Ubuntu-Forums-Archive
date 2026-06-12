---
title: "nm-applet and wpa(supplicant)"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by corvy on 2006-10-08
I just thought I would share my experiences. Lately I did an upgrade (just normal updates) which updated wpasupplicant. Now the executable moved from /sbin/wpa_supplicant to /usr/sbin/wpa_supplicant, this made nm-applet fail like this:

```

Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) New wireless user key for network 'barmen' received.
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1/wireless): access point 'barmen' is encrypted, and a key exists.  No new key needed.
Oct  8 22:47:36 localhost NetworkManager: <WARNING>^I supplicant_exec (): Couldn't start wpa_supplicant.  Error: (8) Failed to execute child process "/sbin/wpa_supplicant" (No such file or directory)
Oct  8 22:47:36 localhost NetworkManager: <WARNING>^I real_act_stage2_config (): Activation (eth1/wireless): couldn't start the supplicant.
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled...
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) failed for access point (barmen)
Oct  8 22:47:36 localhost NetworkManager: <information>^IActivation (eth1) failed.
Oct  8 22:47:36 localhost NetworkManager: <information>^IDeactivating device eth1.
Oct  8 22:47:38 localhost NetworkManager: <information>^Imatch


```Ok, so I did fix this with a little:

```
sudo ln -s /usr/sbin/wpa_supplicant /sbin/
```Either wpasupplicant, or nm-applet needs to be updates to support this change. 

Just thought I would share my experiences. :)

---

### Post by sandrejev on 2006-11-10
Try this code to check if you have the same problem

```
sudo killall NetworkManager
sudo NetworkManager --no-daemon
```

Also i do not understand how other people don't have the same problem. It took me a complete reinstall to realize that wlan drivers are ok and instead there is a problem with nm

---

### Post by corvy on 2006-11-11
I do not know why this happened, but if it only was a problem for me then :rolleyes:, no problems!

Everything works fine for me, day before yesterday I also upgraded to edgy so ... the landscape has changed quite a bit.

---

