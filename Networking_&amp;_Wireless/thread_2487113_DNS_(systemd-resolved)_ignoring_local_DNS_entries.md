---
title: "DNS (systemd-resolved) ignoring local DNS entries"
date: 2023-05-23
forum: Networking &amp; Wireless
---

### Post by regregoryallen on 2023-05-23
I am using the default DNS resolution on Ubuntu 22.04.  I have a router with some locally defined DNS entries, but the Ubuntu systems cannot resolve those local names.  I have other systems running Debian  and Android and they work as expected.  I ran "Try Ubuntu" from a 23.04 ISO and got the same behavior as 22.04, so I'm confident it's not due to any changes I've made on the 22.04 systems.

Perhaps I don't quite understand how systemd-resolved should work, but I'm not getting the result I expect.


The details:

--- Gateway router is on 10.11.0.1, and includes a DNS entry for "homeweb" as 10.11.0.65.  The router DNS works as expected for off-site addresses.  

--- These are **DEFAULT** installations.  No changes have been made to networking or DNS behavior.  Network is configured entirely based on DHCP.

--- resolvectl (on **Ubuntu 22.04**) shows that it should be using the router for DNS
```
$ resolvectl status
Global
       Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
resolv.conf mode: stub


Link 2 (enp5s0)
    Current Scopes: DNS
         Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 10.11.0.1
       DNS Servers: 10.11.0.1

```

--- dig lookup (on **Ubuntu 22.04**) succeeds with EXPLICIT server specification
```
$ dig homeweb @10.11.0.1

; <<>> DiG 9.18.12-0ubuntu0.22.04.1-Ubuntu <<>> homeweb @10.11.0.1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3873
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;homeweb.            IN    A


;; ANSWER SECTION:
homeweb.        3600    IN    A    10.11.0.65


;; Query time: 0 msec
;; SERVER: 10.11.0.1#53(10.11.0.1) (UDP)
;; WHEN: Tue May 23 09:13:11 CDT 2023
;; MSG SIZE  rcvd: 41

```

--- dig lookup (on **Ubuntu 22.04**) FAILS without server specification
```
$ dig homeweb

; <<>> DiG 9.18.12-0ubuntu0.22.04.1-Ubuntu <<>> homeweb
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 59238
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;homeweb.            IN    A

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Tue May 23 09:07:04 CDT 2023
;; MSG SIZE  rcvd: 36

```

--- This works as expected from **Debian Bullseye**
```
$ dig homeweb

; <<>> DiG 9.16.37-Debian <<>> homeweb
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27973
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;homeweb.                       IN      A

;; ANSWER SECTION:
homeweb.                3600    IN      A       10.11.0.65

;; Query time: 15 msec
;; SERVER: 10.11.0.1#53(10.11.0.1)
;; WHEN: Tue May 23 10:15:18 EDT 2023
;; MSG SIZE  rcvd: 41

```


My understanding of systemd-resolved is that it accepts DNS requests to localhost and forwards them to the specified server (in this case, 10.11.0.1 as provided by DHCP).  If that is so, then I would expect the first two dig commands to provide identical results.  Do I have that wrong or is resolved misbehaving?  

Of course, lookups work correctly for off-site addresses (e.g. "$ dig google.com"), so lookups must be getting forwarded.  I cannot understand why the local entries get bypassed.

Any help or guidance is much appreciated. 

 Thank you!
--Roger

---

### Post by SeijiSensei on 2023-05-23
I suggest editing /etc/systemd/resolved.conf and adding your local server to the "DNS=" line. If you have backup servers, add them to the "FallbackDNS=" line. Then run
```
sudo systemctl restart systemd-resolved
```
That works for me.

---

### Post by regregoryallen on 2023-05-24
I appreciate the advice, however I've tried that and it makes no difference.  I didn't really expect it to help because the system already gets the correct DNS server from DHCP (as shown by 'resolvectl status').  And besides, this really should "just work" out-of-the-box like it does for other systems that do not use systemd-resolved. 

The correct DNS server appears to be used (in fact, there is no other option), but I don't understand how/why the resolver can miss the local DNS lookups even though global lookups work fine.  Again, everything except Ubuntu works fine (Debian, Windows, Android, etc.) so it seems to be something specfic to systemd-resolved.



> **SeijiSensei said:**
> I suggest editing /etc/systemd/resolved.conf and adding your local server to the "DNS=" line. If you have backup servers, add them to the "FallbackDNS=" line. Then run
```
sudo systemctl restart systemd-resolved
```
That works for me.

---

### Post by TheFu on 2023-05-24
Try 
```
dig homeweb.
```
homeweb
and 
homeweb.
are different to DNS.
If you have your own DNS, you don't have much need for resolved (that's what systemd uses).  mask that and modify the /etc/resolv.conf to point at your router for DNS.  If you like, you can setup a TLD, perhaps .local or .lan and then use that for the domain for all your systems.  Then add a 
```
search .lan
```
line to the bottom of the /etc/resolv.conf file and then with the FQDN of homeweb.lan., you can lookup  "homeweb" and thanks to the search line, it will check what you type with and without the .lan suffix before sending the query to the internet DNS.

---

