---
title: "Ndiswrapper Problems"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by Nightmare JG on 2006-12-04
I'm having problems with the wireless card in my laptop.
Linux (lspci) identifies it as:
```
06:09.0 Ethernet controller: Winbond Electronics Corp Unknown device 0033
```

and Ndiswrapper says:
```
netw33          driver installed, hardware present
```

But, I don't have a wlan0 device, nor any at all except eth0, sit0, and lo. I can't find any other version of this driver, and this seems to be a pretty rare card, how do I find out what chipset it's using?
Any idea's to get it to work?

Thanks,
Jacy Gaddis

---

