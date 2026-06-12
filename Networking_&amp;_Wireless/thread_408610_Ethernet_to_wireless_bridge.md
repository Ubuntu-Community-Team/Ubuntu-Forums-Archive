---
title: "Ethernet to wireless bridge"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by EvanPMeth on 2007-04-13
I have been trying to get a bridge working through my desktop for my old ibook.
My setup is:
Internet------>Router(192.168.1.1)---*<wireless>*-->**[wlan0]**Desktop(192.168.1.203)**[eth0]**---*<wired>*---->iBook(DHCP)

I tried installing bridge-utils and doing the following:
```
 sudo brctl addbr "ibook"

 sudo brctl addif "ibook" wlan0

sudo brctl addif "ibook" eth0

sudo dhclient ibook

```
dhclient acts like there is no connection and pings the router with no responce just as if it were disconected.

at this point my internet through wlan0 is gone

and sudo route looks as follows:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
``` 
with nothing.

so i uninstalled bridge-utils and reboot and the network works fine.

I think i am missing something.


-EvanPMeth

---

### Post by dbott67 on 2007-04-13
I'm not familiar with bridge-utils, however, many people have used iptables & masquerading to accomplish this.

Try these documents:

[http://doc.gwos.org/index.php/Share_Internet_Connection](http://doc.gwos.org/index.php/Share_Internet_Connection)
[http://www.debuntu.org/iptables-how-to-share-your-internet-connection](http://www.debuntu.org/iptables-how-to-share-your-internet-connection)

-Dave

---

