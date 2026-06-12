---
title: "Squid problem. Getting &quot;Invalid IP&quot; error message"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by btrotter on 2007-10-13
I have set up Squid and Dansguardian to do my web proxy'ing.

I have Squid set up as a transparent proxy.

When I try to access a specific site (allstarracingleague.com), I get the following error message:


[B]You have attempted to access this site with an invalid IP.

If you think this is a mistake you can contact the site webmaster at uglystik(at)pcrob(dot)net.

Be SURE to include the following information in any email!
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)
Remote Address: 124.174.50.122
Client IP: none
Forwarded For: 127.0.0.1[/B]

Anyone know what setting in Squid I would need to enable/disable to make it so that I can get to this site? It seems like Squid is sending my IP address along as "127.0.0.1", which the website is set up to block. I just dont know how to get it to send out another IP address.

Thank you.

---

