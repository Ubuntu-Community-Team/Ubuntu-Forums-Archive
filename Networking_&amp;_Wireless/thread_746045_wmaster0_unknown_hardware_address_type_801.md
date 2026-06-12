---
title: "wmaster0: unknown hardware address type 801"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by aspora.isernia on 2008-04-05
Hi Guys,
each time I issue  ```
sudo /etc/init.d/networking restart
```besides the expected output I found two lines with  the error in the object... Moreover, the ifconfig command shows the interface wmaster0 with a weird HWaddress, namely the same than the wlan0 interface, but followed by a series of 00 pairs.
When I use nm-applet to connect via wi-fi, after a while, the nic suddenly stops working and I'm stuck without connection. A reboot is not enough to make the whole things work again: I have to turn off the laptop and restart again.
Any tips?

Thanks
a.i :)

edit: the dmesg command showed me this line "wlan0: RX disassociation from 42:08:fe:b3:7a:06 (reason=18 )"... More mysteries....

---

