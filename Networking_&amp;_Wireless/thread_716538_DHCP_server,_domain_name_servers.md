---
title: "DHCP server, domain name servers"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by ster1988 on 2008-03-06
I recently put ubuntu on my setup the reason is that i know linux is supposed to be better at setting up servers. I have never set up a DHCP server and i am completely lost and kind of confused. My current set up is i have a modem which i plugged into 1 out of 2 ethernet ports on my motherboard. Then i have a second ethernet cord running from the other port to a dlink 5 port switch. from the switch i have 1 xp home laptop, 1 360, and 1 net gear wireless router. My question is how do i know what i am supposed to choose for the domain name serve. I have installed dhcp3 correctly and i even tried configuring the server through GDHCPD. So according to what i have written i am wonder if anyone has any ideas on how to trouble shoot this. When i look in the lease files it did not lease any IP's. I think the problem is either in the way i have it set up physically or i dont know what domain name server to choose.

any and all help is appreciated

thanks in advanced

---

### Post by SpaceTeddy on 2008-03-06
i have never used any frontend to configure the dhcp-server - always done this in the conf files directly... 

for the dhcp server, can you please supply the output of the following commands
```
cat /etc/dhcp3/dhcpd.conf 
cat /etc/default/dhcp3-server
```

the first if your dhcp configuration file, the second is the network configuration for the server.

as for the DNS servers (domain name server), they are used to convert hostnames (like ubuntuforums.org) into ip-addresses (91.189.94.186). Your isp will usually supply you with at least two different ones. once you are connected to the internet, they will be written to the file /etc/resolv.conf.

a DNS server is not required for a computer to acquire a lease from a dhcp server.

---

### Post by ster1988 on 2008-03-06
~$ cat /etc/dhcp3/dhcpd.conf 
ddns-update-style none;
ddns-updates off;
deny client-updates;
one-lease-per-client false;
allow bootp;
option T150 code 150 = string;



subnet 192.168.1.0 netmask 255.255.255.0
{
        range 192.168.1.100 192.168.1.200;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.1.255;
        option domain-name-servers 127.0.0.1;
        option routers 192.168.1.1;

 }
sterling@sterling-desktop:~$ cat /etc/dhcp3/dhcpd.conf 
ddns-update-style none;
ddns-updates off;
deny client-updates;
one-lease-per-client false;
allow bootp;
option T150 code 150 = string;




subnet 192.168.0.3 netmask 255.255.255.255 {
    interface eth0;
    default-lease-time 6000;
    max-lease-time 7200;
    option subnet-mask 255.255.255.255;
    option broadcast-address 192.168.0.255;
    option domain-name-servers  24.205.192.61, 66.215.64.14;
    option time-offset -3600;
}
:~$ cat /etc/default/dhcp3-server
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES=""

---

### Post by ster1988 on 2008-03-06
> **ster1988 said:**
> 
sterling@sterling-desktop:~$ cat /etc/dhcp3/dhcpd.conf 
ddns-update-style none;
ddns-updates off;
deny client-updates;
one-lease-per-client false;
allow bootp;
option T150 code 150 = string;




subnet 192.168.0.3 netmask 255.255.255.255 {
    interface eth0;
    default-lease-time 6000;
    max-lease-time 7200;
    option subnet-mask 255.255.255.255;
    option broadcast-address 192.168.0.255;
    option domain-name-servers  24.205.192.61, 66.215.64.14;
    option time-offset -3600;
}
:~$ cat /etc/default/dhcp3-server
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES=""
this is right conf that was some crap i had in there

---

### Post by SpaceTeddy on 2008-03-06
> **ster1988 said:**
> 
INTERFACES=""

the dhcp server is not bound or allowed to use any network interfaces - hence it will not work. But the network interface (eth0) in there. This is not so much required by the dhcp-server itself, but more by the script that start/stops it.
after that, start the dhcp server with
```
sudo /etc/init.d/dhcp3-server  start
```

then it should work. All messages get logged to the standard syslog - so i suggest you open a second console and have this command running while testing it.
```
tail -f /var/log/syslog
```

you should see something like this there
```
 Internet Systems Consortium DHCP Server V3.0.4
Mar  6 20:14:40 home dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar  6 20:14:40 home dhcpd: All rights reserved.
Mar  6 20:14:40 home dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Mar  6 20:14:40 home dhcpd: Wrote 0 deleted host decls to leases file.
Mar  6 20:14:40 home dhcpd: Wrote 0 new dynamic host decls to leases file.
Mar  6 20:14:40 home dhcpd: Wrote 37 leases to leases file.

```

if there are no errors, you are all set. then try to obtain a lease with another computer... this should show in the log aswell 

hope it works

---

### Post by ster1988 on 2008-03-06
$ tail -f /var/log/syslog
Mar  6 11:39:21 sterling-desktop dhcpd: All rights reserved.
Mar  6 11:39:21 sterling-desktop dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar  6 11:39:21 sterling-desktop dhcpd: Wrote 4 leases to leases file.
Mar  6 11:39:21 sterling-desktop dhcpd: Listening on LPF/eth0/00:1e:8c:64:4a:48/192.168.0/24
Mar  6 11:39:21 sterling-desktop dhcpd: Sending on   LPF/eth0/00:1e:8c:64:4a:48/192.168.0/24
Mar  6 11:39:21 sterling-desktop dhcpd: Sending on   Socket/fallback/fallback-net
Mar  6 11:39:38 sterling-desktop dhcpd: DHCPDISCOVER from 00:14:a5:8c:3b:f8 (STERLINGLAPTOP) via eth0
Mar  6 11:39:39 sterling-desktop dhcpd: DHCPOFFER on 192.168.0.37 to 00:14:a5:8c:3b:f8 (STERLINGLAPTOP) via eth0
Mar  6 11:39:39 sterling-desktop dhcpd: DHCPREQUEST for 192.168.0.37 (192.168.1.2) from 00:14:a5:8c:3b:f8 (STERLINGLAPTOP) via eth0
Mar  6 11:39:39 sterling-desktop dhcpd: DHCPACK on 192.168.0.37 to 00:14:a5:8c:3b:f8 (STERLINGLAPTOP) via eth0

ok if you look at the log it sent an IP to my laptop, however that was sent via wifi not assigned by the switch. I have a router on the network as well as the switch. Right now the wifi was assigned an IP in the range i set in the .conf file, however the internet itself is not working. any ideas?

---

### Post by rickyjones on 2008-03-06
Let me begin by saying that I am not familiar with the configuration of a linux DHCP server.

I am here to try to get an idea of what you want and to discern possible solutions based on the given information.

1) You have two NICs in your "server". Internet goes into one, LAN into the second.
2) Attached to the "LAN" side is a 360, a laptop, and a netgear router.
3) Internet sharing is not working with this configuration.

I recommend you use the netgear router for DHCP/firewalling/internet sharing instead of your computer. It will accomplish the feat with little to no configuration.

If you wish to continue using your server then you will need to ensure that it is configured for NAT. I do not know how to do this but it must be done to share internet from one NIC to the other.

I hope this helps!

-Richard

---

### Post by SpaceTeddy on 2008-03-06
you do not send a defaut gateway with your dhcp-configuration (option routers). you need to push your default gateway to the clients. i don't know what that is set to for you, but you need to insert something like 

```
option routers 192.168.0.1;
```

to push the default gateway to the client. Best to insert that in the subnet configuration

---

### Post by ster1988 on 2008-03-07
the problem was in my NIC cards i did not have them configured properly, i finally did that and everything works great thanks everyone.

---

