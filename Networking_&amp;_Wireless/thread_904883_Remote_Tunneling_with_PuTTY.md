---
title: "Remote Tunneling with PuTTY"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by avgjoe22 on 2008-08-29
Hi, everyone.

I would like to set up a server at home so that I can use PuTTY at school to surf the web without a proxy.

I installed SSH and made a no-ip account that connects to my home IP as "smackthedean.servebeer.com" and I used that as the hostname, port 22.

Under "SSH>Tunnelling"  I used "80" as the source port and the destination as "localhost:80"

I pressed start and reecieved:

ERROR: Connection Refused

...help?

---

### Post by SpaceTeddy on 2008-08-31
i am sure that your school blocks port 22 (i.e. that's why the connection was refused) - so the request never reached your home computer. Also, the gateway feature of ssh is still experimental (as far as i know at least)... i've never gotten it to work myself either - the forwarding is usually only good for one destination redirect - not for the entire internet.

What you need to do is run the ssh-server at your home on port 80 or 443, and then figure out how the redirect-gateway works with putty - simple forwarding is not enough here... 

i don't think this is going to work... at all...

---

