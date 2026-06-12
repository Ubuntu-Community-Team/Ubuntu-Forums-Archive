---
title: "DNS Connection Issue with UDP"
date: 2023-11-02
forum: Networking &amp; Wireless
---

### Post by cancomert on 2023-11-02
I have a DNS Problem by resolving the Hostnames with DNS.
I think, I do not have any local DNS Cache Server, neither bind9 nor unbound.
I can re-install them but local DNS Cache Server made it more hard to debug the issue.

When execuute dig command with my default DNS Server I get timeout:
```

$ dig s3.eu-central-1.amazonaws.com
;; communications error to 84.200.69.80#53: timed out
;; communications error to 84.200.69.80#53: timed out
;; communications error to 84.200.69.80#53: timed out
;; communications error to 84.200.70.40#53: timed out
;; communications error to 1.1.1.1#53: timed out

; <<>> DiG 9.18.18-0ubuntu0.22.04.1-Ubuntu <<>> s3.eu-central-1.amazonaws.com
;; global options: +cmd
;; no servers could be reached

```

If I execute +tcp flag to force TCP instead of UDP it seems like working:

```

$ dig +tcp s3.eu-central-1.amazonaws.com

; <<>> DiG 9.18.18-0ubuntu0.22.04.1-Ubuntu <<>> +tcp s3.eu-central-1.amazonaws.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62038
;; flags: qr rd ra; QUERY: 1, ANSWER: 8, AUTHORITY: 4, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;s3.eu-central-1.amazonaws.com.    IN    A

;; ANSWER SECTION:
s3.eu-central-1.amazonaws.com. 5 IN    A    52.219.170.65
s3.eu-central-1.amazonaws.com. 5 IN    A    52.219.171.97
s3.eu-central-1.amazonaws.com. 5 IN    A    52.219.171.129
s3.eu-central-1.amazonaws.com. 5 IN    A    52.219.75.239
s3.eu-central-1.amazonaws.com. 5 IN    A    52.219.47.179
s3.eu-central-1.amazonaws.com. 5 IN    A    52.219.171.37
s3.eu-central-1.amazonaws.com. 5 IN    A    52.219.170.233
s3.eu-central-1.amazonaws.com. 5 IN    A    52.219.140.3

;; AUTHORITY SECTION:
s3.eu-central-1.amazonaws.com. 42807 IN    NS    ns-1229.awsdns-25.org.
s3.eu-central-1.amazonaws.com. 42807 IN    NS    ns-2043.awsdns-63.co.uk.
s3.eu-central-1.amazonaws.com. 42807 IN    NS    ns-321.awsdns-40.com.
s3.eu-central-1.amazonaws.com. 42807 IN    NS    ns-562.awsdns-06.net.

;; Query time: 48 msec
;; SERVER: 84.200.69.80#53(84.200.69.80) (TCP)
;; WHEN: Thu Nov 02 19:36:50 CET 2023
;; MSG SIZE  rcvd: 323

```

I tried also with other DNS Servers like 8.8.8.8 or 1.1.1.1

```

$ dig @1.1.1.1 s3.eu-central-1.amazonaws.com
;; communications error to 1.1.1.1#53: timed out

$ dig @8.8.8.8 s3.eu-central-1.amazonaws.com
;; communications error to 8.8.8.8#53: timed out

```

I am living in Germany and my ISP is Deutsche Multimedia Service GmbH.
I have an Android Phone and it seems it does not have DNS issues but in Ubuntu Linux with my laptop I always run into UnkownHost errors due to DNS Problems.
Do you have any idea how can I have a working DNS under Ubuntu?

---

### Post by TheFu on 2023-11-02
systemd-resolved is the likely problem.  It is a caching DNS that Ubuntu started shipping by default with desktops perhaps in 2020.  There is the /etc/systemd/resolved.conf  file which probably just needs the primary and secondary DNS setup, not "magically discovered".

Of course, you don't actually need resolved running at all, but if you disable it, then set /etc/resolv.conf manually, like we did pre-resolvconf.  All this extra junk to protect end users from adding 1 lines to 1 file, one time.

---

### Post by The Cog on 2023-11-02
Agreed. I think /etc/resolv.conf is normally a symlink to a file somewhere else that gets re-written every time you boot. Given resolved's propensity to randomly stop working, I learned a long time ago delete the symlink (or rename it) and replace it with a real file that contains the below (or whichever nameserver you want to use):
```
nameserver 1.1.1.1
nameserver 1.0.0.1
```

---

### Post by TheFu on 2023-11-02
Just changing the file probably isn't sufficient.  Also need to stop, disable, and mask the systemd-resolved service.

---

