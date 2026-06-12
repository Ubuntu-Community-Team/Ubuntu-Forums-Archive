---
title: "A very strange issue with DSL modem"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by Asix on 2007-03-12
Heya everyone,
here's the situation: in my home there is one DSL modem which has both USB and Ethernet ports. One computer is connected to it through USB and is running Windows XP Professional, while the other computer connects to it through Ethernet and is running Kubuntu 6.10 (updated with the latest KDE and other packages, to the max).
The problem is that there is DSL connectivity until I create another normal user in Kubuntu and try to connect to the Internet using that newly - created account. Then, a very strange thing happens.
The modem locks up, and there's no DSL connectivity at all, I am not even able to access its own control module by web interface (by typing 192.168.1.1 in the browser's address bar, that is).
The only way to get DSL connectivity back is to turn off the modem for a few seconds and turn it on again. Then everything works fine unless I try to access the Net using the newly - created account in Kubuntu. Then the whole thing repeats again.
By the way, the connection is persistent, I don't need to connect to the Internet, I am connected as soon as I turn on my computer, and Kubuntu uses DHCP to obtain internal IP address from the modem.
The modem is SmartAX MT882u manufactured by Huawei Technologies.
Is there a workaround for this? Thanks in advance.

---

### Post by dmizer on 2007-03-13
your modem is not a router.

this means that you can use either the ethernet or the usb, but not both at the same time.  further ... even if you ARE able to use both at the same time, your modem will have VERY VERY limited routing capabilities.  so it's no surprise that another user messes up the works.

best bet here is one of two things:
1) to set up an internet connection sharing configuration for your local network
2) purchase an actual router.

---

