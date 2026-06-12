---
title: "Bluetooth Network Access Point (NAP) and IP."
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by korakios on 2014-03-28
Hi I need your help please!
I connected a device thru bluetooth successfully  with the blueman applet 1.23. Then I enabled "Network Access Point (NAP)" and set type to dnsmasq with IP 192.168.1.1.
I need to know the exact ip my device has but it's not shown with ifconfig,netstat, arp commands. I believe it has something to do with the bluetooth protocol , but searching the web I couldn't find anything similar.Can anyone guide me?

---

### Post by korakios on 2014-04-06
To answer my question I used wireshark as a workaround  to monitor pan1 interface (bluetooth) and showed me the IP.

---

