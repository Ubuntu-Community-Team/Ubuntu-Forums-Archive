---
title: "Wlan and ethernet connect to my router but no browse"
date: 2018-09-01
forum: Networking &amp; Wireless
---

### Post by jbrian420 on 2018-09-01
I can access my router and ping my gateway but not google. I am using an AT&T modem/router and do not have any filtering or blocking setup within the router. I have had the same issue with multiple live linux flavors and currently have a fresh install of ubuntu studio 18.4 on my laptop. 

Oddly enough I can connect to my wifi Hotspot on my phone that's also using WPA encryption with no issues.

I have no issues using same hardware under windows. I have used 2 seperate usb nic adaptors with same issues.

Any ideas because this is driving me nuts.

---

### Post by jbrian420 on 2018-09-01
I found my problem but don't understand why it doesn't work. I factory reset my AT&T router and one by one put settings back that I like until issue returned. For whatever reason Linux doesn't like my ip scheme for my dhcp server.

169.254.128.1 as my dhcp server and I can no longer browse on my laptop but I can access my router still and make changes. 

Any ideas why or a workaround?

---

### Post by chili555 on 2018-09-01
169.254.anything is not a valid working IP address to be used in a router: [https://www.webopedia.com/TERM/A/APIPA.html](https://www.webopedia.com/TERM/A/APIPA.html)

---

### Post by jbrian420 on 2018-09-05
Actually it can be valid. I use this ip range professionally. I am an enterprise installer for Hughesnet and we set all of our dsl routers and cradlepoints with this exact same ip range. That's actually why I use it at home so I can pre-programmed fortinet routers for work. Every device I have thrown at this configuration works except Linux. I find that very odd. Within my home network using a 169.254.128.1 ip range I have over 20 devices connected fine with no issues. I introduce a Linux pc and problems arise.

---

### Post by chili555 on 2018-09-05
Let's see:```
ls -al  /etc/resolv.conf
```

---

### Post by SeijiSensei on 2018-09-05
Choose one interface, probably the Ethernet connection, and disable wifi.  A machine with two addresses to the same router will cause routing problems.

Usually Ubuntu adds a route to the 169.254 network, which Windows uses as the default.  Let's see the result of the command "route -n".

There is no performance improvement from having both interfaces connected to the router unless you use "[bonding]("https://help.ubuntu.com/community/UbuntuBonding")."

---

