---
title: "bind9 not forwarding .net domains"
date: 2024-08-07
forum: Networking &amp; Wireless
---

### Post by tatodc2 on 2024-08-07
I have set a test environment for my training at home consisting of a MS domain controller (PDC) with a DNS, one network server (NWSVR) running Ubuntu with bind9, nginx, webmin and chrony and a third server running Ubuntu and Icinga. The environment is set up so the Icinga server queries the NWSVR and this queries the MS PDC. I named my domain tdchdev.net since this is my home development (hdev) network (.net). I know there are more easy implementations but this is what is going to be replicated at a data center where we provide services to some customers.

When I query for a server at the tdchdev.net domain, I got no answer and it looks like the query tries to go to the root DNS servers:
[FONT=&quot]
; <<>> DiG 9.18.28-0ubuntu0.24.04.1-Ubuntu <<>> pdc.tdchdev.net[/FONT]
[FONT=&quot];; global options: +cmd[/FONT]
[FONT=&quot];; Got answer:[/FONT]
[FONT=&quot];; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 40744[/FONT]
[FONT=&quot];; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot];; OPT PSEUDOSECTION:[/FONT]
[FONT=&quot]; EDNS: version: 0, flags:; udp: 65494[/FONT]
[FONT=&quot];; QUESTION SECTION:[/FONT]
[FONT=&quot];pdc.tdchdev.net.               IN      A[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot];; AUTHORITY SECTION:[/FONT]
[FONT=&quot]net.                    900     IN      SOA     a.gtld-servers.net. nstld.verisign-grs.com. 1723051005 1800 900 604800 86400[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot];; Query time: 85 msec[/FONT]
[FONT=&quot];; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)[/FONT]
[FONT=&quot];; WHEN: Wed Aug 07 17:17:15 UTC 2024[/FONT]
[FONT=&quot];; MSG SIZE  rcvd: 117[/FONT]


because of that I created another domain at the MS PDC and made the same query from the Icinga server:

[FONT=&quot]; <<>> DiG 9.18.28-0ubuntu0.24.04.1-Ubuntu <<>> pdc.skate.biz[/FONT]
[FONT=&quot];; global options: +cmd[/FONT]
[FONT=&quot];; Got answer:[/FONT]
[FONT=&quot];; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48257[/FONT]
[FONT=&quot];; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot];; OPT PSEUDOSECTION:[/FONT]
[FONT=&quot]; EDNS: version: 0, flags:; udp: 65494[/FONT]
[FONT=&quot];; QUESTION SECTION:[/FONT]
[FONT=&quot];pdc.skate.biz.                 IN      A[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot];; ANSWER SECTION:[/FONT]
[FONT=&quot]pdc.skate.biz.          300     IN      A       217.26.63.20[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot];; Query time: 436 msec[/FONT]
[FONT=&quot];; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)[/FONT]
[FONT=&quot];; WHEN: Wed Aug 07 17:18:38 UTC 2024[/FONT]
[FONT=&quot];; MSG SIZE  rcvd: 58[/FONT]


the config file at the NWSVR reads like this:

[FONT=&quot]zone "tdchdev.net" {[/FONT]
[FONT=&quot]        type forward;[/FONT]
[FONT=&quot]        forwarders {[/FONT]
[FONT=&quot]                192.168.255.220;[/FONT]
[FONT=&quot]                };[/FONT]
[FONT=&quot]        };[/FONT]
[FONT=&quot]zone "skate.biz" {[/FONT]
[FONT=&quot]        type forward;[/FONT]
[FONT=&quot]        forwarders {[/FONT]
[FONT=&quot]                192.168.255.220;[/FONT]
[FONT=&quot]                };[/FONT]
[FONT=&quot]        };[/FONT]




it looks like bind9 is not reading the .net forward directive. Anyone that can help me fix this?

---

