---
title: "Rtl8188ee will not connect to any access point"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by andrew-blake3 on 2013-12-28
I got a new HP Envy 15t and immediately removed windows 8 to install Ubuntu so I could use lvm whole disk encryption (and I also loathe windows8). Everything works great except my network cards eth0 RTL8111/8168/8411 and wlan0 RTL8188ee.  The wireless card sees all available access points so I know it's not the driver. When I put in my password, it never connects. I know it's not the AP because I turned off WPA2 temporarily and made it wide open with the same results. I tried downloading the 8188ce driver from Realtek but could not compile the source code. Gave me some error about reading the private key. Can someone please help me with this? I'd rather not return the laptop since it has almost everything I need. Thanks!

---

### Post by r3dd on 2013-12-29
Perhaps it is a problem with the keyring. Have you changed anything that would remove it or the wallet manager?

---

### Post by Bucky Ball on 2013-12-29
Is that ce rather than ee?

Could you provide the output of this command, please:

```
sudo lshw -C network
```

---

