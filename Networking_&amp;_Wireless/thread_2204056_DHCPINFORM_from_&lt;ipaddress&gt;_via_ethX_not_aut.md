---
title: "DHCPINFORM from &lt;ipaddress&gt; via ethX: not authoritative for subnet"
date: 2014-02-06
forum: Networking &amp; Wireless
---

### Post by markmckee6011 on 2014-02-06
isc-dhcpd-V3.1.3

I keep seeing this in the log file:
DHCPINFORM from <ipaddress> via ethX: not authoritative for subnet

I have tried adding authorative to the top of the dhcpd.conf file and also within the subnet declaration.

subnet 192.168.1.0 netmask 255.255.255.0 {
        authorative;
        range 192.168.1.30 192.168.1.55;
        option routers 192.168.1.1;
        zone 1.168.192.in-addr.arpa. {
                primary 192.168.1.105;
                key "<keyname>";
        }
        zone <zone name> {
                primary 192.168.1.x;
                key "<keyname>";
        }
}

---

