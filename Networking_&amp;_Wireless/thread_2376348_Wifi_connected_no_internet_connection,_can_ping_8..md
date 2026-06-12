---
title: "Wifi connected no internet connection, can ping 8.8.8.8"
date: 2017-11-02
forum: Networking &amp; Wireless
---

### Post by nlmercado on 2017-11-02
Hello,

Just installed my first XUBUNTU 16.04, was able to connect to Wi-Fi but no internet connection.
I can ping my dsl router and 8.8.8.8 google's dns but cannot resolve domain names [www.google.com]("http://www.google.com") etc.
checked several articles in the network and Wi-Fi thread and result is still the same.


Thanks,

---

### Post by cc1984 on 2017-11-02
If you can ping 8.8.8.8 but can't ping [www.google.com](www.google.com) it sounds like you have a DNS issue. Are you using DHCP on your local network? Do other devices on your network have this issue?

---

### Post by cc1984 on 2017-11-02
You can verify if the DNS is working by running:
```
host google.com
```

If you are having a DNS issue this will return with a time out.

Then run:
```
host google.com 8.8.8.8
```

If this then returns an address for google.com your issue is with your DNS.

---

### Post by HermanAB on 2017-11-02
To see whether DNS is configured right:
$ nslookup [www.google.com](www.google.com)

To reconfigure the DNS resolver:
$ sudo dhclient eth0

This should be handled automatically by NetworkManager process.

---

### Post by jeremy31 on 2017-11-02
*Thread moved to **Networking & Wireless**.*

---

