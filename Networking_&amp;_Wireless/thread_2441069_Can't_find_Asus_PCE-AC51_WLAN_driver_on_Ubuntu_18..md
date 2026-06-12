---
title: "Can't find Asus PCE-AC51 WLAN driver on Ubuntu 18.04.4"
date: 2020-04-18
forum: Networking &amp; Wireless
---

### Post by krishnau on 2020-04-18
Hey, 
I'm new to Ubuntu, I really appreciate your help. 

The hardware is plugged in properly, but when I go to "Wi-Fi", I get no wifi adapter found notification.

[https://pastebin.com/yjasB3vK](https://pastebin.com/yjasB3vK)  (followed instructions from "Before posting in Networking & Wireless")

I tried this advice because it seems like this person faced a similar problem, it didn't solve my problem ([https://www.linuxquestions.org/questions/linux-newbie-8/asus-pce-ac51-wlan-adapter-driver-doesn%27t-install-properly-4175619526/):](https://www.linuxquestions.org/questions/linux-newbie-8/asus-pce-ac51-wlan-adapter-driver-doesn%27t-install-properly-4175619526/):) 

 1) Go to [https://github.com/lwfinger/rtlwifi_...rmware/rtlwifi](https://github.com/lwfinger/rtlwifi_...rmware/rtlwifi)
2) Download rtl8812aefw.bin and rtl8812aefw_wowlan.bin
3) Copy both files to /lib/firmware/rtlwifi
4) Restart computer


Thank you for your help.

---

### Post by CelticWarrior on 2020-04-18
Not a similar problem... In your link the user has their card detected. Yours isn't.
Please check connection, slot, UEFI/BIOS settings, etc.

---

### Post by krishnau on 2020-04-19
Hi, 
What do I check in the UEFI/BIOS setting? I'll also open the PC and check the connection slot. 

Thank you for your help!

---

### Post by CelticWarrior on 2020-04-19
In UEFI or BIOS you should check if there's some setting to enable/disable networking.

---

