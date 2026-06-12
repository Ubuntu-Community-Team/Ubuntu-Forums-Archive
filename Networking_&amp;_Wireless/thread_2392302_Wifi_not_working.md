---
title: "Wifi not working"
date: 2018-05-19
forum: Networking &amp; Wireless
---

### Post by mtbadsha-gmail on 2018-05-19
I am using ubuntu 18.04 LTS on Asus Vivobook, my wifi driver is not installing automatically. 
can any body please help me on this[ATTACH=CONFIG]279751[/ATTACH][ATTACH]279752[/ATTACH][ATTACH=CONFIG]279751[/ATTACH][ATTACH]279752[/ATTACH]

---

### Post by howefield on 2018-05-19
Thread moved to the more appropriate "*Networking & Wireless*" forum.

---

### Post by jeremy31 on 2018-05-19
This should get it working
```
sudo apt get install git dkms build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```
Reboot

---

### Post by mtbadsha-gmail on 2018-05-19
thanks for the reply, did the same as per your instructions, but still problem same

---

### Post by jeremy31 on 2018-05-19
Does ```
mokutil --sb-state
```
Show Secure Boot is enabled?
If it does, disable Secure Boot in UEFI/BIOS

---

