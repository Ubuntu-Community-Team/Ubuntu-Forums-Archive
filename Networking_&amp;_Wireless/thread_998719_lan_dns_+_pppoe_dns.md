---
title: "lan dns + pppoe dns"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by lucifer.anh on 2008-12-01
Computer receives from local network dhcp configurations. Among them dns is local dns server. 
After local network up /etc/resolve.conf contains what I need
nameserver 192.168.15.1

But after pppoe network is started local dns server disappears.
resolv.conf contains just internet dns servers. It is also because while pppoeconf it was said yes to change resolv.conf

Is it possible to have two dns servers (local and internet) anyway but not to manualy edit this file after pppoe started?
And isn't it a bug?

Thanks

---

### Post by superprash2003 on 2008-12-01
yes.. you may set up dns manually [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) .. opendns ips 208.67.222.222 and 208.67.220.220 used in this example.. you may change as you wish

---

