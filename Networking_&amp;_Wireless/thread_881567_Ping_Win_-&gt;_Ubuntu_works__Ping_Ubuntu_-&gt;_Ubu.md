---
title: "Ping Win -&gt; Ubuntu works | Ping Ubuntu -&gt; Ubuntu fails"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Thomas_R on 2008-08-06
Hi,

I have three boxes: W with Win XP, U1 and U2 both with Ubuntu.

I can ping from W both Ubuntu boxes. Good. 
I can also ping from U1 to W (and from U2 to W).
(all pings by name, no static ip involved)

But I cannot ping from the one Ubuntu box to the other:
```
ping aachen
ping: unknown host aachen
```

DNS seems to work, because I can ping the Ubuntu boxes from W (all pings by name).

But why does the name resolution fail for pings from one Ubuntu box to the other?

Any ideas?

Thanks in advance,
Thomas

[purador | Designer - Schmuck - Kollektionen]("http://www.purador.de")

---

### Post by jimv on 2008-08-06
I had to enable the DNS server on my router before I got name resolution to work right in Ubuntu.

You could try this guy's solution though:
[http://www.poromenos.org/node/53](http://www.poromenos.org/node/53)

Basically, install WinBind and add WINS to your /etc/nsswitch.conf file.

---

### Post by Thomas_R on 2008-08-07
Thanks! Now it works.

DNS on my router was already activated. The link was very helpful!

---

