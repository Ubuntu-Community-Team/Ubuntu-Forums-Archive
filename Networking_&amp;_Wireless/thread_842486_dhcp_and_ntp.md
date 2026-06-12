---
title: "dhcp and ntp"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by tizo_rh on 2008-06-27
Hi there,

I have an Ubuntu box, using a win2003 dhcp, and ntpd, with ntp servers configured statically in /etc/ntp.conf.

I would like to know, if Ubuntu could use the ntp servers dynamically assigned by DHCP, instead of the statically configured ones. I have been searching a way, but I couldn't find one. 

Do you know a way?. Maybe I have to discard using ntpd?

Thanks very much,

tizo

---

### Post by chili555 on 2008-06-27
You aren't confusing NTP, or network time protocol, servers with DNS, or domain name system, servers, are you? As far as I know, DHCP gives you an IP address and DNS information and has nothing to say about NTP.

Unless you have done some serious configuration within the depths of your Ubuntu box, it will automagically use the DNS servers offered by the DHCP server.

---

### Post by tizo_rh on 2008-06-27
chili555, thanks for your reply.

I am not confusing NTP with DNS. DNS servers works perfectly, but DHCP can also be configured to give NTP server address. The DHCP client can be configured to take these servers into account, or not. As an example, my /etc/dhcp3/dhclient.conf file, looks like the following:

request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;


Note that one of the parameters is "ntp-servers".

---

