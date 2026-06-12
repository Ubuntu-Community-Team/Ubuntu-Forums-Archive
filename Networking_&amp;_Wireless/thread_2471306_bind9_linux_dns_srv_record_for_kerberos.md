---
title: "bind9 linux dns srv record for kerberos"
date: 2022-01-26
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2022-01-26
I am receiving this error message: 
```

[3035] 1643135656.25896: Getting initial credentials for ubuntu/admin@mydomain.com
[3035] 1643135656.25898: Sending unauthenticated request
[3035] 1643135656.25899: Sending request (191 bytes) to mydomain.com
[3035] 1643135656.25900: Resolving hostname kdc01.mydomain.com
[3035] 1643135656.25901: Sending initial UDP request to dgram 192.168.1.7:88
[3035] 1643135656.25902: Received answer (158 bytes) from dgram 192.168.1.7:88
[3035] 1643135656.25903: Sending DNS URI query for _kerberos.mydomain.com.
[3035] 1643135656.25904: No URI records found
[3035] 1643135656.25905: Sending DNS SRV query for _kerberos-master._udp.mydomain.com.
[3035] 1643135656.25906: Sending DNS SRV query for _kerberos-master._tcp.mydomain.com.
[3035] 1643135656.25907: No SRV records found
[3035] 1643135656.25908: Response was not from master KDC
[3035] 1643135656.25909: Received error from KDC: -1765328378/Client not found in Kerberos database
[3035] 1643135656.25910: Retrying AS request with master KDC
[3035] 1643135656.25911: Getting initial credentials for ubuntu/admin@mydomain.com
[3035] 1643135656.25913: Sending unauthenticated request
[3035] 1643135656.25914: Sending request (191 bytes) to mydomain.com (master)
[3035] 1643135656.25915: Sending DNS URI query for _kerberos.mydomain.com.
[3035] 1643135656.25916: No URI records found
[3035] 1643135656.25917: Sending DNS SRV query for _kerberos-master._udp.mydomain.com.
[3035] 1643135656.25918: Sending DNS SRV query for _kerberos-master._tcp.mydomain.com.
[3035] 1643135656.25919: No SRV records found
kinit: Client 'ubuntu/admin@mydomain.com' not found in Kerberos database while getting initial credentials
```

My forward-lookup file:
```

;; BIND data file for mydomain.com;$TTL    3h@       IN      SOA     ns1.mydomain.com. admin.mydomain.com. (                          1        ; Serial                          3h       ; Refresh after 3 hours                          1h       ; Retry after 1 hour                          1w       ; Expire after 1 week                          1h )     ; Negative caching TTL of 1 day;@       IN      NS      ns1.mydomain.com.mydomain.com.    IN      A       192.168.1.7ns1                     IN      A       192.168.1.7kdc01.mydomain.com. IN A 192.168.1.7_kerberos._udp.mydomain.com.     IN SRV 1  0 88  kdc01.mydomain.com._kerberos._tcp.mydomain.com.     IN SRV 1  0 88  kdc01.mydomain.com._kerberos._udp.mydomain.com.     IN SRV 10 0 88  kdc02.mydomain.com._kerberos._tcp.mydomain.com.     IN SRV 10 0 88  kdc02.mydomain.com._kerberos-adm._tcp.mydomain.com. IN SRV 1  0 749 kdc01.mydomain.com._kpasswd._udp.mydomain.com.      IN SRV 1  0 464 kdc01.mydomain.com._kerberos-master._udp.mydomain.com               IN SRV 1  0 88  kdc01.mydomain.com._kerberos-master._udp.mydomain.com.               IN SRV 1  0 88  kdc01.mydomain.com._kerberos-master._tcp.mydomain.com               IN SRV 1  0 88  kdc01.mydomain.com._kerberos._udp.mydomain.com.     IN SRV 1  0 88  kdc01.mydomain.com.~    
```


It is a relatively easy setup, for now.  I plan on putting my DNS server somewhere else later on. 

 host -t srv _kerberos-master._udp.mydomain.com. 192.168.1.7:
```

Using domain server:Name: 192.168.1.7Address: 192.168.1.7#53Aliases: _kerberos-master._udp.mydomain.com has SRV record 1 0 88 kdc01.mydomain.com.
```

---

### Post by sniper8752 on 2022-01-29
Can anyone please assist?

---

