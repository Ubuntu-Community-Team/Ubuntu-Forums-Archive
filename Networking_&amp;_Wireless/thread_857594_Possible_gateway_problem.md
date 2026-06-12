---
title: "Possible gateway problem"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by Omnutia on 2008-07-12
Dear forum goers,
I am building a home server and, as part of it, I am making an wireless access point using an Atheros card and the madwifi drivers. I have managed to bridge my ethernet and wireless card and am able to connect to the access point using my laptop using both windows and linux but I have the following problems.

1) Running firefox on the server, I can only reach the router "192.168.1.1" but no other IP or domain.
2) Running Ubuntu 8.04 on my connected laptop I cannot even connect to the router.
3) Running Windows XP on my connected laptop and using a static IP, everything works fine.

I have not yet started using hostapd as I wanted to get all the connections working first.
I think the problem has something to do with setting the gateway address; Could someone tell me how to do so through the command line (not using config files.) as it is the one address I cannot set with *ifconfig*.

Thank you for your time.

---

### Post by nixscripter on 2008-07-13
Depending on how you set this up, I would guess that this is caused by a lack of DNS information.

You need to either have your access point connected to however you get your internet service (cable? DSL? T1?) first, and then do IP masquerading on the other interface. Otherwise, it won't know how to look anything up.

You may also need a DHCP server so you can distribute the DNS information to the wireless clients. This is the Ubuntu client's problem; either it needs a static IP (you can do that with the **ifconfig** command) or it needs a dynamic one assigned to it (via DHCP on the AP). The windows box, has neither of these problems; it has a static IP, and probably remembers the DNS information from when it was connected at some point previously.

Some links, which I hope will help.

IP masquerading: [http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm)

DHCP server: [http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

More info about the dhcp.conf configuration file for that server: [http://www.yolinux.com/TUTORIALS/DHCP-Server.html](http://www.yolinux.com/TUTORIALS/DHCP-Server.html)

Hope this helps.

---

