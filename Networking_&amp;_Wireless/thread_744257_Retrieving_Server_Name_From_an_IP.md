---
title: "Retrieving Server Name From an IP"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by underdog512 on 2008-04-03
You can visit [www.dnsstuff.com](www.dnsstuff.com)  and plug the IP address into the "Whois Lookup" field. then click the whois button to get the DNS info about that ip address.  

There is a lookup tool in System -> Administration -> Network Tools,  but dnsstuff.com seems to work better.  

Hope this helps.

---

### Post by dstew on 2008-04-03
You can go to the ARIN site and use [their whois seach.]("http://www.arin.net/whois/") If the IP is registered to another NIC (like in Europe or Asia) it will tell you. There are links to search the other NICs if you need to.

---

### Post by Eiríkr on 2008-04-03
Or, from the CLI, you could use the [font=courier]dig[/font] utility, with the -x option for reverse lookup (using the IP address instead of the fully qualified domain name), like so:
```
user@ubuntu:~$ dig -x 208.77.188.166

; <<>> DiG 9.4.1-P1 <<>> -x 208.77.188.166
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24179
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 4

;; QUESTION SECTION:
;166.188.77.208.in-addr.arpa.   IN   PTR

;; ANSWER SECTION:
166.188.77.208.in-addr.arpa. 21600 IN   PTR     www.example.com.

;; AUTHORITY SECTION:
188.77.208.in-addr.arpa. 11357  IN   NS a.iana-servers.net.
188.77.208.in-addr.arpa. 11357  IN   NS b.iana-servers.org.
188.77.208.in-addr.arpa. 11357  IN   NS c.iana-servers.net.

;; ADDITIONAL SECTION:
b.iana-servers.org.     19352   IN   A  193.0.0.236
c.iana-servers.net.     149738  IN   A  139.91.1.10
c.iana-servers.net.     15493   IN   AAAA       2001:648:2c30::1:10
a.iana-servers.net.     149738  IN   A  192.0.34.43

;; Query time: 28 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Thu Apr  3 10:56:35 2008
;; MSG SIZE  rcvd: 230

user@ubuntu:~$
```

Cheers,

Eiríkr

---

### Post by prshah on 2008-04-03
> **Auston said:**
> 
Basically, if I had the IP address "208.77.188.166" and wanted to know that it belonged to "www.example.com", 

```
Thu Apr 03 23:43:15 ~:$ dig -x 208.77.188.166

; <<>> DiG 9.4.1-P1 <<>> -x 208.77.188.166
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19354
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 4

;; QUESTION SECTION:
;166.188.77.208.in-addr.arpa.   IN      PTR

;; ANSWER SECTION:
166.188.77.208.in-addr.arpa. 21600 IN   PTR     www.example.com.

;; AUTHORITY SECTION:
188.77.208.in-addr.arpa. 21600  IN      NS      b.iana-servers.org.
188.77.208.in-addr.arpa. 21600  IN      NS      c.iana-servers.net.
188.77.208.in-addr.arpa. 21600  IN      NS      a.iana-servers.net.

;; ADDITIONAL SECTION:
a.iana-servers.net.     132180  IN      A       192.0.34.43
b.iana-servers.org.     13175   IN      A       193.0.0.236
c.iana-servers.net.     132178  IN      A       139.91.1.10
c.iana-servers.net.     2586    IN      AAAA    2001:648:2c30::1:10

;; Query time: 2372 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Thu Apr  3 23:44:39 2008
;; MSG SIZE  rcvd: 230

```

If any information here seems privileged to somebody, feel free to tell me to remove it.

---

### Post by koenn on 2008-04-03
or : 
```
k@nix:~$ host 208.77.188.166
166.188.77.208.in-addr.arpa domain name pointer www.example.com.
```

windows ping has an /a option for name resolution, IIRC. unix ping doesn't.

---

