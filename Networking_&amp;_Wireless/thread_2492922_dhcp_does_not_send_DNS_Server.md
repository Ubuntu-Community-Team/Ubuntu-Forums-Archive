---
title: "dhcp does not send DNS Server"
date: 2023-11-27
forum: Networking &amp; Wireless
---

### Post by chfloreck on 2023-11-27
Hi

here my dhcpd.conf.

The Clients receive an IP Nummer and the dns server is updated.
However, no dns server is pushed to the clients.
(DNS IPs 192.168.50.40 / 192.168.100.40)

Any ideas?


include "/etc/dhcp/pennys.key";


default-lease-time 600;
max-lease-time 7200;
option domain-name "darkwing.net";



authoritative;
ddns-updates on;
ddns-update-style standard;


zone darkwing.net. {
        primary 192.168.50.40;
        key pennyskey;
}




zone 100.168.192.in-addr.arpa. {
        primary 192.168.50.40;
        key pennyskey;
}




subnet 192.168.100.0 netmask 255.255.255.0
        {
        range 192.168.100.150 192.168.100.200;
        option routers 192.168.100.40;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.100.255;
        option domain-name-servers 192.168.100.40, 192.168.50.40;
        }

---

### Post by Doug S on 2023-11-27
Are your clients requesting DNS stuff?
Here is an example DCHP request from a client on my LAN, caught via tcpdump:

```
doug@s15:~$ [COLOR="#FF0000"]sudo tcpdump -n -tttt -i br0 -vv port 67[/COLOR]
tcpdump: listening on br0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
2023-11-27 13:14:41.755483 IP (tos 0x0, ttl 64, id 23913, offset 0, flags [none], proto UDP (17), length 328)
    192.168.111.30.68 > 192.168.111.1.67: [udp sum ok] BOOTP/DHCP, Request from 10:29:59:2e:06:9d, length 300, xid 0x84fa37d3, Flags [none] (0x0000)
          Client-IP 192.168.111.30
          Client-Ethernet-Address 10:29:59:2e:06:9d
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message (53), length 1: Request
            [COLOR="#FF0000"]Parameter-Request[/COLOR] (55), length 9:
              Subnet-Mask (1), Classless-Static-Route (121), Default-Gateway (3), [COLOR="#FF0000"]Domain-Name-Server[/COLOR] (6)
              Domain-Name (15), Unknown (108), URL (114), Unknown (119)
              Unknown (252)
            MSZ (57), length 2: 1500
            Client-ID (61), length 7: ether 10:29:59:2e:06:9d
            Lease-Time (51), length 4: 7776000
            Hostname (12), length 6: "iPad-4"
2023-11-27 13:14:41.762979 IP (tos 0x0, ttl 64, id 51709, offset 0, flags [DF], proto UDP (17), length 328)
    192.168.111.1.67 > 192.168.111.30.68: [bad udp cksum 0x60b6 -> 0x1e83!] BOOTP/DHCP, Reply, length 300, xid 0x84fa37d3, Flags [none] (0x0000)
          Client-IP 192.168.111.30
          Your-IP 192.168.111.30
          Client-Ethernet-Address 10:29:59:2e:06:9d
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message (53), length 1: ACK
            Server-ID (54), length 4: 192.168.111.1
            Lease-Time (51), length 4: 93000
            Subnet-Mask (1), length 4: 255.255.255.0
            Default-Gateway (3), length 4: 192.168.111.1
            [COLOR="#FF0000"]Domain-Name-Server (6), length 4: 192.168.111.1[/COLOR]
            Domain-Name (15), length 12: "smythies.com"
```

---

### Post by chfloreck on 2023-11-27
Thanks for the  command it was new for me.
The statement hangs...
The firewall is not running.
The strange thing is that kea delivers the dns server ..

---

### Post by chfloreck on 2023-11-27
After some time, this is reported.
The IP Numbers for DNS and Gateway are correct.


cpdump: listening on pub, link-type EN10MB (Ethernet), capture size 262144 bytes
2023-11-27 23:11:35.850321 IP (tos 0x0, ttl 64, id 15796, offset 0, flags [DF], proto UDP (17), length 328)
    192.168.100.162.bootpc > 192.168.100.40.bootps: [bad udp cksum 0x4b61 -> 0xaaa6!] BOOTP/DHCP, Request from 08:00:27:c5:af:bb, length 300, xid 0xa
          Client-IP 192.168.100.162
          Client-Ethernet-Address 08:00:27:c5:af:bb
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Request
            Hostname Option 12, length 9: "client100"
            Parameter-Request Option 55, length 19:
              Subnet-Mask, BR, Time-Zone, Classless-Static-Route
              Domain-Name, Domain-Name-Server, Hostname, YD
              YS, NTP, MTU, Option 119
              Default-Gateway, Classless-Static-Route, Classless-Static-Route-Microsoft, Static-Route
              Option 252, NTP, RP
2023-11-27 23:11:35.854728 IP (tos 0x0, ttl 64, id 34520, offset 0, flags [DF], proto UDP (17), length 328)
    192.168.100.40.bootps > 192.168.100.162.bootpc: [udp sum ok] BOOTP/DHCP, Reply, length 300, xid 0xaa6c3f37, Flags [none] (0x0000)
          Client-IP 192.168.100.162
          Your-IP 192.168.100.162
          Server-IP 192.168.100.40
          Client-Ethernet-Address 08:00:27:c5:af:bb
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: ACK
            Server-ID Option 54, length 4: 192.168.100.40
            Lease-Time Option 51, length 4: 600
            Subnet-Mask Option 1, length 4: 255.255.255.0
            BR Option 28, length 4: 192.168.100.255
            Domain-Name Option 15, length 12: "darkwing.net"
**            Domain-Name-Server Option 6, length 8: 192.168.100.40,192.168.50.40**
**            Default-Gateway Option 3, length 4: 192.168.100.40**

---

### Post by Doug S on 2023-11-27
I forgot to mention that it might be awhile before any of your clients needed to renew their DHCP license.
So, we can conclude that, at least for the client that you captured, that the DNS servers are both being asked for and supplied.

EDIT: Oh, your lease time is only 10 minutes, so you should see activity fairly quickly. My lease time is over a day.

---

### Post by chfloreck on 2023-11-28
Hi

I did the renews.
I setup an client from scratch and everything went fine.
Seems the was something "broken". 
Will test i again today.
Thank's for the help.

Christian

---

