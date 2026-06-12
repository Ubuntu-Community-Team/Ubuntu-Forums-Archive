---
title: "RTL8723BE Hard Blocked after suspend"
date: 2016-01-16
forum: Networking &amp; Wireless
---

### Post by Tarun_Kancharayan on 2016-01-16
My wifi gets hardblocked everytime I close and open my lid. Here's my rfkill list all outputs before and after suspend :

Before:
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

After:
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes

(Notice that bluetooth is missing)

Additional Info:
Laptop Model : Pavilion 15 ab032tx
Ubuntu version: 15.10
Current kernel : 4.2.0 (The previous kernel had the same bug. And yes, I've reinstalled the driver after the kernel update)
I've to restart the laptop if I want to get my wifi working again.
LAN works fine before/after suspend.
I've tried resetting my bios. Doesn't help.

---

### Post by Tarun_Kancharayan on 2016-01-17
bump.

---

### Post by Tarun_Kancharayan on 2016-01-17
I had problems downloading the wireless script previously. I've now attached the output before and after suspend. Any help would be very much appreciated.

---

### Post by Tarun_Kancharayan on 2016-01-20
Bump.

---

### Post by Tarun_Kancharayan on 2016-01-23
Bump.

---

