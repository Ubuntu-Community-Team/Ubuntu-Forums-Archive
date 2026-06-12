---
title: "Hostap doesn't work!!"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by iceseyes on 2006-10-25
Hi, I have a problem with hostap. Since Dapper I can't use hostap drivers with networkmanager/wpa_supplicant because it find my wep network but doesn't connect to it. I receive a lot of errors in syslog like this:
```

wifi0: CMD=0x0121 => res=0x7f, resp=0x0004
wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE faild (res=127, rid=fc48, len=2)
wifi0: short HostScan result entry (28/64)

```

I have a Intersil Prism2.5 card! I'd like to use NetworkManager because i switch a lot from cable network and a few of wifi nets!

another problem is this: with kernel 2.17-7 I can use orinoco with networkmanager and all work fine, but when I use 2.17-10 networkmanager doesn't find the wireless network!! and so it is for iflist scan!

I'll try to find a solution with google but nothing I've found! Can you help me with hostap?

---

