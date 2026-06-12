---
title: "Ubuntu 18.04.2 LTS can't connect WiFi"
date: 2019-04-27
forum: Networking &amp; Wireless
---

### Post by modomobo on 2019-04-27
Trying to connect to WiFi on an Acer Laptop with a BCM43228 802.11a/b/g/n [14e4:4359].


I can see WiFi networks listed, and connect to some but *not* to others.


The **Authentication Required by Wi-Fi network** prompt keeps coming up, even if I enter the correct password.


Had the same problem in 14.04 and 16.04. Tried upgrading twice, but the problem persists.


My wireless-info.txt file is here:


[http://paste.ubuntu.com/p/SjF.../]("http://paste.ubuntu.com/p/SjFTVzf9tj/")


Any suggestions to get this working?

---

### Post by praseodym on 2019-04-27
Which of the networks do you want to connect to?

Please show
```

sudo modprobe -rfv wl
sudo modprobe-v wl
dmesg | grep wl
```

---

### Post by modomobo on 2019-04-27
Hey, thanks for your message! I'm trying to connect to "Shin-Sekai-Net". Here's the requested output:

```

$ sudo modprobe -rfv wl
rmmod wl
rmmod cfg80211


$ sudo modprobe -v wl
insmod /lib/modules/4.15.0-48-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.15.0-48-generic/updates/dkms/wl.ko 


$ dmesg | grep wl
[   20.185073] wl: loading out-of-tree module taints kernel.
[   20.185081] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.188651] wl: module verification failed: signature and/or required key missing - tainting kernel
[   20.266342] wlan0: Broadcom BCM4359 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   52.564303] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.757404] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  325.007255] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1263.936036] ERROR @wl_dev_intvar_get : 
[ 1263.936049] ERROR @wl_cfg80211_get_tx_power : 
[ 1872.809572] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1873.225385] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2225.322132] ERROR @wl_dev_intvar_get : 
[ 2225.322146] ERROR @wl_cfg80211_get_tx_power : 
[ 5870.482135] wlan0: Broadcom BCM4359 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[ 5871.022251] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5871.374840] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by praseodym on 2019-04-27
> ```
[   20.188651] wl: module verification failed: signature and/or required key missing - tainting kernel
```
SecureBoot is disabled?

---

### Post by modomobo on 2019-04-27
> **praseodym said:**
> SecureBoot is disabled?

Not intentionally. Actually, I didn't know anything about this mechanism.

What steps should I take? Enable it? How?

---

### Post by jeremy31 on 2019-04-27
> **modomobo said:**
> Not intentionally. Actually, I didn't know anything about this mechanism.

What steps should I take? Enable it? How?

I wouldn't worry about it as Ubuntu is installed using Legacy Boot.  Secure Boot is only available when installing using UEFI and it would actually prevent the wifi driver from loading if Secure Boot is enabled

---

### Post by modomobo on 2019-04-27
Okay, thanks. What should I try next for the WiFi issue?

---

### Post by modomobo on 2019-04-30
Bump

---

### Post by modomobo on 2019-05-04
I'm still stuck on this.

I can connect to "shinjuku-library", but not to "Shin-Sekai-Net". Why not? I just keep getting the **Authentication Required** dialog.

Idk if it matters, but the former is listed as "type=802-11-wireless" whereas the latter is "type=wifi".

Any ideas...?

---

### Post by jeremy31 on 2019-05-04
The difference is likely encryption.  Why don't you try
```
sudo apt remove bcmwl-kernel-source && sudo apt install broadcom-sta-dkms
```
Reboot

---

### Post by modomobo on 2019-05-08
Sadly, that didn't work.

What should I try next?

---

### Post by modomobo on 2019-05-13
I'm still stuck on this. 

I'm wondering if the issue is my system not supporting **WEP Shared Auth (WEP-40)** encryption. It works fine connecting to other WiFi networks.

Here's my current wireless-info report:

[http://paste.ubuntu.com/p/wfZ.../]("http://paste.ubuntu.com/p/wfZgKXw6BZ/")

Interface is BCM43228 802.11a/b/g/n [14e4:4359].

Any suggestions to get this working?

**EDIT: Problem solved. I got the router switched to WPA2 and Ubuntu connected. Maybe there's no longer support for WEP(?).**

Thanks!

---

### Post by praseodym on 2019-05-13
"Thou shall not use WEP anymore", it is way too unsafe :-)

---

