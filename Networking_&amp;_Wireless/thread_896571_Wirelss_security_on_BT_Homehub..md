---
title: "Wirelss security on BT Homehub."
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by auralay on 2008-08-21
I have a BT Homehub. It is an original white one, rumour is it's made by Thompson.

I have a Dell Inspiron 510m laptop, 2004 vintage, running 8.04 from USB harddrive.
I can get the wireless to work fine as long as I use WEP encription. 
If I try to set WPA-PSK it will not connect.
The hub gives the choice of WPA, WPA2 or WPA+WPA2 encription. No combination seems to work with any variation of the laptop setup.

Clue 1. Laptop connects fine on WPA when I run XP.
Clue 2. I have similar experience with an old Linksys WAP54G:- fine on WEP, no-go with any WPA setup.
Thanks, JG

---

### Post by pytheas22 on 2008-08-21
It's probably a problem with your wireless driver on Ubuntu, not the router.  Please post the following information so that we'll know which driver you're using:
```

lshw -C Network
lsusb
```

---

