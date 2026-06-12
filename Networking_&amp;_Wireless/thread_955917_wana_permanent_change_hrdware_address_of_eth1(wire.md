---
title: "wana permanent change hrdware address of eth1(wireless)"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by usman idrees on 2008-10-22
hi 
i have been googling today to find a method to permanently change my hardware address (i mean eth1 not eth0 ) but in vain....can anybody plzzzzzzzzz help me ????
the interfaces file looks like this now...

auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-key 0d539292c38cc1bfa980765613
wireless-essid h.net

auto eth1
iface eth0 inet dhcp

auto eth0

---

### Post by kilroy423 on 2008-10-23
[http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)

```
hwaddress ether 01:02:03:04:05:06
```

---

### Post by usman idrees on 2008-10-23
hi 
i tried but i didnot work....
can u plz tell me the exact location to add it in my interface file??
thanks

---

### Post by kilroy423 on 2008-10-23
Did you restart the service?  Did you look at the link I provided?

---

