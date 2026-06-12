---
title: "Intel wireless adapter ac-3165 speed slower than windows (download)"
date: 2019-10-11
forum: Networking &amp; Wireless
---

### Post by antonbas on 2019-10-11
I have a dell gaming( i5577-7359BLK-PUS) with the following info

uname -a                                                                                                                                                                                                                                                                               
Linux devgamer 4.16.18-041618-generic #201806252030 SMP Tue Jun 26 00:33:13 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

rfkill list all                                                                                                                                                                                                                                                                     
0: hci0: Bluetooth
  Soft blocked: no
  Hard blocked: no
1: phy0: Wireless LAN
  Soft blocked: no
  Hard blocked: no


dmesg  | grep iwl                                                                                                                                                                                                                                                                       
 <NOT_MATCHES>    

The connection slow is 50% or less than others devices included the same laptop when is booted on windows, my provider gave 500Mbs/20Mbs and the for speed for the laptop on Linux is 150Mbs/17Mbs.

I would appreciate a lot their advices and where should I check to fix that.

PD: The rest of my devices MBP, Android tables/phones) gave me 400Mbs/18Mbs in the speedtest I do.

---

