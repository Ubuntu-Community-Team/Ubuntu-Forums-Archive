---
title: "Problem with my dhcp server"
date: 2016-01-20
forum: Networking &amp; Wireless
---

### Post by hal90002 on 2016-01-20
I'm trying to use my computer with Ubuntu 15.03 as dhcp server instead of the dhcp in my linksys router. I've followed the guide at 
[http://www.unixmen.com/how-to-install-dhcp-server-in-centos-and-ubuntu/](http://www.unixmen.com/how-to-install-dhcp-server-in-centos-and-ubuntu/)

I've changed my router's ip to 10.0.0.1 and the subnet mask is 255.255.255.0

The isc-dhcp-server file looks like this:

[SIZE=1][B]```
# Defaults for isc-dhcp-server initscript
# sourced by /etc/init.d/isc-dhcp-server
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# Path to dhcpd's config file (default: /etc/dhcp/dhcpd.conf).
#DHCPD_CONF=/etc/dhcp/dhcpd.conf

# Path to dhcpd's PID file (default: /var/run/dhcpd.pid).
#DHCPD_PID=/var/run/dhcpd.pid

# Additional options to start dhcpd with.
#    Don't use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
#OPTIONS=""

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="enp3s0"
```

[/B][SIZE=2]and the dhcpd.conf:[/SIZE]

```
[B]default-lease-time:600;
max-lease-time:7200;
option subnet-mask 255.255.255.0;
option broadcast-address 10.0.0.255;
option routers 10.0.0.1;
option domain-name-servers 8.8.4.4;
option domain-name "datacom.example.com";

subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.7 10.0.0.8;
}
[/B]
```

[SIZE=2] I then start the server and turn off the dhcp server in my router but then the computer it doesn't get any connection at all, Where do I start troubleshoot? How can I check if the server is running at all?[/SIZE][/SIZE]

---

### Post by newbie-user on 2016-01-21
To check if the dhcp server is running:
```
systemctl status isc-dhcp-server.service
```

Check /var/log/syslog to see if the dhcp server is doing anything like responding to dhcp requests

---

