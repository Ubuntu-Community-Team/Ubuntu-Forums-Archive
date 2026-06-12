---
title: "&quot;No wifi adapter found&quot; after reboot - Dell E6520 with Intel Centrino Ultimate-N"
date: 2021-03-07
forum: Networking &amp; Wireless
---

### Post by Steve Kroon on 2021-03-07
I had performed various updates on my Ubuntu 18.04 system and needed to reboot.  On rebooting, the wifi adapter seems to no longer be detected.  In the past, the interface name was wlan0, now it seems to be "wwp0s29u1u6i6".

The result of the wireless-info script at [http://paste.ubuntu.com/p/MxpmNMYCzG/](http://paste.ubuntu.com/p/MxpmNMYCzG/) and attached.

---

### Post by jeremy31 on 2021-03-07
Uninstall the backports and reboot, the wwp0s29u1u6i6 device is cellular

---

### Post by Steve Kroon on 2021-03-07
Can you clarify what you mean by "uninstall the backports"?

---

### Post by jeremy31 on 2021-03-07
You installed some backport package of some sort as it shows the compat module is loaded, post results from terminal for ```
dpkg -i | grep backport; dkms status
```

---

### Post by Steve Kroon on 2021-03-07
I found your feedback on another thread - "sudo apt remove backport-iwlwifi" and the reboot sorted it for me.  Thanks so much!

---

