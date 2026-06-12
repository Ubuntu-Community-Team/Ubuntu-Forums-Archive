---
title: "Wireless card hard locked"
date: 2016-10-15
forum: Networking &amp; Wireless
---

### Post by mermaidman on 2016-10-15
I just installed ubuntu 16.04 but for some reason my wireless card doesn't work.  I checked my wireless settings from the terminal and it said the wireless card was hard locked.  I have a aspire ES 15.  I still have windows on my laptop so I checked the wireless cards and I have a Qualcomm Atheros AR956x wireless card and a Realtek PCIe GBE family controller under network adapters.  How do I unhardlock my wireless card?  I cant hook up to the internet on ubuntu so if I need drivers can I downloand them with windows and then install them with ubuntu?

---

### Post by chili555 on 2016-10-15
Please run and post:```
rfkill list all
lsmod | grep -e acer -e wmi
```

---

