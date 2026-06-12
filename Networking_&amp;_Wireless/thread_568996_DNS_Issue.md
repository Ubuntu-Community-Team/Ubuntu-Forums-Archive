---
title: "DNS Issue"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by tbrothers on 2007-10-06
My DNS must not be configured correctly because when I do an nslookup of brothersfamily.net mx record (or any other record) I get the following error.  Any ideas?

**NSLOOKUP Error**
[COLOR="Blue"]server can't find brothersfamily: NXDOMAIN[/COLOR]

**This is the only entry in named.conf**
[COLOR="Blue"]zone "brothersfamily" {
        type master;
        file "/etc/bind/zones/brothersfamily.net";
};[/COLOR]

**This is my zone file**
[COLOR="Blue"]// brothersfamily.net

brothersfamily.net. IN SOA 192.168.126.90. terry.brothersfamily.net. (

// Do not modify the following lines!
2007031001	;Serial
28800		;Refresh
3600		;Retry
604800		;Expire
38400		;Negative Cache TTL
)

// name servers
brothersfamily.net  IN NS 192.168.126.90

// mail servers
brothersfamily.net. IN MX 10 mailwash244.pair.com.

// hosts
www IN A 216.92.181.22
u2  IN A 192.168.126.90
u22  IN A 192.168.126.91
u23  IN A 192.168.126.92[/COLOR]

Thanks,
Terry

---

### Post by tbrothers on 2007-10-06
I should have added that I'm using Ubuntu 7.04 and BIND 9.  DNS appears to start just fine.
[COLOR="Blue"]
root@U2:/etc# /etc/init.d/bind9 restart
 * Stopping domain name service... bind                                  [ OK ] 
 * Starting domain name service... bind                                  [ OK ] 
root@U2:/etc# [/COLOR]

Terry

---

### Post by helgman on 2007-10-07
> **tbrothers said:**
> root@U2:/etc# /etc/init.d/bind9 restart
 * Stopping domain name service... bind                                  [ OK ] 
 * Starting domain name service... bind                                  [ OK ] 

Bind might start but your zone might not be loaded (due to errors). Restart Bind and take a look in the log (syslog will hold information by default).

I managed to get your zone working by doing a few changes (don't know what change that did it). This is what it looks like:
```
$TTL 30d
brothersfamily.net.  IN  SOA  u2.brothersfamily.net.  terry.borthersfamily.net. (
  2007100700
  28800
  3600
  604800
  38400 )

  IN NS   u2.brothersfamily.net.
  IN MX  10 mailwash244.pair.com.
  
www  IN A  216.92.181.22
u2  IN A  192.168.126.90
u22  IN A  192.168.126.91
u23  IN A  192.168.126.92
```

The comments in your file "//" cases the zone to be rejected on my system so you might want to skip them.

Does this help you at all?

Helgman

---

