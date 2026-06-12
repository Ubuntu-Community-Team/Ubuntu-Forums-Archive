---
title: "WiFi connection fails nightly on 5.19.0-43-generic kernel"
date: 2023-06-15
forum: Networking &amp; Wireless
---

### Post by extraspecialbitter2 on 2023-06-15
I have been running Ubuntu 22.04 with zero WiFi issues until fairly recently. Now I find that WiFi disconnects nightly and won't connect until I shut off WiFi and turn it back on. There are also somewhat random WiFi drops throughout the day. The 5.19.0-43-generic kernel shows a date of May 22, and as I try to keep my system up-to-date, I suspect the update took place not long after that. We have several other computers connected to the same WiFi router that are not experiencing this issue.

A pastebin with the output of the `wireless-info` script is at [https://pastebin.com/HtkVzMdW](https://pastebin.com/HtkVzMdW).

---

### Post by extraspecialbitter2 on 2023-06-15
While awaiting some further guidance, I've decided to edit the file [COLOR=#4D5156][FONT=Roboto]/etc/NetworkManager/conf.d/default-[/FONT][/COLOR][COLOR=#5F6368][FONT=Roboto]**wifi**[/FONT][/COLOR][COLOR=#4D5156][FONT=Roboto]-powersave-on.conf and change the value [/FONT][/COLOR][COLOR=#5F6368][FONT=Roboto]**wifi**[/FONT][/COLOR][FONT=Roboto][COLOR=#4d5156].powersave from 3 to 2. I'll update this thread if it makes a difference with overnight WiFi connection failures.[/COLOR][/FONT]

---

### Post by extraspecialbitter2 on 2023-06-16
> **extraspecialbitter2 said:**
> While awaiting some further guidance, I've decided to edit the file [COLOR=#4D5156][FONT=Roboto]/etc/NetworkManager/conf.d/default-[/FONT][/COLOR][COLOR=#5F6368][FONT=Roboto]**wifi**[/FONT][/COLOR][COLOR=#4D5156][FONT=Roboto]-powersave-on.conf and change the value [/FONT][/COLOR][COLOR=#5F6368][FONT=Roboto]**wifi**[/FONT][/COLOR][FONT=Roboto][COLOR=#4d5156].powersave from 3 to 2. I'll update this thread if it makes a difference with overnight WiFi connection failures.[/COLOR][/FONT]

This morning it appears that the WiFi connection stayed up all night. I'm going to mark this "solved", although I'm baffled as to how this setting might have changed, as well as why "3" would be the default.

---

