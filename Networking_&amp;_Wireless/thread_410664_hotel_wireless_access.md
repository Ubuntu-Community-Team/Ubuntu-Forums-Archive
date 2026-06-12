---
title: "hotel wireless access"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by martymcfry on 2007-04-16
Hi, I'm having problems accessing the hotel 's open AP.  I'm running edgy and Network Manager.  I'm able to successfully connect to the hotel's AP when I boot in Windows so I don't think they're blocking my IP.  I'm also able to connect to my wireless router when I'm at home so I know my wireless card works.  

I'm not sure if this makes a difference but in windows I can that the hotel has 6 APs with the same SSID but with varying signal strengths. 

Any ideas why I can't connect?  Thanks!

---

### Post by martymcfry on 2007-04-16
oh yeah, if i do iwlist scan in edgy, i can 6 of the hotel's APs (again, same SSID).. but in network manager I only see 1 entry.

---

### Post by amohanty on 2007-04-16
In a terminal first use iwlist to find the essids:

iwlist ethX sc

where ethX is your interface name.

If you can see the hotels AP (assuming there are no passwords) try this:

sudo iwconfig ethX essid hotel_ap_essid mode managed

see if that works.

HTH
AM

---

