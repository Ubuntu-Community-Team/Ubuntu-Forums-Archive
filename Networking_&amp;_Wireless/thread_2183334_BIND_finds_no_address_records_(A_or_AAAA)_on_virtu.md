---
title: "BIND finds no address records (A or AAAA) on virtual server machine"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by shadowClint on 2013-10-24
Dear ubuntuforums,

I'm rather new to web hosting, and as part of a university assignment, I decided to host a ubuntu 13.04 server on a virtual machine that is hosted inside Windows 7 through VMWare. I wanted to install a DNS service using BIND9, so I could access my apache server running on ubuntu from navigating to my domain in a browser running on the host OS. Reaching my apache website from Windows works perfectly, but I can't configure BIND9 correctly.

I tried using the following forward DNS file, after configuring BIND to use the Google DNS servers are forwarders (I've seen many examples do the same):
```

$TTL 604800
@    IN   SOA   panda.devajonmiert.com. root.devajonmiert.com (
                                3
                                604800
                                86400
                                2419200
                                604800 )

@    IN   NS     panda.devajonmiert.com
@    IN   A       127.0.0.1
@    IN   AAAA  ::1

devajonmiert.com.    IN    NS    panda.devajonmiert.com.
devajonmiert.com.    IN    A      192.168.147.128

```

where panda is my computer's hostname, and "devajonmiert.com" is the name I've set up in my zone file.

When restarting the service (or running "named-checkzone devajonmiert.com /etc/bind/db.devajonmiert.com"), I get the following error message when this file is interpreted:
```
zone devajonmiert.com/IN: NS "panda.devajonmiert.com" has no address records (A or AAAA)
```

What am I doing wrong? Keep in mind that this is my first time trying to set up a DNS server.

Thank you in advance.

---

### Post by SeijiSensei on 2013-10-24
You don't have an A record for panda, just one for the unqualified domain name.  Add this record

```
panda    IN   A   192.168.147.128
```

assuming that is panda's external IP address.  You should now be able to connect to that address using either "panda.devajonmiert.com" or just "devajonmiert.com".

---

### Post by shadowClint on 2013-10-27
Thank you for the reply, adding that record solved this error message. According to named-checkzone and /var/log/syslog, all zones load correctly.

However, I am still unable to reach my webserver. I tried using the "dig" command in two ways:

Typing "dig @192.168.147.128 devajonmiert.com", I got answers from the server:
```


; <<>> DiG 9.9.2-P1 <<>> @192.168.147.128 devajonmiert.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 9422
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 1, ADDITIONAL: 2


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;devajonmiert.com.        IN    A


;; ANSWER SECTION:
devajonmiert.com.    604800    IN    A    192.168.147.128
devajonmiert.com.    604800    IN    A    127.0.0.1


;; AUTHORITY SECTION:
devajonmiert.com.    604800    IN    NS    panda.devajonmiert.com.


;; ADDITIONAL SECTION:
panda.devajonmiert.com.    604800    IN    A    192.168.147.128


;; Query time: 0 msec
;; SERVER: 192.168.147.128#53(192.168.147.128)
;; WHEN: Sun Oct 27 12:02:55 2013
;; MSG SIZE  rcvd: 113

```

It receives answers from the server as it should in my understanding. However, if I just type "dig devajonmiert.com" I get:
```


; <<>> DiG 9.9.2-P1 <<>> devajonmiert.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 43167
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; MBZ: 0005 , udp: 4096
;; QUESTION SECTION:
;devajonmiert.com.        IN    A


;; AUTHORITY SECTION:
com.            5    IN    SOA    a.gtld-servers.net. nstld.verisign-grs.com. 1382876380 1800 900 604800 86400


;; Query time: 23 msec
;; SERVER: 192.168.147.2#53(192.168.147.2)
;; WHEN: Sun Oct 27 13:19:57 2013
;; MSG SIZE  rcvd: 118



```

I get no answers. I suspect that this has to do something with my inability to reach the server using my domain name. I checked the zone files, and they have rw,r,r permissions (I have read that this could be a potential problem) and checking netstat -an for port 53 gives me the following results:

```
tcp        0      0 192.168.147.128:53      0.0.0.0:*               LISTEN     tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 192.168.147.128:445     192.168.147.1:53974     ESTABLISHED
tcp6       0      0 :::53                   :::*                    LISTEN     
udp        0      0 0.0.0.0:53              0.0.0.0:*                          
udp        0      0 192.168.147.128:53      0.0.0.0:*                          
udp        0      0 127.0.0.1:53            0.0.0.0:*                          
udp6       0      0 :::53                   :::*                               



```

What could be the problem?

---

### Post by SeijiSensei on 2013-10-27
> ```
;; AUTHORITY SECTION:
com.            5    IN    SOA    a.gtld-servers.net. nstld.verisign-grs.com. 1382876380 1800 900 604800 86400
```

Your computer is looking to the root name servers for the names.  You have to tell it to use your local server.  If you are connecting with DHCP, you need to add the DNS server address to the configuration in NetworkManager.  If you are using a static address, add the entry 

```
dns-nameservers 192.168.147.128
```

to the appropriate stanza in /etc/network/interfaces. These problems arise from some [changes made to how Ubuntu handles DNS resolution on the client side]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/").  It works well for people with mainstream needs but requires massaging if you start doing anything complex.

I'd also remove the entry for 127.0.0.1 associated with your domain name in the DNS zone file.  Use "localhost" as the hostname instead:
```
localhost     IN     A     127.0.0.1
```

---

### Post by shadowClint on 2013-11-08
Thank you very much for your detailed replies. I made everything work.

After making this modification, my only problem was that I could not connect to the internet from the server that was hosting bind, even if I added multiple DNS IP addresses, presumably because I've set my only ethernet device to use a static IP.

I worked around it by adding another network adapter to my virtual machine set it to use DHCP, and use Google's DNS servers to resolve domains.

---

