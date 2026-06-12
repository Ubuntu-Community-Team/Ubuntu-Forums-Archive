---
title: "wpa_supplicant 0.5.5 &amp; NetworkManager 0.6.2"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by Hoshimaru on 2006-10-27
Hello.

I recently updated my system and since then I can't connect to my wireless network anymore. NetworkManager complains it can't connect to the supplicant.

I had this error in the past and making the symlink /sbin/wpa_supplicant solved it. This time, it's not working anymore.

Here's the syslog part concerning my wireless connection:
```
Oct 27 21:16:55 naruto NetworkManager: <information>^IWill activate connection 'eth1/Pacifica'.
Oct 27 21:16:55 naruto NetworkManager: <information>^IDevice eth1 activation scheduled...
Oct 27 21:16:55 naruto NetworkManager: <information>^Imatch
Oct 27 21:16:55 naruto NetworkManager: <information>^IActivation (eth1) started...
Oct 27 21:16:55 naruto NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 27 21:16:55 naruto NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 27 21:16:55 naruto NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 27 21:16:55 naruto NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 27 21:16:55 naruto NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 27 21:16:55 naruto NetworkManager: <information>^IActivation (eth1/wireless): access point 'Pacifica' is encrypted, but NO valid key exists.  New key needed.
Oct 27 21:16:55 naruto NetworkManager: <information>^IActivation (eth1) New wireless user key requested for network 'Pacifica'.
Oct 27 21:16:55 naruto NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 27 21:16:55 naruto NetworkManager: <information>^Imatch
Oct 27 21:16:55 naruto last message repeated 3 times
Oct 27 21:17:01 naruto NetworkManager: <information>^IActivation (eth1) New wireless user key for network 'Pacifica' received.
Oct 27 21:17:01 naruto NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 27 21:17:01 naruto NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 27 21:17:01 naruto NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 27 21:17:01 naruto NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 27 21:17:01 naruto NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 27 21:17:01 naruto NetworkManager: <information>^IActivation (eth1/wireless): access point 'Pacifica' is encrypted, and a key exists.  No new key needed.
[COLOR="Red"]**Oct 27 21:17:02 naruto NetworkManager: <WARNING>^I real_act_stage2_config (): Activation (eth1/wireless): couldn't connect to the supplicant.**[/COLOR]
Oct 27 21:17:02 naruto NetworkManager: <information>^IActivation (eth1) failure scheduled...
Oct 27 21:17:02 naruto NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 27 21:17:02 naruto NetworkManager: <information>^Iwpa_supplicant(5557): Debugging disabled with CONFIG_NO_STDOUT_DEBUG=y build time option.
Oct 27 21:17:02 naruto NetworkManager: <information>^IActivation (eth1) failed for access point (Pacifica)
Oct 27 21:17:02 naruto NetworkManager: <information>^IActivation (eth1) failed.
Oct 27 21:17:02 naruto NetworkManager: <information>^IDeactivating device eth1.
Oct 27 21:17:04 naruto NetworkManager: <information>^Imatch

```

I've look everywhere, but I couldn't solve this problem.
Any suggestions?

---

