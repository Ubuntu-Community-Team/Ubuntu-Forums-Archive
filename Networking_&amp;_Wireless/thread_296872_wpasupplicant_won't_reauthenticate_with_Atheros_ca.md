---
title: "wpasupplicant won't reauthenticate with Atheros card"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by cookfromfrozen on 2006-11-10
I have WPA working fine on an Atheros card with wpasupplicant (Xubuntu 6.06).

I have wpasupplicant starting on boot in the **/etc/network/interfaces **file with the following, and everything works.

```
pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Now, the problem is when the link fails because I get too far from the AP or if I manually down the interface or run **/etc/init.d/networking restart**.  It keeps trying to authenticate and then keeps disconnecting in a loop.

This is when I get when I wpa_supplicant from the terminal:

```
[freedy@laptop ~]$ sudo wpa_supplicant -Dmadwifi -i ath0 -c /etc/wpa_supplicant.conf
Trying to associate with 00-11-5B-EF-90-C9 (SSID='HomeWifi' freq=2462 MHz)
Authentication with 00:00:00:00:00:00 timed out.
```
It knows the MAC address yet it suddenly goes to "00:00:00:00:00:00" for some reason.  The SSID is not hidden.

As I say, wpasupplicant works fine on boot the first time around, but subsequent attempts to get it to reauthenticate do not.

I initially thought that the wpa_supplicant process wasn't getting killed, but it is so I can't think why it doesn't work the second time around.

Any ideas?  Thanks.

---

### Post by cookfromfrozen on 2006-11-12
bump

---

