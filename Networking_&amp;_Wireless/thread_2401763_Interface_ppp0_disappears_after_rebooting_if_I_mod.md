---
title: "Interface ppp0 disappears after rebooting if I modified the /etc/.../inferfaces file"
date: 2018-09-22
forum: Networking &amp; Wireless
---

### Post by tomhsiung on 2018-09-22
Hello,

I set up my connection to Internet via
```
sudo pppoeconf
```

It automatically created a interface called ppp0. I use the default settings for it except I don't enable the DNS fetching to resolve.conf because I have set up my own local DNS server (BIND). The most important thing is that the system automatically set up ppp0 interface on computer startups, so I don't need to run the ```
sudo pppoeconf
``` every time I reboot my computer.

Everything worked perfect. My board is Gigabyte H370N WiFi. So toady I tried to switch the 1700+ Mbps wireless network interface to a access point. However, I failed. In addition, if I manually modified the ```
/etc/network/interfaces
``` file, after rebooting, the ppp0 network interface disappears.

Interestingly, if I removed the changes (to configure the wireless interface) made to ```
/etc/network/interfaces
```, this issue resolved.

Tom

---

