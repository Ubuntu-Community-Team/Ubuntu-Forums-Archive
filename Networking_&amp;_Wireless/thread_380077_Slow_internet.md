---
title: "Slow internet"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by jonttix on 2007-03-09
Hello! I have a strange problem, my internet connections seems to be very slow in the beginning, when you enter a new adress or clicking on a link the "looking up adress.com" takes very long. But after a while it speeds up. When I have downloaded some updates to ubuntu the speed is then max 850kbits/sec.

Can anybody please help me with this?

Jonas (Linux newbie!!)

---

### Post by Paul41 on 2007-03-09
You could try to disable IPv6 to see if that speeds things up.

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

When you say things speed up after a while, is it on pages that you have already visited?  If that is the case it may just be faster because it is using the cache and not downloading the page again.

---

### Post by jonttix on 2007-03-09
I have now disabled IPv6 but it is the same problem still.

---

### Post by pandu.rs on 2007-03-09
looks like ur nameserver might not be configured properly

try running the following the command
dig <somenewdomain>

and paste its output here

---

### Post by jonttix on 2007-03-09
jonttix@jonttix-desktop:~$ dig [www.expressen.se](www.expressen.se)
;; reply from unexpected source: 10.0.0.2#3072, expected 10.0.0.2#53

; <<>> DiG 9.3.2 <<>> [www.expressen.se](www.expressen.se)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59134
;; flags: qr rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.expressen.se](www.expressen.se).              IN      A

;; ANSWER SECTION:
[www.expressen.se](www.expressen.se).       10000   IN      A       193.180.57.70

;; Query time: 2 msec
;; SERVER: 10.0.0.2#53(10.0.0.2)
;; WHEN: Fri Mar  9 17:27:58 2007
;; MSG SIZE  rcvd: 50

jonttix@jonttix-desktop:~$


This is what it said.

---

### Post by pandu.rs on 2007-03-09
;; Query time: 2 msec
;; SERVER: 10.0.0.2#53(10.0.0.2)

2ms is pretty fast..
Also you are using a local nameserver (10.0.0.2).. so may be that nameserver takes a long time to resolve a domain.

what kind of enviroment are u in (how do u get connected to the internet)?

r u aware of what is machine with ip 10.0.0.2? (such as another machine at home, work or isp's nameserver)

---

### Post by jonttix on 2007-03-09
I have a ADSL connection, and I use an A-link RR24 modem. The other machine is an AMD laptop with Windows XP as OS. The internet connection on the laptop works fine though...

---

### Post by Mr. C. on 2007-03-09
It appears your modem has a DNS cache, and when an address is not in the cache, it reverts to your ISPs DNS server, which may be incorrectly configured.

First, don't rely on your modem's DNS servers - they are very poor.  Configure the DNS IPs that are available from your ISP (check their website, or contact them).

Windows has a much better cache for name lookups that the router - Windows uses its own cache.

One you have those, place those in the DNS tab in the Networking app.

MrC

---

### Post by Rui Pais on 2007-03-09
Or use [this ones]("http://opendns.com/start/ubuntu.php").

---

### Post by jonttix on 2007-04-05
Thank you Rui Pais!!!

---

