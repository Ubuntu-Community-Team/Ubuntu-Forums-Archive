---
title: "dhcp3-server not submitting dns info"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by mrfloat on 2006-12-26
I just installed dhcp3-server since i use my PC as a router for my DSL internet connection. It works the way I expect it too, submitting all info needed to setup the internet connection (IP-address, subnetgateway) to the clients, except one thing: the addresses of the dns servers are not submitted.


This is what my /etc/dhcp/dhcpd.conf looks like:
```

ddns-update-style none;

option domain-name-servers 192.168.0.1, dns00.btx.dtag.de;
default-lease-time 2592000;
max-lease-time 2592000;#30d

authoritative;

log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.10 192.168.0.99;
        option routers ezra;
        option broadcast-address 192.168.0.255;
        #option domain-name-servers 192.168.0.1;
        #option domain-name-servers 194.25.2.130, 194.25.2.131;
}
```

---

### Post by mrfloat on 2006-12-27
:confused:

---

### Post by dbott67 on 2006-12-27
I think you need to remove the **[COLOR="Red"]#[/COLOR]** from the following line:
```
ddns-update-style none;

option domain-name-servers 192.168.0.1, dns00.btx.dtag.de;
default-lease-time 2592000;
max-lease-time 2592000;#30d

authoritative;

log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.10 192.168.0.99;
        option routers ezra;
        option broadcast-address 192.168.0.255;
        [COLOR="Red"]#option domain-name-servers 192.168.0.1;[/COLOR] [COLOR="Blue"]<--- remove the # from this line[/COLOR]
        #option domain-name-servers 194.25.2.130, 194.25.2.131;
}
```

Just change the IP address to the IP address of the new DHCP server.

-Dave

---

