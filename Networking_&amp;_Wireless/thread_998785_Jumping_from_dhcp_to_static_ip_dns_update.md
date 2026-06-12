---
title: "Jumping from dhcp to static ip: dns update"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by gilberto.nakamura on 2008-12-01
I currently use a wireless network ( dhcp ) at home and sometimes at job. It works fine, i get a valid ip and the correct nameserver.

in order to access other machines at work, as they are ip-restricted, i need to setup my wired network. Again, it works fine because it gives me the correct ip, broadast and gateway. The problem is that I have to manually change my resolv.conf every time in order to use my wired network.

Is there any package/procedure that deals with this kind of problem?

thanks

---

### Post by superprash2003 on 2008-12-01
[http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) . This should help..opendns servers 208.67.222.222 and 208.67.220.220 used here.. you may change if you wish

---

