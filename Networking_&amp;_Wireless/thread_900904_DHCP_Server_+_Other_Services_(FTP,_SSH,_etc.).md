---
title: "DHCP Server + Other Services (FTP, SSH, etc.)"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by firefly2442 on 2008-08-25
I setup dhcp3-server and it works great for sharing my Internet connection.  My other machines can connect via ethernet and access the internet.  However, I can't seem to access my HTTP, FTP, or SSH services on the same machine acting as the router.  I can ping other machines from my router as well as ping from my other machines to the router.  However, I still can't connect to the services.  Here is my dhcpd.conf file:

```
########################
# DHCP Server
# 8/24/08
########################

ddns-update-style none;

option domain-name-servers 69.5.139.3, 69.5.136.253;

default-lease-time 86400;
max-lease-time 604800;

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.100 192.168.1.200;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.1.255;
        option routers 192.168.1.1;
}
```


Do I need DNS or some other type of service running?  Is there a way to assign another IP address so I can access my services yet still have the DHCP server running?  Thanks! :)

---

### Post by firefly2442 on 2008-08-25
Well, it turns out it's a firewall issue.  I used firestarter (firewall) to setup my internet connection sharing and for some reason didn't realize it was running as a service.  Anyway, it was sharing my connection but blocking access by everything trying to connect to it via my LAN.  I'm trying to see if I can figure out how to start firestarter as a service but turn the firewall portion off by default.

---

### Post by firefly2442 on 2008-08-26
Well, I couldn't figure out how to have firewall start without the firewall feature turned on so I just punched a hole in the firewall and only allowed the IP addresses in my DHCP server block.

---

