---
title: "Determine length of DNS Cache"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by jknotzke on 2008-03-13
Hi,

  Is there a way using dig or some other dns tool to determine how long a given DNS server will cache an entry for ?

  I am trying to figure out when blackberry.net's DNS server will go back to the authoritative server to refresh its cache.

  Thanks
  
   J

---

### Post by netztier on 2008-03-13
> **jknotzke said:**
> Hi,

  Is there a way using dig or some other dns tool to determine how long a given DNS server will cache an entry for ?


That's determined by the original DNS server, not the caching one. Each DNS entry (and thus reply) has a TTL value stored with it. 

Using dig, you can see the TTL:


```
marc@cube:~$ dig @195.186.4.111 a www.blackberry.net

; <<>> DiG 9.4.1-P1 <<>> @195.186.4.111 a www.blackberry.net
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11770
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.blackberry.net.            IN      A

;; ANSWER SECTION:
www.blackberry.net.     **[COLOR="Red"]590[/COLOR]**     IN      A       216.9.245.101

;; Query time: 13 msec
;; SERVER: 195.186.4.111#53(195.186.4.111)
;; WHEN: Thu Mar 13 20:37:32 2008
;; MSG SIZE  rcvd: 52
```

A properly configured DNS will remove the entry from it's cache once the TTL has expired.

regards

Marc

---

### Post by jknotzke on 2008-03-13
Thanks for the reply.

It's a bit more complicated then what I originally outlayed. ;)

  My host was hosted by Yahoo and I have recently switched to another provider.
 
   Yahoo's DNS is yns1.yahoo.com. My host is shampoo.ca.

   Blackberry.net comes into play because I need to configure my blackberry to handle my mail. But BIS, which is RIM's server software that does this for me, is still pointing to Yahoo nearly 24hrs later.

   Looking at Yahoo's TTL on my MX records they appear to expire in some 45hrs ! Yet most DNS servers I query, including Yahoo have already swapped to the new domain (Google).

   Any ideas ?

   J

---

### Post by netztier on 2008-03-14
> **jknotzke said:**
> 
my MX records they appear to expire in some 45hrs ! Yet most DNS servers I query, including Yahoo have already swapped to the new domain (Google).


Seems like something's changed; when i ask yns1.yahoo.com about the MX records for shampoo.ca, I get this:

```

marc@blaze:~$ dig @yns1.yahoo.com. mx shampoo.ca

; <<>> DiG 9.3.4 <<>> @yns1.yahoo.com. mx shampoo.ca
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5670
;; flags: qr aa rd; QUERY: 1, ANSWER: 6, AUTHORITY: 4, ADDITIONAL: 9

;; QUESTION SECTION:
;shampoo.ca.                    IN      MX

;; ANSWER SECTION:
shampoo.ca.             600     IN      MX      30 mx5.biz.mail.yahoo.com.
shampoo.ca.             [COLOR="Red"]600[/COLOR]     IN      MX      10 alt1.aspmx.l.google.com.
shampoo.ca.             [COLOR="Red"]600 [/COLOR]    IN      MX      10 alt2.aspmx.l.google.com.
shampoo.ca.             [COLOR="Red"]600[/COLOR]     IN      MX      10 aspmx.l.google.com.
shampoo.ca.             [COLOR="Red"]600[/COLOR]     IN      MX      10 aspmx2.googlemail.com.
shampoo.ca.             [COLOR="Red"]600[/COLOR]     IN      MX      10 aspmx3.googlemail.com.

;; AUTHORITY SECTION:
shampoo.ca.             86400   IN      NS      ns9.san.yahoo.com.
shampoo.ca.             86400   IN      NS      ns8.san.yahoo.com.
shampoo.ca.             86400   IN      NS      yns2.yahoo.com.
shampoo.ca.             86400   IN      NS      yns1.yahoo.com.

...
...
..

;; Query time: 175 msec
;; SERVER: 66.218.71.205#53(66.218.71.205)
;; WHEN: Fri Mar 14 12:54:28 2008
;; MSG SIZE  rcvd: 422
```

Google's mail servers are listed with preference 10, while a leftover with preference 30 is still in there.

regards

Marc

---

### Post by jknotzke on 2008-03-14
Ya, that's because I added them after the fact. ;-)

  Anyhow, Blackberry.net has updated itself so all is well.

   My my real question was how to determine when a non authoritative server will update its cache for a given record.

   The answer appears to be 'you can't'. You can assume that it will be before the TTL on the authoritative server. But that is all.

   J

---

### Post by netztier on 2008-03-14
> **jknotzke said:**
> 
   My my real question was how to determine when a non authoritative server will update its cache for a given record.

   The answer appears to be 'you can't'. You can assume that it will be before the TTL on the authoritative server. But that is all.


I believe the answer is 'you can'. If you query the chaching/non-authoritative server for the record you're interested in, you'll see a TTL value. This value is derived (i.e. counted down in 1sec decrements) from the answer the authoritative server gave when this record was first queried by the caching server.

Hence you can see how long into the future this record is going to be cached on the non-authoritative server. After the TTL has expired, the non-authoritative server is not going to update the cache by itself; only a client's query for the record with trigger a "cache refresh".


regards

Marc

---

