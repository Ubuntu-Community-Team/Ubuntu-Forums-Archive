---
title: "default wireless usb network adapter driver of hardy heron?"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by eec on 2008-06-12
hi everyone,

i wanted to know which wlan adapter driver package is used and defaultly istalled  with ubuntu 8.04 (hardy) because it recognized my usb wlan adapter without any problem. 

Since  i am a new user, i don't know where to look for it. First i thought it was wlan-ng; however, it's just in the synaptic manager and not installed.

---

### Post by chili555 on 2008-06-12
I am not sure I completely understand your question. There are dozens of wireless drivers installed by default. If you want to know yours, open a terminal and do:```
sudo lshw -C network
```It should list your device and it's driver.

---

### Post by eec on 2008-06-12
yes i basically wanted to know it, thanks

---

