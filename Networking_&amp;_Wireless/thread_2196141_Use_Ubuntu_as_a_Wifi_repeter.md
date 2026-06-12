---
title: "Use Ubuntu as a Wifi repeter"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by apoc4l1pt0 on 2013-12-28
i have created an accesspoint with ubuntu to share the internet connection from an InternetKey, It's work, but the client that try to connect in this wifi network can't get the IP, because i need to configure the DHCP server

i have installed DHCP and this is my /etc/dhcp/dhcpd.conf

```

ddns-update-style none;
authoritative;
default-lease-time 600;
max-lease-time 7200
subnet 10.0.0.0 netmask 255.255.255.0 {
option routers 10.0.0.1;
option subnet-mask 255.255.255.0;
option broadcast-address 10.0.0.255;
option domain-name-servers 192.168.1.1;
range 10.0.0.10 10.0.0.20;
}

```

If i try  "isc-dhcp-server start" 
i receve an error : "JOB FAILED TO START"

What is the problem ?

---

