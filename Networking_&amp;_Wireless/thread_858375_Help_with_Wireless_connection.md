---
title: "Help with Wireless connection"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by kcomico on 2008-07-13
I cannot connect to my wireless with my laptop. I can find my wireless network but I cant obtain an IP address. Is there anything I can do to fix this?

Router: Linksys Router WRT54G v8
Wireless card: Intel Pro/Wireless 3945A/B/G 802.11a/b/g 54Mbps MiniPCI Card

Thank you for any help.

---

### Post by pytheas22 on 2008-07-13
Please try to connect a couple times, and then immediately post the output of these commands:
```

dmesg
iwlist scanning
```

That will help figure it out.  dmesg will be very long, but it's useful.

Also, did your card used to work and break suddenly?  Or is this a new install of Ubuntu?

---

### Post by kcomico on 2008-07-13
iwlist scanning:

lo,eth0,wmaster0: Interface doesn't support scanning.
wlan0: no scan result


This is 1st time I install ubuntu.

---

### Post by pytheas22 on 2008-07-13
Thanks for the information, but please also include the output of the command:
```

dmesg
```

That's most important.  It's also important that you run dmesg right after trying to connect to the Internet (and not before!)...please do that and post it here.  There will be a lot of output but it's ok.

---

