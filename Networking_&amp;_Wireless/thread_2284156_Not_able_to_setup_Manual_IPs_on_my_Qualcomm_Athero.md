---
title: "Not able to setup Manual IPs on my Qualcomm Atheros WiFi card, Lenovo Machine"
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by prashant-kocherlakota7 on 2015-06-27
I'm able to connect to WiFis (also can't setup static IPs over ethernet) with dynamic IPs just fine. When I try to change the option to manual IPv4 in the network manager, the save button grays out and I'm just not able to set up a static IP. Lots of people seem to be having this issue. I was running 14.04LTS (Unity) until 2 weeks back and I didn't have this bug. Then I installed 14.04.2, 15.04, 14.10 - both Gnome and Unity and this issue doesn't go away. I've looked up other forum threads and things that don't work for me are:

1. Don't hit tab.
2. Don't click new entry at the end of entering details.
3. My IPv4 details are accurate. I'm sure of that. 

Please help! I've been struggling with this real bad.

---

### Post by chili555 on 2015-06-27
Network Manager won't let you save settings if it believes the settings are incomplete and therefore unworkable. The most common error is failure to specify DNS nameservers. They are required.

Please be sure your settings are specified as here. Of course, substitute your exact details.

[ATTACH=CONFIG]262881[/ATTACH]

---

