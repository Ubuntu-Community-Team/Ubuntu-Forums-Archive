---
title: "[SOLVED] dynamic IP using free DynDNS service"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by borobudur on 2006-11-13
Hi, I have two questions to dynamic IP with dynDns. I followed this [howTo]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service"). It works fine, but:

1. I would like to test it by sending a request to my dhcp-server to get a new ip. Isn't there a command for that?

2. I need to run this script each time when I reboot my machine
```
sudo sh /etc/ppp/ip-up.d/dyndns_update.sh
```
How can I start it automatically at startup?

Thanks for your help.
borobudur

---

### Post by SSamiK on 2006-11-19
> **borobudur said:**
> 

2. I need to run this script each time when I reboot my machine
```
sudo sh /etc/ppp/ip-up.d/dyndns_update.sh
```
How can I start it automatically at startup?



I second that! Having a hard time remembering running the script manually at each reboot. :rolleyes:

---

### Post by speedman on 2006-11-19
apt-get install ddclient


Regards,

SM

---

### Post by borobudur on 2008-03-01
everything is fine with ddclient! Thanks!

---

