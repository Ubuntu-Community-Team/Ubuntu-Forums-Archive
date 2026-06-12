---
title: "Smartlink es 2838 2839 modem trick"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by Omnios on 2006-09-30
Hi my dad has a Smartlink es 2838 2839 modem.  
I found that this dial up modem works out of the box and only needs to have the modem port set in network config. To find your port with this modem you can run the following command in the Terminal.
```
 $ sudo wvdialconf /etc/wvdial.conf
```this will tell you the modem port wich will allow you to open 
Menu / Sytem / Administration / Networking 
When the networking window opens choose modem connection and choose properties. Now click on the modem tag and enter the modem port and fill ut your dial up isp connection settings
I after figuring this out his modem worked without the addition of any extra drivers.

---

