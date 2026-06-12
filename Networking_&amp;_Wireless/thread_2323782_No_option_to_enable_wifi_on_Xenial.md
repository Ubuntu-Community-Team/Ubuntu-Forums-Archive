---
title: "No option to enable wifi on Xenial"
date: 2016-05-08
forum: Networking &amp; Wireless
---

### Post by Fh7p6mG on 2016-05-08
I have done  clean install on my laptop of Xenial (was previously on Wily) and mostly it's fine, but I cannot seem to find an option to enable wifi, even though it's picked up my wifi device. Anyone know why?

rfkill doesn't show it as blocked

```
$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by jeremy31 on 2016-05-08
*Thread moved to **Networking & Wireless**.*

Sounds like the network manager [bug](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1576726)

This command should fix it

```
systemctl restart NetworkManager.service
```

You will need to run the command after every reboot until the fix comes out

---

