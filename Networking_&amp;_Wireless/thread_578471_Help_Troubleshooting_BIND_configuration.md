---
title: "Help Troubleshooting BIND configuration"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by atjensen11 on 2007-10-17
Hello,

I am written a few posts about the need to set up BIND.  I finally decided to give it a try and now have it "working" in that it loads without errors.

I am using the Ubuntu Server edition 7.04 and BIND9.

I have followed some tutorials that suggest using the dig, nslookup and host commands.  Dig appears to work, but the other two do not.  Here are the outputs of each.

```
>dig gopher-nation.com

;; global options: printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 63781
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;gopher-nation.com.  IN A

;; Query time: 1 msec
;; SERVER: 192.168.100.2#53(192.168.100.2)
;; WHEN: Wed Oct 17 09:25:57 2007
;; MSG SIZE rcvd: 35
```

```
>nslookup gopher-nation.com

Server:   192.168.100.2
Address: 192.168.100.2#53

** server can't find gopher-nation.com: SERVFAIL
```

```
>host gopher-nation.com

Host gopher-nation.com not found: 2(SERVFAIL)
```

Can you help me troubleshoot these problems?

Thanks,
Tom

---

### Post by noob12 on 2007-10-17
Actually, I'm sorry to say that your dig didn't work either:
```

;; Got answer:
;; ->>HEADER<<- opcode: QUERY, [COLOR="Red"]status: SERVFAIL[/COLOR], id: 63781
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

```

---

### Post by atjensen11 on 2007-10-17
OK, so it appears that dig didn't work either according to your post.  Is there any suggestions where to look?  I am completely new to this and have managed to stumble this far.

The domain name I am search is not a publicly owned domain name.  I was using a tutorial that used "example.com" and I modeled my configuration files after that tutorial on Ubuntu Geek.

I was expecting the tests to return valid results since the request would hit my DNS server first and then forward the request if it couldn't be completed.

Is this not valid logic on the way my DNS server should work?  Maybe I am just misunderstanding something.

Thanks,
Tom

---

### Post by noob12 on 2007-10-17
There's a HOWTO here that you might find helpful but I haven't actually ever used it: 

[http://langfeldt.net/DNS-HOWTO/BIND-9/](http://langfeldt.net/DNS-HOWTO/BIND-9/)

The simple domain section is probably for you and then look at the real domain section.

---

### Post by atjensen11 on 2007-10-17
I will look at the How To more tomorrow to see if it helps me.  I think I have resolved a few of my errors through trial today.

This is the excerpt from the system logs now:

```
Oct 17 21:48:58 gopher named[5822]: starting BIND 9.3.4 -c /etc/bind/named.conf
Oct 17 21:48:58 gopher named[5822]: found 1 CPU, using 1 worker thread
Oct 17 21:48:58 gopher named[5822]: loading configuration from '/etc/bind/named.conf'
Oct 17 21:48:58 gopher named[5822]: listening on IPv6 interfaces, port 53
Oct 17 21:48:58 gopher named[5822]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 17 21:48:58 gopher named[5822]: listening on IPv4 interface eth0, 192.168.100.2#53
Oct 17 21:48:58 gopher named[5822]: none:0: open: /etc/bind/rndc.key: permission denied
Oct 17 21:48:58 gopher named[5822]: couldn't add command channel 127.0.0.1#953: permission denied
Oct 17 21:48:58 gopher named[5822]: none:0: open: /etc/bind/rndc.key: permission denied
Oct 17 21:48:58 gopher named[5822]: couldn't add command channel ::1#953: permission denied
Oct 17 21:48:58 gopher named[5822]: couldn't open pid file '/var/run/bind/run/named.pid': No such file or directory
Oct 17 21:48:58 gopher named[5822]: exiting (due to early fatal error)
```

Thanks,
Tom

---

### Post by atjensen11 on 2007-10-18
OK, so I am still digging through this and would appreciate any help people can offer.  I changed the properties on my rndc.key file.

I noticed that the owner:group on all my zone files were root:bind.  I don't know if this is correct for permissions and security.  But the rndc.key file was bind:bind.  When I changed it to root:bind like the others, I no longer received the permissions error.

But I still have one more error in my system log:
```
Oct 18 08:52:20 gopher named[9907]: starting BIND 9.3.4 -c /etc/bind/named.conf
Oct 18 08:52:20 gopher named[9907]: found 1 CPU, using 1 worker thread
Oct 18 08:52:20 gopher named[9907]: loading configuration from '/etc/bind/named.conf'
Oct 18 08:52:20 gopher named[9907]: listening on IPv6 interfaces, port 53
Oct 18 08:52:20 gopher named[9907]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 18 08:52:20 gopher named[9907]: listening on IPv4 interface eth0, 192.168.100.2#53
Oct 18 08:52:20 gopher named[9907]: command channel listening on 127.0.0.1#953
Oct 18 08:52:20 gopher named[9907]: command channel listening on ::1#953
Oct 18 08:52:20 gopher named[9907]: couldn't open pid file '/var/run/bind/run/named.pid': No such file or directory
Oct 18 08:52:20 gopher named[9907]: exiting (due to early fatal error)
```

Thanks,
Tom

---

### Post by atjensen11 on 2007-10-18
Further checking reveals that the there is no "bind" directory under /var/run.

Do I need to create this?

Looking through my BIND configuration files, I don't see where the rndc.key file or the named.pid file are even referenced.

Thanks,
Tom

---

### Post by atjensen11 on 2007-10-18
I created the directory "bind/run" under "/var/run" so that I now have a valid directory "/var/run/bind/run" and the named.pid file was created automatically when I attempted to start BIND.

This is the result of the system log after those changes:
```
Oct 18 09:09:29 gopher named[10062]: starting BIND 9.3.4 -c /etc/bind/named.conf
Oct 18 09:09:29 gopher named[10062]: found 1 CPU, using 1 worker thread
Oct 18 09:09:29 gopher named[10062]: loading configuration from '/etc/bind/named.conf'
Oct 18 09:09:29 gopher named[10062]: listening on IPv6 interfaces, port 53
Oct 18 09:09:29 gopher named[10062]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 18 09:09:29 gopher named[10062]: listening on IPv4 interface eth0, 192.168.100.2#53
Oct 18 09:09:29 gopher named[10062]: command channel listening on 127.0.0.1#953
Oct 18 09:09:29 gopher named[10062]: command channel listening on ::1#953
Oct 18 09:09:29 gopher named[10062]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 18 09:09:29 gopher named[10062]: /etc/bind/zones/rev.100.168.192.in-addr.arpa:1: no TTL specified; using SOA MINTTL instead
Oct 18 09:09:29 gopher named[10062]: zone 100.168.192.in-addr.arpa/IN: has no NS records
Oct 18 09:09:29 gopher named[10062]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct 18 09:09:29 gopher named[10062]: dns_rdata_fromtext: /etc/bind/zones/gopher-nation.com.db:1: near '//': not a valid number
Oct 18 09:09:29 gopher named[10062]: zone gopher-nation.com/IN: loading master file /etc/bind/zones/gopher-nation.com.db: not a valid number
Oct 18 09:09:29 gopher named[10062]: zone localhost/IN: loaded serial 1
Oct 18 09:09:29 gopher named[10062]: running

```

Thanks,
Tom

---

### Post by atjensen11 on 2007-10-22
OK, I think things are working better now.  One big realization I made was the an older version of BIND was also installed.  I thought I had uninstalled it, but it was still there.

So now BIND9 is being started at boot time.  I can't get a static IP address for my server, so I am really trying to only setup a caching DNS server that will also resolve computer names on my local network.

At the command prompt, I type "dig gopher-nation.com" and I get:
```
; <<>> DiG 9.4.1-P1 <<>> gopher-nation.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22298
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;gopher-nation.com.             IN      A

;; AUTHORITY SECTION:
gopher-nation.com.      86400   IN      SOA     ns1.gopher-nation.com. admin.gopher-nation.com. 2007031005 28800 7200 604800 86400

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Oct 22 09:44:25 2007
;; MSG SIZE  rcvd: 81
```

When I type "nslookup gopher-nation.com", I get:
```
Server:         127.0.0.1
Address:        127.0.0.1#53

*** Can't find gopher-nation.com: No answer
```

Finally, when I type "host gopher-nation.com", I get:
```
gopher-nation.com mail is handled by 10 mail.gopher-nation.com.
```

Does this look like it is operating correctly for a simple DNS server?

Thanks,
Tom

---

