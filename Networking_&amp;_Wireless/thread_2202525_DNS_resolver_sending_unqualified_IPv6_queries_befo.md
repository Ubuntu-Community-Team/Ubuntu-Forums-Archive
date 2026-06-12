---
title: "DNS resolver sending unqualified IPv6 queries before attempting IPv4 query"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by mark-hall on 2014-01-29
In Ubuntu 12.04 I am seeing issues with the way the resolver performs DNS lookups for unqualified names. 

The resolver will do a complete search for an AAAA record before it attempts to locate an A record for any given name.  My DNS servers do not contain AAAA records.  Therefore, they will respond to AAAA queries for known host names with a NOERROR response.  When the resolver receives an authoritative response (NOERROR) from the DNS server, it continues through the search list querying the remaining domains, and then finally sending an unqualified query which ends up being forwarded to the root name servers.  Only after this process has completed, will the resolver query for an A record, which is resolved immediately.  

This is causing a number of issues.
1. There are a lot of AAAA queries being sent that are completely unnecessary.  A response was received.  
2. I am sending a large number queries to the root name servers for an AAAA records.
3. All of this back and forth on the AAAA queries delays the resolution of the address to the available A records.

Hopefully someone can help me answer 2 questions
1. Why does the resolver continue to attempt resolution for a name/record after it received a valid response(NOERRROR)?
2. Why does the resolver send out unqualified queries?

This is a capture of the DNS traffic coming from the host.  The query for the unqualified name retries because i have intentionally blocked those queries from going to the root nameservers.

root@test-host:~# tcpdump -vv -s 0 -l -n port 53
tcpdump: listening on bond0, link-type EN10MB (Ethernet), capture size 65535 bytes
09:43:34.236454 IP (tos 0x0, ttl 64, id 6318, offset 0, flags [DF], proto UDP (17), length 80)
    10.8.225.108.52171 > 10.8.224.2.53: [bad udp cksum 0xd5cc -> 0xec53!] 49591+ AAAA? test-host.SUB-DOMAIN.DOMAIN.com. (52)
09:43:34.236615 IP (tos 0x0, ttl 64, id 31157, offset 0, flags [none], proto UDP (17), length 130)
    10.8.224.2.53 > 10.8.225.108.52171: [udp sum ok] 49591* q: AAAA? test-host.SUB-DOMAIN.DOMAIN.com. 0/1/0 ns: SUB-DOMAIN.DOMAIN.com. SOA ns1.DOMAIN.com. admin.domain.com. 85635 10800 3600 604800 86400 (102)
09:43:34.236694 IP (tos 0x0, ttl 64, id 6318, offset 0, flags [DF], proto UDP (17), length 58)
    10.8.225.108.60927 > 10.8.224.2.53: [bad udp cksum 0xd5b6 -> 0xa3f9!] 6003+ AAAA? test-host. (30)
09:43:39.241730 IP (tos 0x0, ttl 64, id 7569, offset 0, flags [DF], proto UDP (17), length 58)
    10.8.225.108.44310 > 10.8.224.3.53: [bad udp cksum 0xd5b7 -> 0xe4e1!] 6003+ AAAA? test-host. (30)
09:43:44.243102 IP (tos 0x0, ttl 64, id 6319, offset 0, flags [DF], proto UDP (17), length 58)
    10.8.225.108.60927 > 10.8.224.2.53: [bad udp cksum 0xd5b6 -> 0xa3f9!] 6003+ AAAA? test-host. (30)
09:43:49.248143 IP (tos 0x0, ttl 64, id 7570, offset 0, flags [DF], proto UDP (17), length 58)
    10.8.225.108.44310 > 10.8.224.3.53: [bad udp cksum 0xd5b7 -> 0xe4e1!] 6003+ AAAA? test-host. (30)
09:43:54.253215 IP (tos 0x0, ttl 64, id 11322, offset 0, flags [DF], proto UDP (17), length 80)
    10.8.225.108.47319 > 10.8.224.2.53: [bad udp cksum 0xd5cc -> 0x532f!] 28139+ A? test-host.SUB-DOMAIN.DOMAIN.com. (52)
09:43:54.253375 IP (tos 0x0, ttl 64, id 31610, offset 0, flags [none], proto UDP (17), length 164)
    10.8.224.2.53 > 10.8.225.108.47319: [udp sum ok] 28139* q: A? test-host.SUB-DOMAIN.DOMAIN.com. 1/2/2 test-host.SUB-DOMAIN.DOMAIN.com. A 10.8.225.108 ns: SUB-DOMAIN.DOMAIN.com. NS ns2.SUB-DOMAIN.DOMAIN.com., SUB-DOMAIN.DOMAIN.com. NS ns1.SUB-DOMAIN.DOMAIN.com. ar: ns1.SUB-DOMAIN.DOMAIN.com. A 10.8.224.2, ns2.SUB-DOMAIN.DOMAIN.com. A 10.8.224.3 (136)
09:44:04.237933 IP (tos 0x0, ttl 64, id 31750, offset 0, flags [none], proto UDP (17), length 58)
    10.8.224.2.53 > 10.8.225.108.60927: [udp sum ok] 6003 ServFail q: AAAA? test-host. 0/0/0 (30)
09:44:09.243124 IP (tos 0x0, ttl 64, id 60970, offset 0, flags [none], proto UDP (17), length 58)
    10.8.224.3.53 > 10.8.225.108.44310: [udp sum ok] 6003 ServFail q: AAAA? test-host. 0/0/0 (30)

---

