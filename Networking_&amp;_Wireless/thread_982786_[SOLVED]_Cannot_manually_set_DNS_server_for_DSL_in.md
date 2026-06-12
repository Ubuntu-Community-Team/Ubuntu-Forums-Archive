---
title: "[SOLVED] Cannot manually set DNS server for DSL in nm-connection-editor"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by tomcheng76 on 2008-11-15
Hi, i use "DSL" Tab in "nm-connection-editor" to create my PPPOE connection.
However, i cant setup DNS server for the pppoe connection. As a result, i am using isp provided dns server now and it is bad ....

I tried to edit resolv.conf, dhclient.conf (prepend domain-name-servers 208.67.222.222,208.67.220.220;), every time reboot/networking restart restore the setting....

I understand that i can set DNS in Wired Connection tab, however, each ethernet adapter can only pick one from the wired or dsl connections.

IMHO, network manager is kind of bull ****...why dont we just use pppoeconf? why do i upgrade to Intrepid?

Please help :)
Thanks in advance.

---

### Post by superprash2003 on 2008-11-15
to solve your dns issue , follow this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by tomcheng76 on 2008-11-15
i tired with those network manager and dhclient...
for those who are interested, you can use this to lock the DNS server after editing resolv.conf
```

sudo chmod 444 /etc/resolv.conf
sudo chattr +i /etc/resolv.conf

```

---

