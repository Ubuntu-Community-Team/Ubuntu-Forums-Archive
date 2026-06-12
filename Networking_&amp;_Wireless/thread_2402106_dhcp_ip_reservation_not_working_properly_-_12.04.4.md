---
title: "dhcp ip reservation not working properly - 12.04.4 LTS"
date: 2018-09-26
forum: Networking &amp; Wireless
---

### Post by eby on 2018-09-26
Not sure if this can be posted here,

I'm facing issue with dhcp server not respecting ip reservation for some devices(laptops/desktops) in the network, the server would assign reserved IP to other devices and when the reserved device is connected to the network, it would assign the reserved IP resulting ip conflict !!!!. Have searched for a solution for this without any resolution. 

Have tried deleting unreserved entry from dhcpd.leases and service restarted, this works for few days or so, then back to square 1.

Observation 1: When the server assign ip to some other device other than reserved, entry in dhcpd.leased is, even after deleting entry and restarting service.
```
binding state active;
next binding state free;

```

Observation 2: Devices that are reserved, but not disconnected/Powered Off daily (IP Phones, AP, ThinClients) don't get their IP assigned to another device.
Note: Maximum number of devices do not exceed 300.

dhcp server configuration - ip reservations excluded,

Ubuntu 12.04.4 LTS, isc-dhcp-server version - 4.1.ESV-R4-0ubuntu5.11
```

authoritative;

##### Network #####
subnet 172.16.6.0 netmask 255.255.254.0
{
range 172.16.6.50 172.16.7.200;
option subnet-mask 255.255.254.0;
option broadcast-address 172.16.7.255;
option domain-name-servers 192.168.0.100;
option routers 172.16.6.1;
default-lease-time 7200;
max-lease-time 14400;

infinite-is-reserved on;

host wifi_router_2
{
hardware ethernet dc:ef:09:15:fe:e1;
fixed-address 172.16.6.177;
}

host wifi_ROUTER_1
{
hardware ethernet a0:ab:1b:d8:7f:ce;
fixed-address 172.16.7.40;
}

}
```

Any help is much appreciated.

---

### Post by jeremy31 on 2018-09-26
You do realize that 12.04 is no longer supported?  It went EOL 16 months ago

---

### Post by eby on 2018-09-26
Yup, thats why i mentioned "Not sure if this can be posted here," as the first line.

---

