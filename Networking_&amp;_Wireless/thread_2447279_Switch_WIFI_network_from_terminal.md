---
title: "Switch WIFI network from terminal?"
date: 2020-07-16
forum: Networking &amp; Wireless
---

### Post by harry5552 on 2020-07-16
Using Ubuntu 20.04

I'm trying to find a way of switching WIFI networks using the terminal e.g a command/shell script to switch from ssid WIFI_A to WIFI_B etc...

dabbled with iwconfig but nothing seems to work - any ideas please?

---

### Post by &amp;KyT$0P# on 2020-07-16
If you're using NetworkManager, as is standard for Ubuntu 20.04, have you looked into [FONT=Courier New]nmcli[/FONT] ?

There's also [FONT=Courier New]nmtui[/FONT] if you don't need to script this.

---

### Post by harry5552 on 2020-07-16
wow, that is exactly what I was after, thanks so much

---

### Post by &amp;KyT$0P# on 2020-07-16
You're welcome. :KS

---

