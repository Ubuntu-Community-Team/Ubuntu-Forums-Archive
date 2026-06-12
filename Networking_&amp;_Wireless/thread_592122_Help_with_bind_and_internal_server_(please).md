---
title: "Help with bind and internal server (please)"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by DeltaWolf7 on 2007-10-26
Hi,


I am new to linux, so please try to keep it simple.

I have created an entry in bind for an internel server, which works internally, but from the internet it is not being forwarded.

here is the dig log for both addresses;

servera.ink4u.co.uk should go to an internal server @ address 192.168.0.250
earth.ink4u.co.uk is the server connected to the internet (internal address 192.168.0.200).

what do i need to do?


; <<>> DiG 9.4.1-P1 <<>> servera.ink4u.co.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12184
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;servera.ink4u.co.uk.           IN      A

;; ANSWER SECTION:
servera.ink4u.co.uk.    3600    IN      A       192.168.0.250

;; Query time: 10 msec
;; SERVER: 192.168.0.250#53(192.168.0.250)
;; WHEN: Fri Oct 26 10:41:21 2007
;; MSG SIZE  rcvd: 53

root@earth:~# dig earth.ink4u.co.uk

; <<>> DiG 9.4.1-P1 <<>> earth.ink4u.co.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62327
;; flags: qr aa; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;earth.ink4u.co.uk.             IN      A

;; ANSWER SECTION:
earth.ink4u.co.uk.      14400   IN      A       213.123.193.145

;; Query time: 676 msec
;; SERVER: 192.168.0.250#53(192.168.0.250)
;; WHEN: Fri Oct 26 10:41:50 2007
;; MSG SIZE  rcvd: 51



named.conf file


options {
        pid-file "/var/run/bind/run/named.pid";
        directory "/etc/bind";
        auth-nxdomain no;
        /*
         * If there is a firewall between you and nameservers you want
         * to talk to, you might need to uncomment the query-source
         * directive below.  Previous versions of BIND always asked
         * questions using port 53, but BIND 8.1 uses an unprivileged
         * port by default.
         */
        // query-source address * port 53;
};

//
// a caching only nameserver config
//
zone "." {
        type hint;
        file "db.root";
};

zone "0.0.127.in-addr.arpa" {
        type master;
        file "db.local";
};




ink4u.co.uk.hosts file

//// MAKE MANUAL ENTRIES BELOW THIS LINE! ////

zone "ink4u.co.uk" {
	type master;
	file "/etc/bind/ink4u.co.uk.hosts";
	};





$ttl 38400
ink4u.co.uk.    IN      SOA     earth.ink4u.co.uk. craig.ink4u.co.uk. (
                        1193387569
                        10800
                        3600
                        604800
                        38400 )
ink4u.co.uk.    IN      NS      earth.ink4u.co.uk.
servera.ink4u.co.uk.    IN      A       192.168.0.250

---

