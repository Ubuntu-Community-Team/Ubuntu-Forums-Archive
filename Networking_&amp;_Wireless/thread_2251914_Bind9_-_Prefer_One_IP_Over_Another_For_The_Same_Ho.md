---
title: "Bind9 - Prefer One IP Over Another For The Same Host"
date: 2014-11-07
forum: Networking &amp; Wireless
---

### Post by TheHackMan on 2014-11-07
I have a host setup with multiple interfaces and each interface has its own IP address on the same subnet. One is acting as a backup link and the other is the main link. I want to know if there is a way to force Bind to prefer one IP over another. I have tried searching on Google and I may just be typing in the wrong search strings but the only mention I found was creating some form of sortlist but no mention of where to create it or what file to append it to. The main IP address ends in .177 while the backup ends in .179 and whenever I resolve or ping the domain from other computers it always resolves to the .179 address.

---

### Post by Doug S on 2014-11-07
The sortlist would go in the /etc/bind/named.conf.options file (or so I think). It is a little odd to use it this way, but here is an example I tested on my server.

First some entries in my forward zonefile:```
doug@doug-64:~/config/bind$ [COLOR=#ff0000]cat /etc/bind/db.smythies.com[/COLOR]
;
; BIND data file for smythies.com
;
$TTL    604800
@       IN      SOA     smythies.com. doug.smythies.com. (
                        2014110703      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
                IN      A       192.168.111.1
;
@               IN      NS      ns1.smythies.com.
ns1             IN      A       192.168.111.1
www             IN      A       192.168.111.1

DOUG-64         IN      CNAME   ns1
mail            IN      CNAME   ns1
Wireless-R      IN      A       192.168.111.57
doug-xps        IN      A       192.168.111.100
... deleted a bunch of stuff...
serv-tt         IN      A       192.168.111.214
[COLOR=#ff0000]test            IN      A       192.168.111.223
test            IN      A       192.168.111.222[/COLOR]
```Now, regardless of the order of the above entries, "test" always resolved to 192.168.111.223, until I added this to my /etc/bind/named.conf.options file:```
doug@doug-64:~/config/bind$ [COLOR=#ff0000]cat /etc/bind/named.conf.options[/COLOR]
options {
        directory "/var/cache/bind";

        recursion yes;
        allow-recursion {any;};
        allow-query {any;}; // this is needed to override the default
        allow-transfer {"none"; }; // transfer will be allowed per zone below.

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

//      forwarders {
//              75.153.176.9;
//              75.153.176.1;
//      };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { none; };

[COLOR=#ff0000]        sortlist {
                {// preference block start
                        0.0.0.0/0;  // For any client IP
                        {192.168.111.222/32;   // return this response as 1st preference
                        };
                }; // end first block (only block, in this case)
        }; // end sortlist[/COLOR]
};
```Then "test" resolved to 192.168.111.222

---

### Post by TheHackMan on 2014-11-08
Thank you very much, this solution appears to be exactly what I needed. Since the server is running IPv4 and IPv6 addresses I assumed I needed a block for each one in the sortlist and it seems to be working. Since I have two DNS servers, the primary and secondary I added the list to both. If that is incorrect please let me know but I assume that is what's needed to keep the behavior during a failover scenario. 

My only problem now is the damn server keeps trying to make the .179 address which is a 1gig link the default router/interface instead of the .177 interface which is a dual 10gig fiber port-channel link but I'm pretty sure I know just what needs to be done on the networking interfaces configuration to force one to come up as default in the routing table.

---

