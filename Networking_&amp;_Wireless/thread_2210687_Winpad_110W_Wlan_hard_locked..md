---
title: "Winpad 110W Wlan hard locked."
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by Brian_Ellse on 2014-03-12
Hi,

Running a clean install of Ubuntu 12.04 on an MSI Winpad 110W. Wireless card is "hardware switch" disabled, as per the GUI. Confirmed with rfkill list in terminal. In system settings, the wireless hardware is listed with a mac of 74:2F:68:9B:5C:B3.

Relative newcomer to Ubuntu, so need arrows painted on shoes to guide me please.

Thanks
Brian
Zimbabwe

---

### Post by chili555 on 2014-03-12
Please open up the terminal again and run and post:```
lspci -nn | grep 0280
lsmod | grep wmi
rfkill list all
```The pipe symbol | is on the right side of my keyboard on the same key with \.

I realize you may have to copy off the outputs with an old-fashioned pencil, but we need to see the diagnostics.

---

