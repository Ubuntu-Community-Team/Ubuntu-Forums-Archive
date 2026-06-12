---
title: "Dell Latitude E5430 drivers"
date: 2018-03-31
forum: Networking &amp; Wireless
---

### Post by moto1860 on 2018-03-31
Hi all, I've just installed Ubuntu's latest release on my Latitude, can someone help me out on installing drivers for my hardware? I can't use my wi-fi at the moment.

---

### Post by jeremy31 on 2018-03-31
*Thread moved to **Networking & Wireless**.*
Please see the wireless script in my signature and post results

---

### Post by moto1860 on 2018-03-31
How do I donwoload and run the wirless info script? Just clicking on the link? 
Anyways it can't seem to recognise any wi-fi device.

---

### Post by jeremy31 on 2018-03-31
The instructions are at the link

---

### Post by moto1860 on 2018-03-31
This is the pastebin link: [https://pastebin.com/ZaML3sLL](https://pastebin.com/ZaML3sLL)

---

### Post by jeremy31 on 2018-03-31
In terminal ```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```
Reboot and make sure Secure Boot is off in UEFI/BIOS

---

### Post by moto1860 on 2018-03-31
> **jeremy31 said:**
> In terminal ```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```
Reboot and make sure Secure Boot is off in UEFI/BIOS

It's working, thanks a lot. I still need drivers for the rest of the hardware, do I open a new thread in Hardware section or we can move this one back?

---

### Post by jeremy31 on 2018-03-31
I would start a new thread in hardware and say what other hardware isn't working.  It might help to give some idea of what hardware you have ```
sudo apt-get install inxi && inxi -Fxxxzc0
```
and paste the results using code tags

Use the thread tools near the top right of page to mark as solved

---

### Post by moto1860 on 2018-03-31
Thank you!!

---

