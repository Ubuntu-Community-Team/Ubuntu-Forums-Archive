---
title: "No option for drivers"
date: 2017-07-05
forum: Networking &amp; Wireless
---

### Post by darkestnight1 on 2017-07-05
I just dual booted Ubuntu with Windows 8. My broadcom internet chip and nvidia drivers and not enabled on default so I went into the settings to enable them. When it was searching for drivers it came up with no results. A window came up saying Ubuntu has experienced an internal error. I cant use the internet without enabling the broadcom chip so this is a big problem. Could enable the drivers on Ubuntu live usb but after i installed they are not there. Was this a bad installation?

---

### Post by jeremy31 on 2017-07-06
Open a terminal window and enter ```
lspci -nnk | grep -iA3 net
```
Post results

---

