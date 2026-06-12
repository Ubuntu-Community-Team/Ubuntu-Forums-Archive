---
title: "linksys wusb54gc different drivers?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by mike22 on 2008-12-09
Hi, I have a couple of questions. I always thought that the driver for linksys wusb54gc is a ralink rt73 driver. However, when I start my laptop and connect to the internet, the driver is listed as rtl8187? How do I change it back to rt73? I get limited internet with rtl8187. The only way I get internet with rtl8187 is if I'm within 15 feet or so from my router. I have two different wifi adapters. One of the them is a zd1211rw my essentials wifi adapter. Also, as I checked the connection information, I noticed different wifi interfaces, wlan0 and wlan1, or 2, I can't remember. Could that be a problem? Thanks.

---

### Post by Old_Grey_Wolf on 2008-12-09
I probably can not help you because the wusb54gc has worked OOTB for me since 7.10. If you provide more information about the Ubuntu version you are running, the wireless router you are connecting to, what encryption you are using (WEP/WPA/WPA2), etc., maybe someone else can.

---

### Post by mike22 on 2008-12-09
Here is my system info:

```
Ubuntu
Release 8.10(intrepid)

Kernel Linux 2.6.27-10-generic

GNOME 2.24.1
```

I'm using wpa/wpa2 to connect to my ap. The router I'm using is a linksys wrt54gs.

---

### Post by mike22 on 2008-12-10
bump.

---

### Post by silverglade00 on 2008-12-10
try adding rtl8187 to /etc/modprobe.d/blacklist and rebooting

---

### Post by mike22 on 2008-12-10
> **silverglade00 said:**
> try adding rtl8187 to /etc/modprobe.d/blacklist and rebooting

ok, I'll try. How do I blacklist rtl8187?

---

### Post by mike22 on 2008-12-10
I get internet with wusb54gc rtl8187 driver (not rt73 unfortunately) but it's limited internet in wifi range. Why is the range so limited with rtl8187?

---

