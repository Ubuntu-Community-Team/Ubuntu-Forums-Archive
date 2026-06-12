---
title: "Where are NetworkManager connections being stored ?"
date: 2024-09-04
forum: Networking &amp; Wireless
---

### Post by landjalan on 2024-09-04
hi,

I created 2 wlan connections as user. I want to reuse them (their profiles), but I don`t find the location where they are stored at. It is not /etc/NetworkManager/system-connections (99% of google search results offer that path).

I also did not find anything in the user home die (.local or .config)


Thanks a lot

---

### Post by jeremy31 on 2024-09-04
Check in /etc/netplan for 24.04

---

### Post by landjalan on 2024-10-29
Thank you !

---

