---
title: "No network"
date: 2023-01-18
forum: Networking &amp; Wireless
---

### Post by forgisound on 2023-01-18
I installed ubuntu but no network.  I can't find a way to install the driver.  I am new to Linux.

---

### Post by chili555 on 2023-01-18
Let's see if you have a networking device. Please open a terminal Ctrl+Alt+t and run:

```
lspci -nnk | grep -e 0200 -e 0280 -A3
```Post the result.

Is it wireless or ethernet that you want to use to connect to the internet? Is there any indication of a network device at the Network Manager icon at the top right?

[IMG]https://www.laravelcode.com/postimages/wi-fi-networks-device-not-ready-error-solve-in-linux-ubuntu-open-wifi-tab.jpg[/IMG]

---

