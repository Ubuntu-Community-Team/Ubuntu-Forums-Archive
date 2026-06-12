---
title: "Unexplained continuous downloads on hotel wifi- Egypt"
date: 2015-07-11
forum: Networking &amp; Wireless
---

### Post by fallenstardust on 2015-07-11
Hi,

When the wifi connects it starts downloading at around 200KiB/s before I've even logged into the hotel's wifi web page to get it connected. This continues through the whole session. Is there any way I can see where it is going? What it is? It's not a Chrome download and it occurs after Chrome is closed.

Ubuntu Gnome 15.04 on a Sony Vaio.

Thanks

edit. just checked terminal where i was running chrome from, got this error message like 100 times

[3948:3948:0711/075152:ERROR:CONSOLE(1)] "Uncaught ReferenceError: downloads is not defined", source:  (1)

related?

---

### Post by tgalati4 on 2015-07-11
Install *etherape* and run it and note the IP addresses to where the data is going.  Then use *whois* to who owns the IP addresses.

If you have a LiveUSB stick, boot off of it and see if you have the same behavior.

It's possible that the hotel's router has been compromised.  If you have a lot of add-ons to chrome, it's possible that it is trying to update them or synchronize them.  Try *firefox* and see if you get the same behavior.

---

