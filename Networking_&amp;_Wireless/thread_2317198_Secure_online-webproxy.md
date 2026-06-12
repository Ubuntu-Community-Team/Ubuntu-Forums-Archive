---
title: "Secure online-webproxy?"
date: 2016-03-14
forum: Networking &amp; Wireless
---

### Post by karl17 on 2016-03-14
Hi,

I'm looking for some kind of proxy, but I have no idea if something like this exists and how it would work really. Following situation:

1. I have a dedicated server "S" which is able to access everything in internet
2. I have a interface to internet "I" which is limited, means I can reach only a few webpages but also my server "S"
3. "I" is also not able to submit any proxy information in HTTP-headers

Now I want to set up some kind of proxy on my server "S" which can be reached from "I" and provides full access to the internet. I could imagine a special webpage on "S" that shows an input field where a URL can be entered. Now "S" fetches all data from this URL and displays it to "I" via a frame of this webpage on "S" - so from "I"'s point of view it is a connection to "S" only but not to the real webpage behind it.

Access to "S" of course should be HTTPS-secured and password protected so that not everybody can use this proxy.

My question: does something like this exists for Ubuntu?

Thanks!

---

### Post by ecaep on 2016-03-14
Hey Karl17,

I would say to look into squid or tinyproxy. They both are web proxies for HTTP/S, and generally are easy to setup.

I am curious though why not just restrict server 'l' out bound web traffic on the firewall. Not all but most now can permit/deny traffic based on domains now and just not network IPs.

---

### Post by SeijiSensei on 2016-03-14
[http://wiki.squid-cache.org/SquidFaq/InterceptionProxy](http://wiki.squid-cache.org/SquidFaq/InterceptionProxy)

---

