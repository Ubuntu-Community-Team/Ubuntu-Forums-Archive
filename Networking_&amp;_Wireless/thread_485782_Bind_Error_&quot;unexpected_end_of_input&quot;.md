---
title: "Bind Error &quot;unexpected end of input&quot;"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by dthacker on 2007-06-27
Hi!
I'm setting up an internal (not exposed to net) nameserver for my household PC's.  I've been working from a tutorial here:
[http://ubuntuforums.org/showthread.php?t=236093&highlight=bind+syntax](http://ubuntuforums.org/showthread.php?t=236093&highlight=bind+syntax)

bind seems to start ok, but I can't ping any machines by name.   When I run the named-checkconf -z to check syntax,  I get these mysterious EOL errors.  Here's the output. 
```
root@weasley:/etc/bind/zones# named-checkconf -z
zone localhost/IN: loaded serial 1
zone 127.in-addr.arpa/IN: loaded serial 1
zone 0.in-addr.arpa/IN: loaded serial 1
zone 255.in-addr.arpa/IN: loaded serial 1
dns_rdata_fromtext: /etc/bind/zones/dthacker.org.db:7: near eol: unexpected end of input
zone dthacker.org/IN: loading master file /etc/bind/zones/dthacker.org.db: unexpected end of input
_default/dthacker.org/IN: unexpected end of input
dns_rdata_fromtext: /etc/bind/zones/rev.168.192.in-addr.arpa:7: near eol: unexpected end of input
zone 168.192.in-addr.arpa/IN: loading master file /etc/bind/zones/rev.168.192.in-addr.arpa: unexpected end of input
_default/168.192.in-addr.arpa/IN: unexpected end of input

```

Heres my current zone file:
```
$TTL 1500
@  IN SOA ns1.dthacker.org. (
                             2007062703        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes

                IN NS ns1.dthacker.org.

ns1         IN  A  192.168.1.30
buckbeak        IN  A  192.168.1.5
fluffy          IN  A  192.168.1.3

```

and here's my reverse lookup file:
```
root@weasley:/etc/bind/zones# more rev.168.192.in-addr.arpa
$TTL 1500
@ IN SOA ns1.dthacker.org. (
                                   2007062703     ;serial #
                                   1500           ;refresh
                                   604800         ;retry
                                   604800         ;expire
                                   86400    )     ;minimum

             IN NS ns1.dthacker.org.
30.1         IN PTR ns1.dthacker.org.
30.5         IN PTR buckbeak.dthacker.org.

```

I hope someone with some DNS experience will see what the cause of the "unexpected end of output" is caused by and help me correct my config files.  Thanks in advance!

---

### Post by Ninj@ on 2008-05-19
try this

replace  zone file and reverse lookup file
[PHP]$TTL 1500
@  IN SOA ns1.dthacker.org. root (
                             2007062703        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes

[/PHP]

and
[PHP]
service named restart[/PHP]

---

