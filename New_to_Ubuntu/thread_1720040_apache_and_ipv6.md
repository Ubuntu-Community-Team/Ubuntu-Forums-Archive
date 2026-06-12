---
title: "apache and ipv6"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by jba6511 on 2011-04-02
I am trying to get apache to work with ipv6. When I do an ifconfig, I see my machine is assigned an ipv6 address of fe80::a800:4ff:fe00:a04. My apache configuration is set to Listen 80, so based on what I have read I do not believe I need to do anything to allow me to access the apache server based on its ipv6 address. However, when I enter [http://[fe80::a800:4ff:fe00:a04]/](http://[fe80::a800:4ff:fe00:a04]/) into firefox 3.6.16, nothing happens. The ipv4 address returns the It Works! page. The version of apache is 2.2.16 and I have also checked to make sure firefox does not have ipv6 disabled. I also tried from another machine on my network to access apache via ipv6 but that fails as well. Also, when I check netstat I see that apache is listening on port 80 (0.0.0.0:80) but there is no equivalent ipv6 entry (:::80). Any ideas?

---

### Post by Sef on 2011-04-02
Can the devices, e.g., router, modem, etc., that you use to get access to the net have the ability use IPv6?

---

### Post by jba6511 on 2011-04-03
I believe they do as I can use ping6 to hit the other ipv6 enabled hosts on my LAN.

---

### Post by lemming465 on 2011-04-04
Does netstat -tln show anything listening on :::80?  If not, maybe your apache build wasn't configured with --enable-v4-mapped.  Try adding a *Listen [::]:80* directive as described in the [documentation]("http://httpd.apache.org/docs/2.2/bind.html").

---

