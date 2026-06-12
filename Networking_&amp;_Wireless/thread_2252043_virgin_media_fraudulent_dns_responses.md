---
title: "virgin media fraudulent dns responses"
date: 2014-11-08
forum: Networking &amp; Wireless
---

### Post by The Cog on 2014-11-08
Is anyone else having problems with virgin media fraudulently giving out an IP that they own instead of the true answer?

In the last hour or so, Virgin have been hijacking my attempts to connect to amazon.co.uk and to ubuntuforums.org. Other sites I have tried (e.g. slashdot.org) are not being hijacked.

Here is an example:
```
steve@StevesLappy:~$ nslookup www.amazon.co.uk 192.168.0.1
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	www.amazon.co.uk
Address: 62.252.172.241

steve@StevesLappy:~$ nslookup 62.252.172.241 192.168.0.1
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
241.172.252.62.in-addr.arpa	name = know-sspiprxy-vip.network.virginmedia.net.

Authoritative answers can be found from:


```
The real address can be got from Google's DNS server:
```
steve@StevesLappy:~$ nslookup www.amazon.co.uk 8.8.8.8
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
Name:	www.amazon.co.uk
Address: 178.236.6.251


```

---

### Post by ajgreeny on 2014-11-08
This is what I got using EE as my ISP.
```
~$ nslookup www.amazon.co.uk 192.168.0.1
Server:        192.168.0.1
Address:    192.168.0.1#53

Non-authoritative answer:
Name:    www.amazon.co.uk
Address: 176.32.108.186
```
And then when I do the reverse lookup
```
$ nslookup 176.32.108.186 192.168.0.1
Server:        192.168.0.1
Address:    192.168.0.1#53

** server can't find 186.108.32.176.in-addr.arpa.: NXDOMAIN
```
And if I use google's dns servers I get
```
~$ nslookup [www.amazon.co.uk]("http://www.amazon.co.uk") 8.8.8.8
Server:        8.8.8.8
Address:    8.8.8.8#53

Non-authoritative answer:
Name:    [www.amazon.co.uk]("http://www.amazon.co.uk")
Address: 178.236.7.220

~$ nslookup 178.236.7.220 8.8.8.8
Server:        8.8.8.8
Address:    8.8.8.8#53

** server can't find 220.7.236.178.in-addr.arpa.: NXDOMAIN
```
What does that tell us?

---

### Post by The Cog on 2014-11-08
> What does that tell us?
Two things I think:
1: Amazon's addresses are somehow a little odd in that you can't reverse lookup on them. I don't know DNS well enough to know why that might be. 
2: Amazon seem to be doing some load balancing by giving several addresses as DNS answers.

See this sequence. Note that amazon and ubuntuforums seem to have the same IP address:
```
steve@StevesLappy:~$ nslookup ubuntuforums.org 192.168.0.1
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	ubuntuforums.org
Address: 62.252.172.241

steve@StevesLappy:~$ nslookup 62.252.172.241
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
241.172.252.62.in-addr.arpa	name = know-sspiprxy-vip.network.virginmedia.net.

Authoritative answers can be found from:

steve@StevesLappy:~$ nslookup ubuntuforums.org 8.8.8.8
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
Name:	ubuntuforums.org
Address: 91.189.94.12

steve@StevesLappy:~$ nslookup 91.189.94.12
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
12.94.189.91.in-addr.arpa	name = feijoa.canonical.com.

Authoritative answers can be found from:


```
While I was writing this reply, Virgin seem to have stopped hijacking amazon although they are still hijacking ubuntuforums.

---

### Post by The Cog on 2014-11-08
Virgin support web site says:
> Hi 
 
We're aware that some customers are experiencing issues with Web Safe.
 
We're investigating this at the moment, and will update this thread accordingly.
 
Please subscribe or bookmark for updates.
 
Our apologies for any inconvenience caused.
 
Thank you.
 
James

---

### Post by Doug S on 2014-11-08
> **The Cog said:**
> 1: Amazon's addresses are somehow a little odd in that you can't reverse lookup on them. I don't know DNS well enough to know why that might be.It just means they, or whomever owns the IP address, didn't setup a reverse zone file> **The Cog said:**
> 2: Amazon seem to be doing some load balancing by giving several addresses as DNS answers.Yes, but it is not similar to others I have ever seen. Take Google for example:```
doug@doug-64:~$ [COLOR=#ff0000]dig -t any google.com[/COLOR]
;; Truncated, retrying in TCP mode.

; <<>> DiG 9.8.1-P1 <<>> -t any google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7318
;; flags: qr rd ra; QUERY: 1, ANSWER: 24, AUTHORITY: 4, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      ANY

;; ANSWER SECTION:
google.com.             86205   IN      SOA     ns1.google.com. dns-admin.google.com. 2014110400 7200 1800 1209600 300
google.com.             3405    IN      TXT     "v=spf1 include:_spf.google.com ip4:216.73.93.70/31 ip4:216.73.93.72/31 ~all"
google.com.             405     IN      MX      30 alt2.aspmx.l.google.com.
google.com.             405     IN      MX      40 alt3.aspmx.l.google.com.
google.com.             405     IN      MX      50 alt4.aspmx.l.google.com.
google.com.             405     IN      MX      10 aspmx.l.google.com.
google.com.             405     IN      MX      20 alt1.aspmx.l.google.com.
google.com.             86205   IN      TYPE257 \# 19 0005697373756573796D616E7465632E636F6D
google.com.             105     IN      AAAA    2607:f8b0:400a:805::100e
[COLOR=#ff0000]google.com.             105     IN      A       173.194.33.165
google.com.             105     IN      A       173.194.33.166
google.com.             105     IN      A       173.194.33.167
google.com.             105     IN      A       173.194.33.168
google.com.             105     IN      A       173.194.33.169
google.com.             105     IN      A       173.194.33.174
google.com.             105     IN      A       173.194.33.160
google.com.             105     IN      A       173.194.33.161
google.com.             105     IN      A       173.194.33.162
google.com.             105     IN      A       173.194.33.163
google.com.             105     IN      A       173.194.33.164[/COLOR]
google.com.             82645   IN      NS      ns3.google.com.
google.com.             82645   IN      NS      ns4.google.com.
google.com.             82645   IN      NS      ns2.google.com.
google.com.             82645   IN      NS      ns1.google.com.

;; AUTHORITY SECTION:
google.com.             82645   IN      NS      ns1.google.com.
google.com.             82645   IN      NS      ns3.google.com.
google.com.             82645   IN      NS      ns4.google.com.
google.com.             82645   IN      NS      ns2.google.com.

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Nov  8 15:20:45 2014
;; MSG SIZE  rcvd: 633
```

---

### Post by The Cog on 2014-11-08
Amazon looks much the same as that to me, but with 3 addresses.

I was wrong about virgin stopping its hijacking of amazon. They are hijacking [www.amazon.co.uk](www.amazon.co.uk) but not amazon.co.uk.

This makes it even easier to see:
```
steve@StevesLappy:~$ ping amazon.co.uk
PING amazon.co.uk (176.32.108.186) 56(84) bytes of data.
64 bytes from 176.32.108.186: icmp_seq=1 ttl=244 time=30.6 ms
64 bytes from 176.32.108.186: icmp_seq=2 ttl=244 time=30.1 ms
^C
steve@StevesLappy:~$ ping www.amazon.co.uk
PING www.amazon.co.uk (62.252.172.241) 56(84) bytes of data.
64 bytes from know-sspiprxy-vip.network.virginmedia.net (62.252.172.241): icmp_seq=1 ttl=245 time=24.3 ms
64 bytes from know-sspiprxy-vip.network.virginmedia.net (62.252.172.241): icmp_seq=2 ttl=245 time=22.2 ms
^C
steve@StevesLappy:~$ ping ubuntuforums.org
PING ubuntuforums.org (62.252.172.241) 56(84) bytes of data.
64 bytes from know-sspiprxy-vip.network.virginmedia.net (62.252.172.241): icmp_seq=1 ttl=245 time=24.0 ms
64 bytes from know-sspiprxy-vip.network.virginmedia.net (62.252.172.241): icmp_seq=2 ttl=245 time=22.2 ms
^C

```
I am able to log in to amazon and ubuntuforums again now, but my connection is clearly still hijacked by Virgin's server. 
Even HTTPs works. So Virgin  seem to be conducting a man-in-the-middle attack even on my HTTPs connections, presumably reading every web page I visit.

I understand how they can proxy HTTP, but how do they manage to intercept HTTPS? I thought it was supposed to be secure.
Can anyone explain that?

---

### Post by The Cog on 2014-11-09
Next day, and Virgin are now returning the real IP address for my DNS queries. No more hijacking.

I would still like to know how they managed to make my HTTPS connections work (as in allowing me to order from amazon) when I was connecting to virgins server instead of amazons server.

---

### Post by Doug S on 2014-11-09
> **The Cog said:**
> Amazon looks much the same as that to me, but with 3 addresses.Yes, it does for me also, if I do it properly. Sorry for adding noise to your thread.

---

### Post by bashiergui on 2014-11-10
> I would still like to know how they managed to make my HTTPS connections work (as in allowing me to order from amazon) when I was connecting to virgins server instead of amazons server.Indeed. Did it default to http?

---

### Post by The Cog on 2014-11-11
> **bashiergui said:**
> Indeed. Did it default to http?

A lot of it does, but the basket and checkout pages don't. And I was also able to https to ubuntuforums. It complained about insecure (http) scripts, but the https page and login worked. I really thought you couldn't do that with https. Sorry but I didn't keep the wireshark traces.

---

