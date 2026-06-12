---
title: "Ubuntu 17.10.1 No Wi-Fi Adapter Found"
date: 2018-03-24
forum: Networking &amp; Wireless
---

### Post by war97man on 2018-03-24
Hi, 
From what i read on the forums the usual problem here. I just istalled Ubuntu 17.10(first time using Ubuntu) and i can't make wi-fi to work.
 Wi-Fi panel displays ```
No Wi-Fi Adapter Found
```
Here it is my info text file [ATTACH]279063[/ATTACH]

---

### Post by jeremy31 on 2018-03-24
Go into BIOS/UEFI settings and disable Secure Boot.  That should allow the module to load

---

### Post by war97man on 2018-03-24
This was weird. I already had SECURE BOOT [DISABLED] but SECURE BOOT STATUS showed ENABLED. I toggled SECURE BOOT and now it seems to work. Thank you. I spent so much time looking for answers PFEW.\\:D/

---

