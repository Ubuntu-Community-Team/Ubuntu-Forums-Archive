---
title: "ASUS X75VD / Atheros AR816"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by Aunt_Dot on 2013-09-30
This is my first experience with Linux. I've booted into a live environment and cannot get wireless to work. If I switch WiFi to On or Airplane Mode, it immediately switches back to off. If I try to set up the wireless connection manually in Network Connections (SSID and WPA2 password), it still will not connect. I did not look in ifconfig... It slipped my mind at the time.  I have an ASUS X75VD laptop, with an Atheros AR816 NIC. I tried googling similar problems with this model... From looking at an "rfkill list", my wifi shows as "being disabled by hard switch". I tried sudo rfkill unblock wifi, but that did not work nor change the rfkill list status (wifi still remained disabled by hardswitch). I also tried using the Fn key + F2 (the wifi icon key), as I have no physical switch on the laptop.  I am currently using Ubuntu 13.04, 64-bit. I had originally tried Ubuntu 12.04 and Linux Mint 15 (all 64-bit). The wireless did not work on those either.

---

### Post by varunendra on 2013-10-02
Welcome to the forums Aunt_Dot! :)

> **Aunt_Dot said:**
> ....with an Atheros AR816 NIC....

That doesn't sound like a familiar card. Please show us the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by bquillosa on 2013-11-09
hi I have the same specs of laptop and i want to know when i connect to wifi its very slow and then disconnected immidiately. whats the problem with that.im very new to ubuntu as far as i know this is the stable os out there but it is very tricky and not user friendly as it is.. please help me with my problem.. thanks

---

### Post by varunendra on 2013-11-09
Welcome to the forums bquillosa !

> **bquillosa said:**
> hi I have the same specs of laptop
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

