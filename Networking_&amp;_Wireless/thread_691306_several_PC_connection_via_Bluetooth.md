---
title: "several PC connection via Bluetooth"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by AzazelMazikin on 2008-02-08
I got two PC's running Ubuntu 7.10. Both have BlueTooth dongles in USB ports and both seems to connect fine to my phone's file transfer service when I choose Browse Device... from applet.
One PC has Internet connection, other hasnt, so I want to share it. I need to connect PCs into PAN network. So I made both dongles "Visible and connectable for other devices", in Services tab checked "Network service" so it became "Running". Then I said "ifconfig pan0 192.168.0.1" on first computer and "ifconfig pan0 192.168.0.2" on another. So, whats next? How should I connect them? There is no obvious buttons to click and when I tried do say "hcitool cc [address_of_bt_device]" it didnt made any sense.

---

