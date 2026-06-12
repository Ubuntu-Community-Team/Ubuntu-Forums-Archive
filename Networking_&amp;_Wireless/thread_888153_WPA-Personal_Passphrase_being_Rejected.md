---
title: "WPA-Personal Passphrase being Rejected"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by Dalius on 2008-08-12
Hello all. I was wondering if anyone had any ideas regarding this problem I've been having.

My wireless home network uses WPA1-Personal for security protection. Computers running Windows Vista and OS X seem to be connecting fine, yet 8.04 is giving me some problems. Network-manager is constantly rejecting the passphrase, even though it's correct. 

I'm able to connect to the wireless network with WEP protection or open, but WPA's passphrase system is a lot more handy to use then WEP hex keys, especially with multiple PCs/consoles connected via WiFi to the network.

I'm using ndiswrapper for drivers (Broadcom) and wpasupplicant is installed, although I'm not quite sure what it does. Anyone have any advice? :confused:

---

### Post by AaronMT on 2008-08-12
Forgot to post your wireless adapter

```
lspsci -v | grep Network
```

---

### Post by Dalius on 2008-08-12
```
05:01.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
```

---

### Post by AaronMT on 2008-08-13
bump

---

