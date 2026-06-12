---
title: "Cellular modem - &quot;No SIM&quot;"
date: 2023-11-07
forum: Networking &amp; Wireless
---

### Post by stona1 on 2023-11-07
Hi,

I am going to make my Lenova Yoga gen 5 dual boot (Windows 11 and Ubuntu 23.10). Today before install I was tried Live USB to check will everything work under Ubuntu. 
I found that build in Cellular LTE Modem does not work. It says that there is no SIM. For sure there is SIM inserted in try - when boot in Windows 11 it is working OK. For test I switched SIM card to another operator and it shows the same error. Bellow I pasted detailed information. Can anybody help me to solve it?

ubuntu@ubuntu:~$ mmcli -L
    /org/freedesktop/ModemManager1/Modem/0 [Fibocom] L850 LTE Module","L850
ubuntu@ubuntu:~$ mmcli -m 0
  -----------------------------
  General  |              path: /org/freedesktop/ModemManager1/Modem/0
           |         device id: c838716d9d08ea0427b9097653417255596a8b6f
  -----------------------------
  Hardware |      manufacturer: Fibocom
           |             model: L850 LTE Module","L850
           | firmware revision: 18500.5001.00.05.27.30
           |         supported: gsm-umts, lte
           |           current: gsm-umts, lte
           |      equipment id: 015761002360527
  -----------------------------
  System   |            device: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0
           |           drivers: iosm
           |            plugin: Intel
           |      primary port: wwan0at1
           |             ports: wwan0 (net), wwan0at1 (at)
  -----------------------------
  Status   |             state: failed
           |     failed reason: sim-missing
           |       power state: low
  -----------------------------
  Modes    |         supported: allowed: 3g, 4g; preferred: none
           |           current: allowed: 3g, 4g; preferred: none

Best regards
Arek

---

### Post by 7upturbo on 2024-04-12
i have exactly the same issue. anyone knows how to solve this?

---

### Post by pai natal on 2024-09-29
I'm kinda on the same boat.. any ideas? Anyone?

---

