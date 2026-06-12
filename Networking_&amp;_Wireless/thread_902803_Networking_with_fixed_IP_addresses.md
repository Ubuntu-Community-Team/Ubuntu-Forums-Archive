---
title: "Networking with fixed IP addresses"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by Vegan on 2008-08-27
If I setup Ubuntu with DHCP it works fine, but if I change to a fixed IP address for use with server software, the shares fail. I tried adding:

127.0.0.1 wins

to the hosts and no effect, any thoughts. I need to have Windows 9x to Vista interoperate.

I am using a Linksys WRT54G with cat6 wire connections. Only some Win boxes use wireless.

Samba does not work either

---

### Post by Iowan on 2008-08-27
Put 127.0.0.1 back to **localhost**. You can make 127.0.1.1 your hostname (I have one machine with local address 192.168.x.x as hostname). Server *may* need to have **winbind** installed, and edits to **/etc/nsswitch.conf**

---

### Post by Vegan on 2008-08-28
I changed my hot back to localhost as you suggested, and added my URL followed by UBUNTU which is the local machine name.

Still cant get the web server to recognize the URL.

I wonder if I should install the DNS service?

---

### Post by DreadedOne509 on 2008-09-03
On a couple of my machines I've needed to edit the /etc/hosts file like this -

127.0.0.1 localhost
127.0.0.1 machinename.localhost

So far, only on 8.04 though. Although, 1 box insists on this -

127.0.0.1 localhost
127.0.1.1 machinename

---

