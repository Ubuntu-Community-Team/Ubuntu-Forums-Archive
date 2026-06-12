---
title: "I can't connect to WiFi 6ghz when SIDD is hidden"
date: 2023-03-04
forum: Networking &amp; Wireless
---

### Post by 27hf4-1 on 2023-03-04
recently I  bought 6E router  with 6ghz/wpa3 functionality. However due to unknown reason I can't connect my Ubuntu to router 6ghz network when sidd is hidden  (works well with 2.4ghz and 5ghz hidden and it works  
well with 6ghz when broadcasting ssid). I can connect other devices to router 6ghz hidden network, as well windows11 from the computer where is my ubuntu (same hardware). The problem seems to be  with Ubuntu settings or driver.  

[COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial] uname -a
     Linux ======= 6.2.2-060202-generic #202303031131 SMP PREEMPT_DYNAMIC Fri Mar  3 11:39:20 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

lsusb
[/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]Bus 002 Device 007: ID 8087:0032 Intel Corp. AX210 Bluetooth


lsb_release -a 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy

 lspci -nnk | grep -A2 0280 
07:00.0 Network controller [0280]: Intel Corporation Wi-Fi 6 AX210/AX211/AX411 160MHz [8086:2725] (rev 1a)
    Subsystem: Intel Corporation Wi-Fi 6 AX210 160MHz [8086:0024]
    Kernel driver in use: iwlwifi

nmcli c up id "====="
Error: Connection activation failed: The Wi-Fi network could not be found
Hint: use 'journalctl -xe NM_CONNECTION=c9f9dee5-03e2-4bf1-ad93-cd55bdff6458 + NM_DEVICE=wlp7s0' to get more details.

Thanks

---

